---
title: "Massive hardware problems"
date: 2008-06-14
forum: Hardware
---

### Post by wild_thing2k2 on 2008-06-14
Hi all,
Recently a friend of mine managed to severely damage his laptop, so much so that he had to install a new OS which I suggested he get ubuntu.  I installed version 8.04 and his computer has been absolutely fine; very quick with a few minor adjustments, its been ace.

I decided to install it myself after seeing such a success.  I wish I could say I have had the same success.  It seems that I'm having loads of hardware issues which are really quite irritating.

1)  Booting takes a long time
This is the least of the problems but still annoying.  The ubuntu load bar first goes from left to right (someone on another post pointed out it looked like pong).  After this is starts to fill the bar left to right.  The bar gets stuck at a certain point on the left and stays there for ages.  After about 6 mins or so it continues to the right filling fairly quickly.  After that various commands scroll down all saying ok until it gets to bluetooth and gets stuck there for about another minute.  After reading a few posts about similar problems i removed the splash screen with alt f5 to see what was going on.  It does nothing for ages (again about 6 mins) and then comes up with the following:

184.111665 phy0-7rt2x00usb_vendor_request:error - vendor request 0x09 failed for off set 0x0000 error -110
phy0-7rt2x00usb_vendor_request:error - vendor request 0x07 failed for off set 0x0000 error -110
rt2500usb-init-eeprom@error Invalid RT chipset detected
(another error code)

There was one other line of error, if its needed I'll be happy to write it at request.

2)no sound.
I have a creative x-fi platinum fatal1ty series sound card and so far have no sound.  It doesn't even detect any sound cards are connected but it can't be right because it works in my windows xp partition.  I thought maybe it was a driver issue but I cant find any drivers for this card.

3)graphical problems
This is very strange.  I've tested on two platforms; an Acer al1711 17" monitor and my Samsung 37" LE37M8 1080p tv.  There aren't so many problems with the monitor except when I go into screens and graphics(applications / other / screens and graphics) I try to test it and the screen goes very strange, kinda grey and black dots everywhere except on the top left where it has a box giving a selection of keeping the current settings or not and itll reset in 15 seconds.
Although this is annoying I could live with it as it doesn't effect really affect anything.
The T.V. is a different matter.  Firstly on the login screen the text is so big it doesn't fit in the box and so i cant see what im typing, no huge deal though.  Once ive logged in it doesn't fill the entire screen, theres a black border around the edge.  This is at resolution 1980x1080.  It also cuts off a chunk of the screen on the right and bottom. At 1680x1050 it solves the cut off on the right but not at the bottom.  It also has the same problems with the screen and graphics menu.  I'd like to add that I can't change the graphics driver either, when I select something else it just remains on fglrx.

Computer specs:

AMD 64 dual core processor 4200+
ATI radeon x1300 (not sure the exact model it was bought with it)
2gb ddr RAM
250gb hard drive

If you need more information just ask. Any help on the matter would be greatly appreciated otherwise I may have to go back to windows (gasp!).

Thanks

---

### Post by Cato2 on 2008-06-14
Please ignore - see next post.

---

### Post by Cato2 on 2008-06-14
Maybe I'm stating the obvious, but have you run any hardware diagnostics since the 'damage'?  And what was damaged anyway, and has it been replaced/repaired?

A couple of quick things to try:

* Download and burn a CD of Knoppix - this has good hardware detection and you can turn off USB or anything else you think might be slowing down boot, causing failures, etc.  The Knoppix cheatcodes are good, Google for the list and when to use them.

* SystemRescueCD is a Linux recovery CD that includes utilities to test memory as well as do some basic hardware diagnostics.

For the boot problem - rt2500usb seems to be a WiFi USB stick, try removing that to see if it boots faster.  It's trying something there and timing out I think.

For sound, see the HOWTO in the Multimedia and Video forum.

On the graphics, that sounds weird - see if Knoppix can manage this better.  If not, maybe it's a hardware problem - try another video card to be sure.

Also, try disabling fglrx in restricted drivers (Hardware Drivers in Ubuntu menus, or run restricted-manager from Terminal) - the open source radeon* drivers may be better apart from 3D.  Generally it's better to try the latter first, and only use binary drivers like fglrx once the open source ones are working OK.  

Setup about TV is clearly a bit more complex, suggest you make a separate post about that, including your xorg.conf perhaps.

---

### Post by ljonesj on 2008-06-14
actually i think he said that the friends machine was fixed and he put ubuntu on that machine so he decided to put it on his and his is the one having the problems

---

### Post by wild_thing2k2 on 2008-06-15
> **Cato2 said:**
> Maybe I'm stating the obvious, but have you run any hardware diagnostics since the 'damage'?  And what was damaged anyway, and has it been replaced/repaired?

A couple of quick things to try:

* Download and burn a CD of Knoppix - this has good hardware detection and you can turn off USB or anything else you think might be slowing down boot, causing failures, etc.  The Knoppix cheatcodes are good, Google for the list and when to use them.

* SystemRescueCD is a Linux recovery CD that includes utilities to test memory as well as do some basic hardware diagnostics.

For the boot problem - rt2500usb seems to be a WiFi USB stick, try removing that to see if it boots faster.  It's trying something there and timing out I think.

For sound, see the HOWTO in the Multimedia and Video forum.

On the graphics, that sounds weird - see if Knoppix can manage this better.  If not, maybe it's a hardware problem - try another video card to be sure.

Also, try disabling fglrx in restricted drivers (Hardware Drivers in Ubuntu menus, or run restricted-manager from Terminal) - the open source radeon* drivers may be better apart from 3D.  Generally it's better to try the latter first, and only use binary drivers like fglrx once the open source ones are working OK.  

Setup about TV is clearly a bit more complex, suggest you make a separate post about that, including your xorg.conf perhaps.

Just to clarify its my friends laptop that had damage to it and ubuntu works perfectly on his laptop.  My computer is fine but experiencing all these problems.

Thanks for the suggestion on the wifi usb stick, it boots with great speed now, no problem at all.

As far as the sound suggestion goes I followed your advice in the forum and followed a few links to find that my sound card doesnt have a supported driver for linux yet so am I right in thinking I won't get any sound from the creative sound card until a driver comes out for it, in which case should I get the driver for the on board sound.

I havn't got round to trying out knoppix yet but will keep you posted on whether it helps anything.

I'll try to get hold of the xorg info tomorrow and post that as a different thread.

---

