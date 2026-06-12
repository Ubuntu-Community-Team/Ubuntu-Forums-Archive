---
title: "Logitech MX Revolution (14.04) Middle mouse button not working"
date: 2015-09-16
forum: Hardware
---

### Post by egandt on 2015-09-16
Just about ready to give up on Linux and this system as teh mouse will not work, I can not for any reason get a middle button and without it I can not work in Linux.  I've tried:

[https://blog.qpg.us/2013/03/05/logitech-mx-revolution-synaptics-touchpad-in-x/](https://blog.qpg.us/2013/03/05/logitech-mx-revolution-synaptics-touchpad-in-x/)

and

[https://wiki.archlinux.org/index.php/Logitech_MX_Revolution](https://wiki.archlinux.org/index.php/Logitech_MX_Revolution)

Which are the best I can locate online about how to fix the mouse, but neither worked, I've tried everything I can think of.  I did get it to work once but not after a reboot (so no idea why it worked for 5 minutes), and I got the search to work once, but again not after a reboot (again no idea why) and search does not help as reaching it is not practical.  What I need is the mouse wheel on down to act as a third button, as it does in Windows and should have down out of the box.  
I know since I've seen it work it must be possible, but obviously neither of the links above work, so I'm asking since at this point for suggestions, as it is either fix the mouse or drop Linux on this system.  Anyone have an MX that actually has a functional third button on 14.04 and xfce, if so how?

This is why Linux still does not work for most people, since I've used it for years and still wasted 2+ hours on a single mouse button today.

Edit: Best I've found is to get search to act as mouse2 by
/etc/sysctl.d/50-mouse.conf:
# Enable mouse button emulation
#dev.mac_hid.mouse_button_emulation = 1
# Set 2nd button to 217 - the middle button of MX Revolution mouse.
#dev.mac_hid.mouse_button2_keycode = 217
# Optionally reset default mapping of Alt_R to right click
# by mapping right click to a non-existing key
#dev/mac_hid/mouse_button3_keycode = 999

.Xmodmap:
keycode 225 = Pointer_Button2

.xbindkeysrc: 
   "/usr/bin/xvkbd -text "\[Alt_L]\[Left]""
     m:0x0 + b:8
   "/usr/bin/xvkbd -text "\[Alt_L]\[Right]""
     m:0x0 + b:9
   "/usr/bin/xvkbd -text "\[Control_L]\[Page_Up]""
     m:0x0 + b:6
   "/usr/bin/xvkbd -text "\[Control_L]\[Page_Down]""
     m:0x0 + b:7
   "echo 'ButtonPress 2 ButtonRelease 2' | xmacroplay :0"
     m:0x0 + c:225

However search is nearly useless to be, better than nothing, but to hard to hit regularly.

Thanks,
ERIC

---

### Post by efflandt on 2015-09-17
The MX Revolution looks like my MX Master, in which case what you might think is the middle mouse button is not. The middle button just switches whether the mouse wheel clicks while rolling it or spins freely to scroll faster. So your middle mouse button "might" be pressing down on (not rolling) the mouse wheel until it clicks.

My MX Master also has a button below my thumb which does Ctrl+Alt+Tab which was switching windows and could be quite annoying when hit accidentally during gaming. So I switched that in X to be Ctrl+Alt+Home to deactivate that mouse button, but I forget where I did that because currently in keyboard settings Shorcuts, Navigation, both "Switch applications" and "Switch a window of an app directly" both display as Disabled.

My Anywhere MX mouse is different. On that what appears to be the middle mouse button is the middle mouse button.

---

