---
title: "(xorg.conf) need help w/ synaptics touchpad config"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by wastedfluid on 2007-05-22
Okay.

I have the Synaptics touchpad. I'm trying to TOTALLY disable the touchpad - except for it to "move the cursor" - I do not want it to be able to click AT ALL!  I just want it to move my cursor, and use the two mouse buttons under my touchpad.  but I'm having problems. 

 I have set 

Option "Touchpadff" to 2.

However, I still have random clicks(active window changes), as well as some kind of phantom copy/paste thing that comes and goes as it pleases, and pastes anything in my CLIPBOARD to the active text box when i move my cursor.

So.  I was doing some research, and came across this article:

[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

However, in this article, it says.. to load up the ServerLayOut portion.. and
[I]
All the setup except for one section is the same for synaptics and ALPS users. We need to edit the "ServerLayout" section. It probably contains two lines similar to these:

  InputDevice "Mouse1" "CorePointer"
  InputDevice "Keyboard1" "CoreKeyboard"
[/I]

It then wants you to add this line between those two..

[I]
 InputDevice "TouchPad" "AlwaysCore"
[/I]

I don't have either of these.  My "Serverlayout" section looks like this:

[I]
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"Server
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection[/I]

Does anyone know anything about this?  I just want this random tapping, and pasting to go away.. I have gsynaptics, and Touchpadoff IS set to "2" - but I still have random clicking, and was hoping this article could help, as I found this article on another forum where the guy said it helped.  Thanks!!

---

### Post by wastedfluid on 2007-05-22
anyone..? bump.

---

