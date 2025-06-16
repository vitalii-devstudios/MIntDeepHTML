# Exit
When the player clicks the leave icon on the menu we call this function on javascript, the destination string sent is 'menu'

```javascript
SendExitEventToParent: function (destination) {
  var destinationString = UTF8ToString(destination);
  console.log(
    "Sending exit event to parent with destination:",
    destinationString
  );

  var exitEvent = new CustomEvent("unityExitEvent", {
    detail: { exit: true, destination: destinationString },
  });
  window.dispatchEvent(exitEvent);
},
```
Then we close the game

#Score
When the player dies in game we send the score with this function on javascript
```javascript
  SendDataToParent: function (data) {
    var jsonString = UTF8ToString(data);
    console.log("JSON string received:", jsonString);

    // Parse the JSON string and log the parsed object
    try {
      var jsonData = JSON.parse(jsonString);
      console.log("Parsed JSON data:", jsonData);
    } catch (e) {
      console.error("Failed to parse JSON:", e);
    }

    window.parent.postMessage(jsonString, "*");
  },
```
the json string is "score": 999
with 999 being replaced with the total amount of xp collected by the player during his gameplay
