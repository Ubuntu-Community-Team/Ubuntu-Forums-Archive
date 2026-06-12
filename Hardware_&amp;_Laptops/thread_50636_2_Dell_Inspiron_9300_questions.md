---
title: "2 Dell Inspiron 9300 questions"
date: 2005-07-20
forum: Hardware &amp; Laptops
---

### Post by jodar on 2005-07-20
After spending weeks working on my kubuntu installation, I've run into 2 problems I can't seem to fix.

1)  Using the guide found here:
[https://wiki.ubuntu.com//HoaryPM](https://wiki.ubuntu.com//HoaryPM)
I've gotten to the point where I can, by use of the script, enable suspend to ram...problem is I can't get back from it without reboot...my computer seems active still (caps, num lock buttons respond still) but the screen never comes back..I don't have anything I can think of to use as an audible test to see if it is just video or not.  



2)  I keep reading about 1920x1200 and have that in my xorg.conf, but I can't get abovce 1400x990...when I go to the desktop configure thing, it never gives me an option higher than that, even though I've got it in my xorg.conf.


Another small thing, but if someone knows, is the scrolling on my touchpad.  I've actually copied xorg.conf's for THIS COMPUTER that just cause my startx to fail...I don't know why.  I've downloaded all the symantic drivers and stuff....

---

### Post by jodar on 2005-07-21
??

---

### Post by damonw5 on 2005-07-21
[QUOTE=jodar]??[/QUOTE]
 Hi Jodar,

I found this page to be extremely helpful in setting up my Inspiron 6000 (even though it's a 9300 page):

[http://rtr.ca/dell_i9300/](http://rtr.ca/dell_i9300/)

It explains the touchpad, display, and suspend/hibernate issues you are having.

---

### Post by mlord on 2005-07-21
I have a i9300, and *everything* except the SD slot works perfectly for me, after a few tweaks and a replacement kernel.

[http://rtr.ca/dell_i9300/](http://rtr.ca/dell_i9300/)

As for your screen resolution, well.. the i9300 is sold with a choice of screens.  I paid extra for the 1920x1200 display, but yours might only have the basic lower rez one, which could explain the resolution choices you see.

Cheers

---

### Post by jodar on 2005-07-21
yeah, I've used that site for almost all I've done...I'm so new to kernel upgrades and patching though that when something goes wrong, I'm lost.  I'm reinstlaling now to try again from scratch..


as for the screen, I got the 17'', but not the super wide or whatever (does that make sense..I think there is a wide one (mine) then an even wider one after that..)...that's probably it.  

I'll let you know when/if I run into dificulties since you've done y'alls stuff thru that site you might be able to help point me in the right direction. 

Thanks again.

---

### Post by mlord on 2005-07-21
Well, unless you paid extra for the WUXGA (or whatever they're calling the 1920x1200 screen), then yours is probably correct at 1400x990 pixels.

Cheers

---

### Post by dresdn on 2005-07-30
[QUOTE=jodar]
1)  Using the guide found here:
[https://wiki.ubuntu.com//HoaryPM](https://wiki.ubuntu.com//HoaryPM)
I've gotten to the point where I can, by use of the script, enable suspend to ram...problem is I can't get back from it without reboot...my computer seems active still (caps, num lock buttons respond still) but the screen never comes back..I don't have anything I can think of to use as an audible test to see if it is just video or not.  
[/QUOTE]

I'm having the *exact* same problem with my 9300.  I've tried practically everything that I can think of.  I followed everything from [http://rtr.ca/dell_i9300/](http://rtr.ca/dell_i9300/) down to the T to see if any of that would help (minus the DVD firmware patch, haven't done it yet).

I originally had the A03 bios, but then upgraded to the A04 to see if that would help, and it didn't.

I've tried the 2.6.10 kernel that comes with Ubuntu, and also tried my own 2.6.12 with the Software Suspend 2 patches, with no luck.  Also, I've other other distro's such as Gentoo without any luck (same exact problem).  This makes me think I'm missing something, just 1 little thing somewhere.

If anyone has *any* ideas, tips, or tricks to help me get this going, I'd really*100 appreciate it.

-Mike

---

### Post by flyingman on 2005-09-18
try gconf-editor at a command prompt and look for "screen" and "monitor" values. Sometimes Gnome overrides the X settings when it comes to resolution...

---

