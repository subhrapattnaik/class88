# class88


https://snack.expo.dev/@subhra/storytelling-88-kavya


//login to gmail with the same gmail id(make sure you are able to check inbox)-in the mobile
//scan the qr code 
//ogin to the story telling app from same gmail id--in the mobile
//so that the app can store the user details into the firebase --users
//then add story by clicking on plus (new story page)


*********************************************************
class89:
-------------
our side drawer is still plain white and does not match with the App.

start with the custom design for the Drawer Navigation.

we will have to create a custom UI and then use it in the Drawer Navigation.



DrawerNavigator.js
------------------

will first import firebase and convert const DrawerNavigator into a class component from a functional component -
As we are adding export default here make sure to remove the export statement written as the last line from the previous class.
Now, similar to how we created the componentDidMount() in the Tab Navigation, we will do the same here as well -


 we’ll add our Drawer Navigator inside a render() function -
 
 we’ll add an attribute drawerContentOptions to our <Drawer.Navigator> component -
 
 we will add another attribute drawerContent in which we can define our custom menu for the Drawer -
 
 we have created a variable props as this.props is in our render() function above.
We will also have to import CustomSidebarMenu, a component we are yet to create

Let’s import it first -

With the drawerContentOptions and the drawerContent attributes, we are explicitly telling Drawer.Navigator to use a component called CustomSidebarMenu and are setting relevant properties for it like activeTintColor, inactiveTintColor, and itemStyle (the style for the options in the menu).

CustomSidebarMenu.js
----------------------

Inside this component, we will have our constructor() and componentDidMount() function -


render() function 


Here, we have a <SafeAreaView> component for our drawer in which, we have put the logo of our App in a <Image> component.
Next, we have our <DrawerContentScrollView> component in which we will place our drawer’s content and our drawer’s content from our drawer navigator is available to us in the <DrawerItemList> component, which we have inside it.

  With all the code we just went through imported into our DrawerNavigator, our UI now looks like -
  
  ------------------------------------------
  
  
  
  like button functionality.
We already have the like button in our StoryCard and StoryScreen.

  
  
  start by adding two states in our constructor within StoryCard.js -
  
  is_liked,likes
  
  first state is, for if the story is liked, which is false by default. We also have stored the number of likes separately for now.
Next, let’s add a <TouchableOpacity> component around our like button so that we can make it clickable -
  
  
  Here, we have used a function likeAction() with the onPress event of our <TouchableOpacity>
Let’s now change the styles of the likeButton. We want it styled differently for when it’s liked and when it’s not liked -
  
  Here, based on if the state is_liked is true or false, we are giving our View container for the like button different styles. Also, note that we are not using this.state.likes for our number of likes.
Let’s add the styling for likeButtonLiked and likeButtonDisliked 
  
  Now we still have to create our likeAction() function, so let’s do that -
  
  Here, if the state is_liked is true, that means that the user has disliked the post. This is because we are not yet changing the state of the button and hence, it was previously liked.
If that’s the case, we are reducing the number of likes by 1 (by using increment(-1)) and updating the states accordingly.
If however, the user has liked the post, we are increasing the number of likes by 1 and then updating the states accordingly.
Note that we had our unique ID for the story stored in our state, and we are using it to identify which story it is on which we want to perform the given operation.
  
  -------------------------------------
  now recreate this and add the like functionality in the StoryScreen as well.
  
  
  Remember that since we passed the story from one screen to another through  navigation and not from the parent component to the child component directly, the story's data will not be accessible to us with this.props.story.
Instead, we will be using - this.props.route.params since our route is a prop for our
Navigation and the story has been passed as a parameter.//
  
  
  
  We change the code for our Like Button to check if it has been clicked or not; we are using a ternary operator to change the style depending on the result of Like Button pressed and also calling this.likeAction() function written below:
  
  Add styles for it -
  
  We are then creating our likeAction() function -
  
  he student runs the code and clicks on the heart to add the number of likes.
  
  
  ---------------------------------------------
  
  
  
