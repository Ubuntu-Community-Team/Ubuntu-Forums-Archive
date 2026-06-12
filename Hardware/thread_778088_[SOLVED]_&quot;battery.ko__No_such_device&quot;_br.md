---
title: "[SOLVED] &quot;battery.ko : No such device&quot; breaking xserver on *buntu?"
date: 2008-05-01
forum: Hardware
---

### Post by brainstuff on 2008-05-01
Yo! I've been battling with "battery.ko" and a black screen lock-up for about 4 hours now - nothing I tried worked. I started off by installing hardy xubuntu alternative 386 on an old trusty Pentium 3 with 320Mb RAM, and a cheap ATI something or other low-end AGP card. I've selected "all variants" but I must admit I've only tried this with Ubuntu and Xubuntu on 8.04

The plan was to turn the old girl into an Edubuntu box for the kids, plugged only into the TV. So when I started having this problem with battery.ko at the first boot, I thought it must be because it was plugged into my analogue TV and that I'd need to muck around with xorg.conf or something, so to make life easier I plugged in my LCD from my main PC, and started my journey into recovery-mode hell. Everytime it tried loading X the machine would freeze on a black screen after the loader screen.

So I tried all this stuff:

[LIST]from root command line after a recovery boot: dpkg-reconfigure xserver-xorg[/LIST]
[LIST]added these to grub (in various combinations): noacpi nodma nolapic vga=788
[/LIST]

[LIST]Saw a post somewhere which reckoned the install process thought my machine might be a laptop, so I went through the steps and rm'd some toshiba_acpi thing from /etc/modprobe.d[/LIST]

[LIST]Tried blacklisting "battery" as per:
[http://ubuntuforums.org/showthread.php?t=761447](http://ubuntuforums.org/showthread.php?t=761447)[/LIST]

None of that worked, so I was this close to giving up: 
*indicates very small space between finger and thumb*

...Then something tickled the back of my mind...Hmmm ACPI...hmmmm...sounds kinda fundamental...f*** it, why not!

So I reset my BIOS to default. I didn't even write down any settings first. I just did it. **And it worked!** The darn thing booted straight up after all that.

Somebody cleverer and more scientific than me might hopefully be able to figure out what it was - AGP aperture, VGA BIOS shadow, too much cheese before bedtime, who knows. For such an old mobo (with a 1999 Award BIOS) there are surprisingly many options for overclocking that I must have played with over the years and Windows 2K didn't ever seem to mind.

Who knows what other settings got screwed by my dodgy BIOS? Because of all the tinkering with configs etc, I've now gone back and zapped the machine to square one, installed Ubuntu over the top, to (hopefully) make sure any modules, hardware, and all that stuff are properly detected at install. 

So here I am, with a lovely soon-to-be Edubuntu box that I might let the kids have a play with, some time...

Now.... I wonder if I can get Compiz running... :D

EDIT: Dear lord, I get wobbly windows running fine on this box! And weirdly, I think the battery.ko thing might still be happening, so perhaps it was a red herring? Either that, or with the wrong thing ticked in the BIOS it becomes a major thing, rather than a minor one. Bizarre.

---

### Post by Abecedaria on 2008-06-09
I wouldn't call "resetting your BIOS" a resolution. You don't even have any idea what specific setting cured your problem. 

Is there any way we can get this thread reset to UNSOLVED so we can get this problem truly figured out?

abc

---

### Post by OneMixDJ on 2009-05-17
I would like to know about this, even though this is an old thread. 

I just got a "battery.ko" type error for the first time booting up my Hardy machine 5 mins ago. Running xfix gives me the same error. 

If "battery.ko" means that my CMOS battery is going to the crapper, then fine I'll just get another battery. However, the system date & time hasn't flipped out in anyway, nor am I getting any error from BIOS.

Thanks!

---

