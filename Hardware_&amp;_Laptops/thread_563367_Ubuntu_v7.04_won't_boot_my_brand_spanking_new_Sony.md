---
title: "Ubuntu v7.04 won't boot my brand spanking new Sony VGN-SZ650N/C laptop..."
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by Convert on 2007-09-29
Man, talk about a let-down.

My old laptop finally died.  Never could get the Broadcom wireless card on it to work with any distro of Linux.  So this time I said I will not buy a laptop unless the wireless card is specifically supported in Linux with a driver from the wireless manufacturer...

So, after some research, here I am with my brand new Sony VGN-SZ650N/C (with Intel® PRO/Wireless 4965AGN wireless card) and come to find out the Ubuntu v7.04 won't boot it.  Just for good measure, I also tried Ubuntu 6.10 and it fails to boot properly as well.

Oh good grief, as Charlie Brown would say.  The good news (for me) is that it is something to do with Ubuntu, as the OpenSUSE 10.2 distro boots it just fine.

So for all you Ubuntu techies out there, a little help would be greatly appreciated.  Here is what happens:

I start the laptop with the the CD in the drive.  Ubuntu starts up, everything looks normal.  Then there is a split second flash on the screen with the message "Failed to allocate mem resource: #6 blah blah blah".  Sorry but the message flashes so fast I can't read the rest of it.  All I can say is that it looks like hex code which is mostly zeros.

Anyway, after the super fast flashy message Ubuntu returns to the pretty Ubuntu screen and continues.  We arrive at the startup menu.  I select to run from the CD.  Ubuntu continues for a few moments and then the pretty screen goes away and the following lines are displayed:

     BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)

     Enter 'help' for a list of built-in commands.

     /bin/sh: can't access tty; job control turned off
     (initramfs)

I recognize I'm now sitting at the command line prompt but I have no clue what to do.  When I try to boot from v6.10, I end up at a character graphics screen with the message "Failed to start X server".

Disheartening but I haven't given up hope.  All I need now is for the Ubuntu God to smile down on me and get her devout followers to fix the boot issue (whatever it may be) so that I can try the next release of Ubuntu Linux.

If anyone can tell me what to do so that I can provide more pertinent information, it would be greatly appreciated.

---

### Post by ryanVickers on 2007-09-29
You know something, I was able to install 7.04 perfectly, and it runs great, but *now* my live CD doesn't work at all!  It used to?  what's up!?  (gues I'm not the only one :))

---

### Post by Convert on 2007-09-30
\\:D/  Woohoo, good news.  Ubuntu live 7.10 beta boots my laptop.  It does tell me that it cannot figure out the monitor on the machine and gives me a chance to make some selections.  Using the LCD 800x600 works ok, so I assume I can eventually install the nVidia drivers and get my screen up to it's fully hardware boosted glory.

After booting the live CD, I looked at the hardware that Ubuntu discovered and it looks like it did a better job than generic XP Professional.  And it thinks it found and configured the wireless card.  Unfortunately, it looks like Linux STILL does not support WPA-PSK and TKIP encryption so I'll have to find a wireless security combination for my home that both Linux and Windows will work with.  That, however, I can do, so it looks like I will be dumping my copy of Vista that came on the machine.  And none too soon if you ask me (go ahead, ask me...).

---

### Post by ryanVickers on 2007-09-30
Good to here they did *something* good in gusty! :)  Sorry to be so negative about it, but it seems to me that the feisty to gusty is slightly similar to xp to vista :( with the effects on by default, and stuff like that!

---

