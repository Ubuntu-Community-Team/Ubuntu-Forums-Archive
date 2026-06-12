---
title: "Reprogram Right Alt Key - Programmer Dvorak"
date: 2014-04-30
forum: Hardware
---

### Post by schowell on 2014-04-30
I am using the Programmer Dvorak keyboard.  After upgrading to Tahr (complete re-install), the right Alt key now does not function as an Alt key.  This causes problems when using emacs and when trying to switch between workspaces.  
Looking at the key map (All Settings > Text Entry > small keyboard icon) I see that it is now Level3 S..., though I am not sure what that is.  How can I reprogram the right Alt key to be Alt R (or Meta R)?

---

### Post by rushwest on 2014-06-14
I feel your pain. Upgrading Ubuntu removed the right meta (alt) key and this is a HUGE problem.

---

### Post by rushwest on 2014-06-14
use '***xev***' to find the keycode for your right alt (mines was 108).  

put the following in your ***~/.Xmodmap*** file:

[B][I]clear mod1
keycode 108 = Alt_R Meta_R
add mod1 = Alt_L Meta_L Alt_R Meta_R[/I][/B]

run ***xmodmap ~/.Xmodmap*** to test it out

of course u need to set up ur X11 to load this on start to make it persistent.

[SIZE=2]Edit: apparently ubuntu no longer uses xmodmap ([http://askubuntu.com/questions/325272/permanent-xmodmap-in-ubuntu-13-04](http://askubuntu.com/questions/325272/permanent-xmodmap-in-ubuntu-13-04)) so my solution will cause problems.[/SIZE]

---

### Post by rushwest on 2015-03-07
to remove level3 and return the right alt (right meta) for "English (programmer dvorak)" in xkb do the following:

edit 
/usr/share/X11/xkb/symbols/us

find "dvp" variant 

remove the line 

include "level3(ralt_switch)"

now clear the pre-compiled keymaps before your modifications work:  

cd /var/lib/xkb/
sudo rm *.xkm

reboot or restart (lightd?)

---

