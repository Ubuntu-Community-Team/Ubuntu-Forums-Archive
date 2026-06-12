---
title: "[SOLVED] Logitech G5 - TiltWheel"
date: 2008-04-30
forum: Hardware
---

### Post by Plasma_NZ on 2008-04-30
Ok yes i know theres heaps of threads on this.. but none of them bring a solution...

Logitech G5 Mouse

Basically something changed with X and tiltwheel no longer functions for "back/forward" in firefox... 

Does nyone have a solution that actually works ad doesnt require installing more apps to utilise the mouse properly...

Have used this guide in the past - but he even states something changed in X and hes not been able to get his working..

[http://adterrasperaspera.com/blog/2006/06/20/logitech-g5-review-under-linux?cp=4#comments](http://adterrasperaspera.com/blog/2006/06/20/logitech-g5-review-under-linux?cp=4#comments)

Im seriously missing not having the tilt-wheel working, as im sure many many others are aswell.... Someone please help !

---

### Post by Plasma_NZ on 2008-05-05
Bump.. someone must have a answer ? or a solution without installing a third-party app ??

---

### Post by Plasma_NZ on 2008-05-05
Ok i've followed a recent post in the above link and have tilt-wheel working using this in xorg.conf

Section “InputDevice”
Identifier “Logitech G5&#8243;
Driver “evdev”
Option “CorePointer”
Option “Device” “/dev/input/by-id/usb-Logitech_USB_Gaming_Mouse-event-mouse”
Option “ZAxisMapping” “invert”
Option “Emulate3Buttons” “false”
Option “Buttons” “9&#8243;
Option “Resolution” “800&#8243;
EndSection

and putting this in the ~/.Xmodmap

pointer = 1 2 3 4 5 9 8 6 7

But now my single thumb-button doesnt open links in a new tab in firefox.. I understand the button mapping has change.. does anyone know a way to fix this.?

---

### Post by Plasma_NZ on 2008-05-06
Ok in Hardy Heron 64bit - Logitech G5 is working flawlessly..

Use the below methods, but to make the thumb-button open links in a new tab swap 2 with 7 in the xmodmap and reload xmodmap etc...

> **Plasma_NZ said:**
> Ok i've followed a recent post in the above link and have tilt-wheel working using this in xorg.conf

Section “InputDevice”
Identifier “Logitech G5&#8243;
Driver “evdev”
Option “CorePointer”
Option “Device” “/dev/input/by-id/usb-Logitech_USB_Gaming_Mouse-event-mouse”
Option “ZAxisMapping” “invert”
Option “Emulate3Buttons” “false”
Option “Buttons” “9&#8243;
Option “Resolution” “800&#8243;
EndSection

and putting this in the ~/.Xmodmap

pointer = 1 2 3 4 5 9 8 6 7

But now my single thumb-button doesnt open links in a new tab in firefox.. I understand the button mapping has change.. does anyone know a way to fix this.?

---

### Post by Plasma_NZ on 2008-05-11
Ok - this is how u do it... make sure evdev is installed already....

put this in your xorg.conf
 In the "section "server layout" remeber to put this in and remove the old mouse identifier..

InputDevice    "Logitech G5" "CorePointer"

Section &#8220;InputDevice&#8221;
Identifier &#8220;Logitech G5&#8243;
Driver &#8220;evdev&#8221;
Option &#8220;CorePointer&#8221;
Option &#8220;Device&#8221; &#8220;/dev/input/by-id/usb-Logitech_USB_Gaming_Mouse-event-mouse&#8221;
Option &#8220;ZAxisMapping&#8221; &#8220;invert&#8221;
Option &#8220;Emulate3Buttons&#8221; &#8220;false&#8221;
Option &#8220;Buttons&#8221; &#8220;9&#8243;
Option &#8220;Resolution&#8221; &#8220;800&#8243;
EndSection

Then make a xmodmap file like so ..
create a file called ~/.Xmodmap and put in it:

pointer = 1 7 3 4 5 9 8 6 2

and run xmodmap ~/.Xmodmap to update your map. On logging in again, Gnome will ask if you want to load this file: click on the file, click &#8220;Load&#8221;, and click &#8220;Ok&#8221;.

Wahlah - working G5 Logitech Mouse with tilt-wheels as back/forward and thumb button for open link in new tab.. drop a post if u are using a 2 thmb button G5 ...

---

