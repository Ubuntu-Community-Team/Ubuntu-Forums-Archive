---
title: "Edit menu.lst to delete a OS title"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by raymondh on 2009-06-15
A little stumped here ... and in behalf of a friend.

Had 8.10 installed in an external HD which was deleted. Installed 8.10 thru WUBI.  Windows and Ubuntu (wubi) working well.  

Boot gives 3 options .... Windows, Ubuntu and Ubuntu-Linux.  Would like to delete one Ubuntu entry which does not work anymore (am thinking it was for the 8.10 external HD install which is now deleted).

Went to /boot/grub.menu.lst to try to remove from there but menu.lst shows only one (1) ubuntu 8.10 install (2 kernels as well as the recovery and memtest options) as well as the XP install.

Am stumped.  How can I/we remove the extra Ubuntu option in the boot-up?  That extra Ubuntu option, when highlighted and enetered, just produces a blank screen with the blinking cursor.

Do I edit from the grub boot menu (with the 'e' option)?

Thanks in advance for your tips/advices.

---

### Post by merlinus on 2009-06-15
It sounds like a wubi problem, Raymond.  You can edit the grub menu on the fly by pressing the e key, but the change will not be permanent.

There may another menu.lst file somewhere, perhaps in windows.  Maybe a search?

Gotta love the name -- wubi.  Does it remind you of anything?

---

### Post by raymondh on 2009-06-15
> **merlinus said:**
> It sounds like a wubi problem, Raymond. 

Gotta love the name -- wubi.  Does it remind you of anything?

LOL :)

Thanks merlin ..... I too, was thinking of a menu.lst inside windows.  

Merlin, let me throw this up for pondering, if it's OK with you.... 

WUBI being part of windows, does the windows bootloader have authority in boot or does GRUB have it? To be specific, does GRUB boot or does the windows bootloader do it... in a WUBI install?  I ask because we know that on a non-wubi install, GRUB overwrites the MBR hence "has the ball" .... I just don't know on a WUBI install.  

If you think/say windows has the "ball" .... then could it be that the sole UBUNTU in the menu.lst we just pulled up be the one that I can remove?  

I could cp that list and test it out ... just wanted to throw it up for opinions/suggestions first. 

In the meantime ... am giving this my best google-fu :)  Will post back any outputs/solutions.

Thnaks again.

---

### Post by merlinus on 2009-06-15
I don't know about which has the booting priority, grub or windows, as I have never used wubi.  Presence1960 has been playing around with it, however, so you might either PM him or wait until he's on the prowl.

I will be very interested to hear how you make out with this situation.  Great idea to cp the file and delete the entry it might be.

---

### Post by presence1960 on 2009-06-16
Raymond, I don't mind the PM. I am in wubi right now. My system is set up with Jaunty, Hardy & Windows XP. I installed wubi to see how to install it & see how it runs. Just wanted to increase my knowledge. Here's what I know so far which may shed some light on your situation. My Jaunty GRUB is installed to MBR of first boot disk. Hardy is on same disk but GRUB is installed to it's partition. I chainload Hardy on Jaunty's menu.lst. Windows is on second disk.

When I boot to get to wubi I choose XP from Jaunty's GRUB menu. Then I get the menu that gives me a choice of Windows or Ubuntu. At that point that is controlled by the windows bootloader because at the bottom of the page it says press F8 for advanced start up options.

Once you choose wubi then the menu.lst of wubi takes over. it is located in the same directory as a regular install. I noticed on my wubi menu.lst it has every instance of each OS on my system.

If the non existant OS is not able to be edited in wubi's menu.lst see if you can edit it in windows. I'd have to go back in and see where but I think it is Control Panel> System > Advanced in XP. Or possibly the boot.ini file needs editing.

Hopefully this helps the situation. Off to work now. Will check back tonight after my daughter's Tae Kwon Do class.

---

### Post by raymondh on 2009-06-16
Thanks for having a look-see and your inputs, Presence1960.

Will have a browse inside windows. 

Thanks again :)

---

### Post by presence1960 on 2009-06-16
No problem. One hand washes the other in here.

---

