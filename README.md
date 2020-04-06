# GWTPFunctions
Google Sheet functions for pulling item and trade post information from public Guild Wars 2 APIs
<hr>
<h3>HOW TO</h3>

  - Create a Google Sheet spreadsheet
  - On the top toolbar click Tools > Script Editor
  - Copy the contents of the Functions file into the Code.gs 
  - Implement the functions in your spreadsheets to your desire
<hr>

<h3>Information</h3>

The functions require you to provide the itemID which can be found on gw2bltc.com, wiki.guildwars2.com, gwspidy.com or any other resource

Functions that are included in the code:
  - Get the name of an item
  - Get the rarity of an item
  - Get the vendor value for an item
  - Get the chat link for an item
  - Get the category of an item (ie. "Weapon")
  - Get the type of an item (ie. "Sword")
  - Get the current buy or sell price of an item
  - Get the total number of buy or sell orders of an item
  - Get the average buy or sell price of an item 
      - Default set to the most recent 10% of the item
      - ie. If there are 300 current lists for an item, the function will return the average price of the latest 30 listings
      - You can change the value for this by changing the "percentage" variable value to any value between [0,1.0] where 0.5 would be 50% of the listings
    
These functions will allow for personal record keeping of in-game investments, statistics and calculations

NOTE: the getValue, getListingQuantity, getAveragePrice have a second parameter which specifies if you want the buy or sell orders
      
        ie. If you are pulling information for Bolt (itemID: 30699)
        getValue(30699, "b") --> returns 21000000 (2100g00s00c)
        getValue(30699, "s") --> returns 23449999 (2344g99s99c) Pre 15% Tax
 <hr>
   
<h3>How to format numbers for Guild Wars 2 notation</h3>

  - On the top toolbar click Format > Number > More Formats > Custom number format
  - Copy <b>#0"g" #0"s" 00"c"</b> into the textbox and click apply
  - Apply the number format to cells

<table>
  <th>Unformatted</th><th>Formatted</th>
  <tr>
    <td>12345678</td><td>1234g 56s 78c</td>
  </tr>
</table>

<hr>

<h3>Example</h3>

  <table>
  <th>  </th><th>A</th><th>B</th><th>C</th><th>D</th><th>E</th><th>F</th>
  <tr>
    <td>1</td>
    <td><b>ItemID</b></td>
    <td><b>Name</b></td>
    <td><b>Chat Link</b></td>
    <td><b>Current Buy Price</b></td>
    <td><b>Current Sell Price</b></td>
    <td><b>Average Sell Price (top 10%)</b></td>
  </tr>
  <tr>
<td>2</td>
    <td>30689</td>
    <td>=getName(A2)</td>
    <td>=getChatLink(A2)</td>
    <td>=getValue(A2,"b")</td>
    <td>=getValue(A2,"s")</td>
    <td>=getAveragePrice(A2,"s")</td>
  </tr>
  </table>
  
shows

<table>
  <th>  </th><th>A</th><th>B</th><th>C</th><th>D</th><th>E</th><th>F</th>
  <tr>
    <td>1</td>
    <td><b>ItemID</b></td>
    <td><b>Name</b></td>
    <td><b>Chat Link</b></td>
    <td><b>Current Buy Price</b></td>
    <td><b>Current Sell Price</b></td>
    <td><b>Average Sell Price (top 10%)</b></td>
  </tr>
  <tr>
<td>2</td>
    <td>30689</td>
    <td>Eternity</td>
    <td>[&AgHhdwAA]</td>
    <td>3001g 04s 99c</td>
    <td>3499g 99s 99c</td>
    <td>3575g 00s 48c</td>
  </tr>
  </table>



      
