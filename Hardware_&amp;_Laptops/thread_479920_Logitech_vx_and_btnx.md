---
title: "Logitech vx and btnx"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by saldie on 2007-06-20
I used a guide here to get the buttons to work on logitech vx mouse using btnx.
Everything works well except the btnx config. file is set to move through tabs in firefox with the side buttons.
I want to set it to go backward and forward in the web page.
This is the part of the file that needs to be changed:

# Thumb button back. 
# Does a Ctrl+PageDown. Useful for moving through tabs 
# (Firefox, gnome-terminal, etc.)
Button
name	=	Thumb button back
rawcode	=	0x01011300
type 	=	0
keycode =	KEY_PAGEDOWN
mod1	=	KEY_LEFTCTRL
EndButton


# Thumb button forward. 
# Does a Ctrl+PageUp. Useful for moving through tabs 
# (Firefox, gnome-terminal, etc.)
Button
name	=	Thumb button forward
rawcode	=	0x01011400
type 	=	0
keycode =	KEY_PAGEUP
mod1	=	KEY_LEFTCTRL
EndButton


Can anyone please tell me what to change that section to, so I can go forward and back in firefox.

---

