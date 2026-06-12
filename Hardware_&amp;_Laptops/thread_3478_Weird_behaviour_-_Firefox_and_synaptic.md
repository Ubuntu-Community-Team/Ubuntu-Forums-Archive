---
title: "Weird behaviour - Firefox and synaptic"
date: 2004-11-06
forum: Hardware &amp; Laptops
---

### Post by knappen on 2004-11-06
Am I the only one who experince this weird behavior when running Firefox?

I got a Synaptic touchpad, all works fine. However, when running Firefox I sometimes go back and forward by just moving the curser!!!

It gets so bad that it is difficult moving my finger on the pad without going back to the previous page I was viewing.

I have looked in about:config and could not find anything. I have not installed any plugins for mouse gestures.

This is so annoying :-)

---

### Post by Jspired on 2004-11-06
I have a touchpad as well, but have not experienced this at all.  Sorry I couldn't be of more help.

---

### Post by penipol on 2004-11-06
I experience the same thing on my laptop. I think that this is a feature of Firefox. Whenever I scroll right with my touchpad Firefox moves forward a page and when I scroll left it moves back a page.

I tried to find a way to disable this feature but I could not find the options.

---

### Post by Magneto on 2004-11-06
this is a feature os the synaptics driver
to scroll up and down in a window that has a scrollbar drag the tip of your finger down or up the left edge of the window
tapping in the corners of the touchpad will do things to
scroll left right by moving your finger along the bottom edge of the touchpad

go to google and look up synaptics touchpad
on the main synaptics linux site you will find an in-depth explaination of all the features and ways to edit certain aspects

---

### Post by anklator on 2004-11-07
my synaptic touchpad goes crazy sometimes(in all OS i tryied on my laptoc), so i use a mouse and i have no problem

---

### Post by burriko on 2004-11-07
[QUOTE=knappen]I got a Synaptic touchpad, all works fine. However, when running Firefox I sometimes go back and forward by just moving the curser!!![/QUOTE]

Yes, i get this too, and it's very frustrating.  I've searched for a related option in firefox, but can't find anything.  I though it was possibly mouse gestures, but firefox needs an extension for those.

---

### Post by Magneto on 2004-11-07
[QUOTE=burriko]Yes, i get this too, and it's very frustrating.  I've searched for a related option in firefox, but can't find anything.  I though it was possibly mouse gestures, but firefox needs an extension for those.[/QUOTE]
its the synaptics driver- its a feature readup on synaptics and i dont mean the package manager

---

### Post by knappen on 2004-11-08
Good to hear that I am not the only one :-)

This feature just drives me nuts!

I will see if I can find a solution and will post any my findings here.  If anyone else comes up with the solution, please do the same.

---

### Post by mkosteva on 2004-11-16
[QUOTE=knappen]Good to hear that I am not the only one :-)

This feature just drives me nuts!

I will see if I can find a solution and will post any my findings here.  If anyone else comes up with the solution, please do the same.[/QUOTE]
 same thingself, fixed for me by browsing the HOW TO: Laptop Touchpad  thread at [http://ubuntuforums.org/showthread.php?t=3994](http://ubuntuforums.org/showthread.php?t=3994).

once you get all that done, the config option you are looking for in  /etc/X11/XF86Config-4 is:

Option "HorizScrollDelta" "0"

from synclient -l , it defaults to a higher number: changing to zero disables horizontal scrolling, and keeps mozilla from freaking out.

alternately, i'm pretty sure you can change the pad's edge definition instead of blanket duisableing horiz scroll, but i never use it, and thus disabled it.

---

### Post by knappen on 2004-11-17
Thanks for that!

I will try it tonight, I am sure it will work :-)

---

### Post by knappen on 2004-11-17
It worked fine.

Thanks!

---

### Post by fergus.b on 2005-05-30
[QUOTE=Magneto]this is a feature os the synaptics driver
to scroll up and down in a window that has a scrollbar drag the tip of your finger down or up the left edge of the window
tapping in the corners of the touchpad will do things to
scroll left right by moving your finger along the bottom edge of the touchpad[/QUOTE]
Hi magneto, I've also got this problem and its definitely not one of the synaptic touchpad features. I know all about the nifty features of the touchpads like you mentioned and this is not one of them. Its more like some kind of bug with mozilla and the touchpad. I remember I had the same problem when I was using mozilla on Linux before. Under windows I have my touchpad setup using corner taps, etc, and I've never had this problem. Using Firefox in Linux with the touchpad sometimes causes the browser to navigate a couple of pages back through your history like knappen said. Incredibly annoying!

I've changed my xorg.conf and I'm about to restart my X. I'll let you know the result when I'm done.

---

### Post by fergus.b on 2005-05-30
[QUOTE=fergus.b]Hi magneto, I've also got this problem and its definitely not one of the synaptic touchpad features. I know all about the nifty features of the touchpads like you mentioned and this is not one of them. Its more like some kind of bug with mozilla and the touchpad. I remember I had the same problem when I was using mozilla on Linux before. Under windows I have my touchpad setup using corner taps, etc, and I've never had this problem. Using Firefox in Linux with the touchpad sometimes causes the browser to navigate a couple of pages back through your history like knappen said. Incredibly annoying!

I've changed my xorg.conf and I'm about to restart my X. I'll let you know the result when I'm done.[/QUOTE]
 Yup, thats seems to have sorted it. Thanks for the help chaps :)

---

### Post by gbm85 on 2005-07-15
Actually, this is both a feature of the touch pad and a feature of Firefox.  It's not a bug of either.  For some reason, under Linux (and apparently under OS X, which is *nix-based), Firefox defaults to using horizontal scroll for going back/forward instead of actual scrolling.  I found the resolution at the following URL:

[http://www.vectified.com/2004/11/horizontal-scrolling-in-firefox.php](http://www.vectified.com/2004/11/horizontal-scrolling-in-firefox.php)

You just have to open up about:config and change the following settings:

mousewheel.horizscroll.withnokey.action => 0
mousewheel.horizscroll.withnokey.sysnumlines => true

I tried it on Fedora and it works perfectly.  And my pad still has horizontal scroll! :)

---

### Post by hayim on 2007-12-29
haha! gbm85, thanks for pointing out the mozilla options! now finally i can get my horizontal scrolling = forward/back feature ***back***!!

how i missed it so...

for anyone who's interested, set the ...withnokey.action to **2**, set numlines = **-1** for right/forward, left/back,  and sysnumlines to **false.** (any other combo of numlines and sysnumlines seems to result in reversed scrolling direction)

enjoy!

---

