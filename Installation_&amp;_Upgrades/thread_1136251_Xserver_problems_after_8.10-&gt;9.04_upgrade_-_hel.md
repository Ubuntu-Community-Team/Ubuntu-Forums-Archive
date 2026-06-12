---
title: "Xserver problems after 8.10-&gt;9.04 upgrade - help please"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by andyj1 on 2009-04-24
Hello,

This should be easy (?) for somebody familiar with X server setup.

Here is my problem.  I have a pretty generic Acer box with Intel 810 (on the MB) video.  Worked fine in 8.10.  Last night I did the upgrade to 9.04.  Everything went smoothly but when I got to the last part (rebooting) I was getting:
1.  Regular Grub menu with the new kernel.
2.  Splash screen Kubuntu with the horizontal "meter" bar
3.  A strange looking about 1"" wide grainy purple screen
4.  After that a black screen with some very grainy strings Kubuntu
5.  Nothing beyond that.  Have to do hard restart to get back the machine.

I downloaded the ISO distribution and burned it on the a CD.  This starts and runs on the same machine without a single problem.

How do I fix this.  I do not want to install from the CD if I can avoid it.

Here are a few other pieces of info.

1.  I can run fine in the recovery mode.
2.  The "automatic fix of X problems" does not seem to help at all
3.  I dropped to the "netroot" command mode and did
apt-get install --reinstall xserver-xorg-core - nothing changed
4.  I did
dpkg -reconfigure xserver-xorg
It only took me through the keyboard configuration.  After the last OK it just gives me back the prompt.

Any suggestion will be greatly appreciated.

Thanks in advance,

Andy

---

### Post by radamo on 2009-04-25
I have the same issue... Not sure what to do.
RA

---

### Post by hockman5 on 2009-04-25
I have exactly the same problem. Graphics card is a ATI Radeon HD2400 PCI. HAven't solved yet.

---

### Post by omeomi on 2009-04-25
Same problem here. Video card = nvidia 9500gt. Solution = unknown

---

### Post by jackal_twister on 2009-04-25
I did the upgrade through the update manager followed all the steps and xserver just wouldnt load I did the sudo dpkg-reconfigure xserver-xorg and the desktop loaded, but i want my 3d desktop settings and I cant get the Nvidia drivers to work, I want to roll back

---

### Post by thomasgoot on 2009-04-25
Yep, me too. Toshiba satellite with ATI Radeon HD 2400...
workin' on it but not very quickly since I don't know wtf I'm doing...

---

### Post by jackal_twister on 2009-04-27
Has anyone even remotely come up with a fix for this?

I loved the way 8.10 dealt with Nvidia cards, with the hardware drivers auto detection and download of new drivers. why cant they just go back to using that? I tried to activate the drivers but it wont let me!

Does this mean we need to install and use envy again?

---

### Post by jackal_twister on 2009-04-29
Hi all, just as a heads up, I tried getting drivers through envyng, it doesnt work!

---

### Post by caver1 on 2009-04-29
I had similar problems to yours and the Xserver/Nvidia drivers.
The only way I was able to overcome it was to do a clean install instead of an upgrade.
After a clean install no problems what so ever.
caver1

---

### Post by StuartN on 2009-04-29
> **jackal_twister said:**
> Has anyone even remotely come up with a fix for this?

If you have an ATI card, were using the proprietary driver (Catalyst / fglrx) and upgraded, then this guide to erasing all traces of the previous driver settings might help: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by emarkay on 2009-04-29
Let's get all the Jaunty 9.04 ATI HD 2 series card data on one post to get this solved:

[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

---

