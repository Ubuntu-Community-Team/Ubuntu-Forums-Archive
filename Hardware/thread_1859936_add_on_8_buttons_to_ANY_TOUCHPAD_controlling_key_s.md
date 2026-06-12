---
title: "add on 8 buttons to ANY TOUCHPAD controlling key strokes FOR FIREFOX CHROME"
date: 2011-10-14
forum: Hardware
---

### Post by Enterpart on 2011-10-14
You will need easystroke and thats all

```
sudo apt-get install easystroke
```

youtube video showing how to work easystroke

[www.youtube.com/watch?v=sOWXAyOde18]("http://www.youtube.com/watch?v=sOWXAyOde18")

add an action Name it anything type:command and paste this in the command box

```
#!/bin/sh
#
# Use xinput --list-props "SynPS/2 Synaptics TouchPad" to extract data
#

# Set multi-touch emulation parameters
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

# Disable edge scrolling
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 8 0 0 0 

# This will make cursor not to jump if you have two fingers on the touchpad and you list one
# (which you usually do after two-finger scrolling)
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 32 110

synclient tapbutton2=2
synclient CircularScrolling=1
synclient LTCornerButton=9
synclient RTCornerButton=10
synclient RBCornerButton=11
synclient LBCornerButton=12
synclient TopEdge=2431
synclient RightEdge=4700
synclient BottomEdge=3689
synclient LeftEdge=2356


```

this will add 2 finger scrolling, 2 finger tap for middle click and circular scrolling also

now "Record gesture" (see the video) you can set the Gesture button to be left click if you want. Record a circle for this gesture. NOW PERFORM THE GESTURE
your settings will have changed to check use this

```
synclient -l
```

and check what it says at TopEdge it should say 2431

ONLY THEN WILL THE NEXT PART MAKE SENSE

now in easystroke go on Preferences tab and click additional Buttons
then click add
then click the box with no writing on and choose 9 press OK and repeat adding buttons 10 11 12

now your touchpad is configured with the corners as button 9 on top left and it goes clockwise with button 10 top right, button 11 bottom right and button 12 bottom left.

now in easystroke go on "Advanced" tab and check timeout gestures (it should now have a tick next to it)

to set the corner buttons with key strokes do this

"add action" then for type click key record the key (you can press 2 or 3 keys at once and it will record those key strokes
once you click Record Stroke and tap on a corner of the touchpad
(make sure its the corner) it will pop up with 

"You are about to bind an action to a single click.  This might make it difficult to use Button 1 in the future.  Are you sure you want to continue?"

thats why make sure its at the corners and your activating the buttons 9-12 and not button 1

press yes and you should have set one corner as a keystroke such as Alt+left arrow for backpage on internet if you so wish

IF YOU ACCIDENTLY MISS THE CORNER KEY just press "Return" key on keyboard then "right arrow" and "return" key again it will delete the gesture and you can start again.

now in the future you can easily change the keystroke associated with each corner

set the other 3 corners

now for the last four keys all you have to do is double tap on any corner and hold (WHICH YOU USE A GESTURE) for 2 seconds then let go. which will count as another button. each corner can be used like this.

you can also open applications like firefox for example, after you add an action, in the type choose command and then past

```
firefox
```

basically you can do anything since you got control of the terminal this way.

oh and to load easystroke at boot you want to go to preferences and check "autostart easystroke" and at boot you want to perform the initial gesture to activate that big command I gave at the beginning

show your love by replying with thankyou

---

### Post by Enterpart on 2011-10-15
you can also use the touchpad to control volume, double tap the corners and move down for the gesture and it is like controlling a scroll wheel. and then do another gesture this time scrolling in anti clockwise direction and this can be volume down. then try the gesture. since you got 4 corners you can use 4 different scroll wheels controlling things like brightness and even zooming on website. try it out

---

### Post by Enterpart on 2011-10-15
this is how to configure the tap zones to how big you want them

[http://ubuntuforums.org/showthread.php?t=1824870]("http://ubuntuforums.org/showthread.php?t=1824870")

---

### Post by durand on 2011-10-15
Nice post! I've been trying to get circular scrolling working like it used to Maverick and below for ages. As for the rest, my touchpad is too small for it to be particularly useful but it's a good tut nevertheless :)

---

### Post by Enterpart on 2011-10-15
Glad you liked it Durand I just want to add that if you use easystroke you can use the scroll wheel to control more than just scroll this is how.

course you need easystroke

enable mouse button 1 through preferences and additional buttons

then once you performed the first script I gave in my original post. you perform an action, make it a key type and for the key I just whatever key you use to put volume down. and for the gesture double click on the top edge and without letting go slide down. 

you should see the gesture as a red number 5

do it again and for the key this type increase the volume. and for the gesture again double tap on top edge and this type go anticlockwise and you should see the number 4 red

now you can by double clicking the scrolling area and going clockwise or anticlockwise control the volume

you could control anything even zoom in and zoom out the way I do.

---

### Post by Enterpart on 2011-10-15
lastly you can use PINCH TO ZOOM using the last tip by adding button 2 as an additional button

then for the gesture double tap on touchpad and slide up
you should see for the gesture a a number 2 -> 4 and you can set the key as Ctrl + + that will increase the screen and do the same for zoom down by double tapping and sliding down. I'm going to do a better tutorial when I have time for this. but If you got any questions Im happy to reply

---

### Post by durand on 2011-10-15
How do you remember all those gestures?! I struggle with just a few...

---

### Post by Enterpart on 2011-10-15
lol I have about a 100 that I use regularly I remb them because they have recurring patterns that fit together. Its best if I show by example

[ATTACH]204465[/ATTACH]

oh and I have mainly gesture set up for internet

now in that image you can see that I think how I can easily remb the gesture so for moving to tab to the right I slide to the right
and tab to left is left
now to get rid of the tab its a simple line to the top left corner. so it makes sense that if I wanted the tab back I would swipe in the opposite direction
for back page I do a swipe like I'm turning a page on a book to see the previous page like your rolling it bacwards. then simply If I want a forward its the reverse of that one. Simple and easy to remb because they follow naturally. and find is like it pops down so its down up. and history is up down.

now look at these commands

[ATTACH]204463[/ATTACH]

these are commands to control the windows of applications. I wanted simple commands so I can remb but also easy to stroke and remb. and because I already used a single line I thought why not use an arrow (even though they dont look like arrows, they are because you draw slightly diff in practical) so as you can see minise a window is an arrow facing down.
you cant see but maximising will be an arrow facing up
and the arrows are almost have the same rotational symmetry.
and windows to right has an arrow to the right and windows to left has an arrow to left.
and exiting a window I got an arrow to top left corner. can you start to see they compliment each other in a "set" but also with all my commands.
now move window is like picking it up and moving away so its an arrow top left. and an arrow moving within itself is like making it smaller "resizing it".

lastly

[ATTACH]204464[/ATTACH]

these took a while to think of, they control things like copy and stuff
well I started with paste since we use control + V I thought I would use a v sign and what is the opposite of paste = copy so its a v but backwards. now the all function is like an A but that is like a v with mirror image.
and a v pointing to the left is like deleting something so that what I did.
and the opposite of delete is undo so I did that with the same as delete v but reversed the starting point of my v

you cant see but a forward v is for "return" key

now all I've done is use three symbols and made like 20 gestures but they each tell how to use each other. If that makes sense. Im going to one day post all my gestures so you can see how I done them. I have lots more but they use like only 2 or 3 more symbols but symmetry of each other and follow rules. I REALLY THINK UBUNTU SHOULD ROLL OUT WITH THIS WITH GESTURES LIKE MINE INCLUDED

trust me when I say this is the best browsing experience ever I can do anything and everything with just swiping. I showed you how I highlight and I can search in a search engine well Ive got a great system for that to.

Ive got some more tips coming so stayed tuned

---

