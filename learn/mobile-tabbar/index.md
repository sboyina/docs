---
title: "Mobile Tabbar"
id: ""
---

Tabbar provides a form of navigation between the pages. It comes as a part of page layout and is always at the bottom of the page.

**Notes**:

- Mobile Tabbar comes as part of the page when the page layout with tabbar is selected. It is not available as a ‘drag n drop’ widget.
- Widgets cannot be added to a mobile tabbar.

# Features

**Tabbar** is a list of anchor elements. Based on screen size, only limited number of anchor elements are visible. If the number of the anchors is more than the limit, then a more button is shown on right side. Upon clicking more, a dropdown with the remaining anchors is shown.

Following are the limits:

Screen Size (px)

Limit of anchors

< 480

4

\>= 480 and < 768

5

\>= 768 and < 1024

7

\>= 1024 and < 2048

10

\>= 2048

12

Each anchor requires a label, Icon (icon CSS class) and link. A JSON array containing this information has to be bound to dataset property of the widget, you can create a [Model Variable](/learn/app-development/variables/model-variable/) for the same. Corresponding property names should then be mapped for action label, action icon, and an action link. More Button label and icon are configurable via properties panel. See below for use case example.

[![](../assets/tabbar_props.png)](../assets/tabbar_props.png)

# Properties

**Property**

**Description**

Name

The name is a unique identifier for the Tabbar. Special characters and spaces are not allowed in widget name.

**Dataset**

Value

Set this property to a variable or enter comma-separated values to populate the list of values to display.

**Actions**

Action Label

Label for tabbar items to be picked from the fields of the Dataset Value mentioned above or bound to a variable.

Action Icon

Icon for tabbar items to be picked from the fields of the Dataset Value mentioned above or bound to a variable.

Action Link

Link for tabbar items to be picked from the fields of the Dataset Value mentioned above or bound to a variable.

**Behavior**

Show

Showing determines whether or not a component is visible. It is a bindable property.

More Button Icon Class

This property sets the icon for the more button.

More Button Label

Sets the label displayed on more items button.

# Callback Events

Following events can be used to modify the behavior of Tabbar:

- **On select**: The event listener to call when an anchor is clicked. Using this event user can write javascript code to execute an action, navigate to a page etc.. Three parameters are passed to the event listener:
    1. event object,
    2. the isolated scope of the widget and
    3. The label of the anchor ($item)  on which event happened. _Script Example_:

$scope.form1Beforesubmit = function ($event, $isolateScope, $data) { 
//$isolateScope: $isolateScope of the form
//$data has the data of the all widgets inside the form. This data can be modified and validated before sending the request 

        function isValidData(data) {
            /\*restrict password to be minimum of 6 characters\*/
            if (data.password) {
                if (data.password.length < 6) {
                    return {
                        'error': "Password too small"
                    };
                }
            } else {
                return {
                    'error': "Password field required"
                };
            }
        }
        return isValidData($data)
};

# Use Cases

We will create navigation for the following music app pages using tabbar.

1. Songs
2. Favorites
3. Albums
4. Playlists
5. Equalizer
6. Account

(Assume that pages exist with above names)

## Step 1: Data

1. From the **[Variable](http://[supsystic-show-popup id=121])** on Workspace Toolbar, access Variables to create a New Model Variable.
2. Set the **Type** property to _Entry_ and check the **Is List** option. [![](../assets/tabbar_statvar.png)](../assets/tabbar_statvar.png)
3. Use the TEXT EDITOR under the JSON section to enter the following structure. This structure builds the list as given above. _Note_: In WaveMaker apps, link to an app page with name ‘pageName’ is ‘#/pageName’
    
    \[{
    	"label" : "Songs",
    	"icon" : "fa fa-music",
    	"link" : "#/Songs"
    },{
    	"label" : "Favorites",
    	"icon" : "wi wi-favorite",
    	"link" : "#/Favorites"
    },{
    	"label" : "Albums",
    	"icon" : "wi wi-video-library",
    	"link" : "#/Albums"
    },{
    	"label" : "Playlists",
    	"icon" : "wi wi-format-list-bulleted",
    	"link" : "#/Playlists"
    },{
    	"label" :"Equalizer",
    	"icon" : "wi wi-equalizer",
    	"link" : "#/Equalizer"
    },{
    	"label" :"Account",
    	"icon" : "wi wi-account-box",
    	"link" : "#/Account"
    }\]
    

## Step 2: Design

1. Select the tabbar and bind **Dataset Value** property to the _dataset of the Model Variable_ created earlier [![](../assets/tabbar_bind.png)](../assets/tabbar_bind.png)
2. Set _action label_, _action icon_ and _action link_ to corresponding fields from the Model Variable [![](../assets/tabbar_props_ex.png)](../assets/tabbar_props_ex.png)

## Step 3: Preview App

1. Click **Run** to preview the tabbar. [![](../assets/tabbar_run1.png)](../assets/tabbar_run1.png)
2. When more button is clicked, the remaining anchors will be shown. [![](../assets/tabbar_run2.png)](../assets/tabbar_run2.png)

B.2 Mobile UI Design

- 2.1 Mobile Page Concepts
    - [i. Page Layouts](/learn/hybrid-mobile/mobile-page-concepts/#page-layouts)
    - [ii. Page Navigation & Actions](/learn/hybrid-mobile/mobile-page-concepts/#page-navigation-actions)
    - [iii. Page Transitions & Gestures](/learn/hybrid-mobile/mobile-page-concepts/#page-transitions-gestures)
- [2.2 Mobile Tabbar](#)
    - [i. Features](#features)
    - [ii. Properties](#properties)
    - [iii. Events](#events)
    - [iv. Use Cases](#use-cases)
- 2.3 Mobile Navbar
    - [i. Features](/learn/hybrid-mobile/mobile-navbar/#features)
    - [ii. Properties](/learn/hybrid-mobile/mobile-navbar/#properties)
    - [iii. Events](/learn/hybrid-mobile/mobile-navbar/#events)
    - [iv. Use Cases](/learn/hybrid-mobile/mobile-navbar/#use-cases)
- 2.4 Mobile & Device Widgets
    - [i. Media List](/learn/app-development/widgets/mobile-widgets/media-list/)
    - [ii. Segmented Control](/learn/app-development/widgets/mobile-widgets/segmented-control/)
    - [iii. Barcode Scanner](/learn/app-development/widgets/mobile-widgets/barcode-scanner/)
    - [iv. Camera](/learn/app-development/widgets/mobile-widgets/camera/)
- 2.5 Gesture Support
    - [i. Swipe Gesture](/learn/hybrid-mobile/gesture-support/#swipe)
    - [ii. Limitations](/learn/hybrid-mobile/gesture-support/#limit)