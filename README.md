# Sort List By

A script to sort a list of objects by a given key

# Version 

1.0 Initial

# Global Script Setup
1. Create a Global Script called "SortListBy"
2. Add the input parameters below to the Global Script
   1. List
   2. SortBy
3. Add the output parameter below to the Global Script
   1. Result
4. Drag a *JavaScript* action into the script
5. Add the Javascript below into the JavaScript code property
```javascript
/* Stadium Script 1.0 https://github.com/stadium-software/utils-sort-array-by */
let list = ~.Parameters.Input.List;
if (!list) {
    console.error("No list found");
    return [];
}
if (list.length == 0) { 
    console.error("The list contains no items");
    return list;
}
let sortBy = ~.Parameters.Input.SortBy;
let sortMe = (arr, key) => arr.sort((a, b) => (a[key] > b[key] ? 1 : a[key] < b[key] ? -1 : 0));
if (typeof list[0] === "object") {
    if (!sortBy) {
        sortBy = Object.keys(list[0])[0];
    }
    return sortMe(list, sortBy);
} else { 
    return list.sort();
}
```
6. Drag a *SetValue* action into the Global Script and place it under the *JavaScript* action
   1. Target: = ~.Parameters.Output.Result
   2. Value: = ~.Javascript

## Usage
1. Drag the script called "SortListBy" into a script or event handler
2. Enter values for the script input parameters
   1. List: A List of objects or values
   2. SortBy: A key to sort the list by (objects only)
3. Result: The script returns a sorted list of objects or values