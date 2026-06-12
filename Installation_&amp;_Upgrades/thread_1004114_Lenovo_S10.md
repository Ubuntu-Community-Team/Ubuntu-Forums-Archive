---
title: "Lenovo S10"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by neverkn0wsb357 on 2008-12-06
Hey guys I've been a long time Linux user now and for the most part Ubuntu has been really good about finding and loading the proper packages for the machine in which you're installing it.

So here's the breakdown, I have the most recent update of the Ubuntu Hardy Hereon 8.04 release installed on a little netbook the Lenovo S10 which i am really fond of. I bought the computer with hopes that maybe Ubuntu Netbook Remix would come pre-installed and ready to go, but it wasn't which is alright it gives opportunity for a Project machine. So basically i need your help on this one guys. Ive installed the aforementioned release but the following isn't working and since i cant seem to find any info on people who've done the install I'm calling out to you guys.

The Following doesn't work: (in order of personal importance)

wireless card (Not exactly sure which one the S10 uses)
Integrated Web and Mic
Doesn't have the neat lenovo software

If you guys could help me get to that point I'd appreciate it more than you could imagine so that i could then be on my way to installing Netbook remix. UNLESS the packages have what i need to fix these two inconveniences, the wireless being the most important.

---

### Post by sparty_xubunter on 2008-12-12
Just reporting that I have the same problems.

I have a new S10 and I've been trying Xubuntu 8.04 using a USB drive.  

Wireless card won't show up.

---

### Post by sparty_xubunter on 2008-12-12
Wireless problem now corrected.  Connected my S10 to a wired connection and my Xubuntu 8.04 recognized and downloaded the restricted Broadcom driver automatically.

Might have also been the fact my 8.04 USB stick wasn't updated.

This may not be the place to ask, but are there any comparisons of Xubuntu vs. Ubuntu Netbook Remix for the S10 (or any other small laptop).  Obviously Xubuntu Netbook Remix would be a best of both words but I'm guessing that ain't happening.

---

### Post by dbunting on 2009-01-11
i know you resolved the issue for yourself but i just picked up 2 of the s10 netbooks new for a really cheap price hoping to get one running ubuntu.

im having problems with the system utilizing my wireless card, i was able to manually install the drivers, and the drivers say the detect the hardware but i still canrt get it to function.

and if your still wondering the s10s i have use Broadcom BCM4310 USB Controller wireless cards.

i ran the hardware test and thats what showed up.

maybe ill install ubuntu to the hard drive and have another go, i have been trying it via live USB stick.

---

### Post by sparty_xubunter on 2009-01-28
I would suggest installing wicd to run your wireless - it's much nicer than the network manager (i.e., it doesn't change fixed ip address to dhcp on startup) and wicd is great for XFCE:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Otherwise, I read that changing your wireless to WPA2 might help:

[http://www.s10lenovo.com/viewtopic.php?f=13&t=551](http://www.s10lenovo.com/viewtopic.php?f=13&t=551)

---

