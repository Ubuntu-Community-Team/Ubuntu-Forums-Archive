---
title: "HOWTO get the Sylvania MP3 player to work with Ubuntu"
date: 2009-12-26
forum: Hardware
---

### Post by stephanecharette on 2009-12-26
Picked up two Sylvania SMPS1017 MP3 players for Christmas, and was getting ready to bring them back to the store when I finally got them working with Ubuntu 9.10.

These are the .mp3 players in question:  [http://www.curtisint.com/web/browser.asp?productID=SMPS1017](http://www.curtisint.com/web/browser.asp?productID=SMPS1017)

When plugging them in via USB, nothing seems to happen.  By default, it looks like they're doing something that probably works fine in Windows, but gets nowhere in Ubuntu.  Here is what I did to finally get it working:

(All of the following steps are performed on the .mp3 player, not Ubuntu.)

[LIST=1]
[*] unplug the .mp3 player from the usb cable
[*] turn it on (hold down the play button for a few seconds)
[*] when the 4-icon menu comes up, select the 4th menu called "Sys"
[*] press "Mode" (top left button) to enter into "Sys"; you should now be at the "Clock" menu icon
[*] scroll right 8 menu items to one called "Online Device"; this is not in the documentation that came with the .mp3 player
[*] change this setting from "Media Device" to "USB Disk"; press "Mode" to accept
[*] scroll right 1 menu item to one called "Online Mode"
[*] change this setting from "Multi Drive" or "Encrypted Only" to "Normal Mode"; press "Mode" to accept
[*] scroll completely to the right to "Exit"; once again press "Mode" to select this menu
[/LIST]

Now when you connect via USB it should show up as a normal removable drive on your Ubuntu desktop.  Create a folder called "Music" on that drive, and copy your .mp3 files to this folder.  I found that several layers of sub-folders within "Music" also worked just fine.

Hope this eventually helps someone...

Stéphane Charette

---

### Post by S1xp4ck on 2009-12-29
Thought I would add to this thread.  This method works for the SMPS2017 model as well.  Cheers.

---

