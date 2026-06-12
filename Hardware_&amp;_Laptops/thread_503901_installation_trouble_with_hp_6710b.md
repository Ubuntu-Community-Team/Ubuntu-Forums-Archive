---
title: "installation trouble with hp 6710b"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by crash0 on 2007-07-18
hello,

i just bought an hp 6710b laptop with intel core 2 duo, 1 gig ram, 160 hdd, mobile intel graphics, integrated wireless and bluetooth, etc.

at first, i couldn't even run the installer because it would display "can't start tty, job control turned off", so i solved this by downloading the alternate install version... the install went pretty ok (although i had a lot of trouble configuring the keyboard) but when i tried to start feisty for the first time, an error appeared, after which i was sent to a console.

there's a long error report, i couldn't copy the whole thing, but the essential line (as far as i'm concerned) is the following:

"Screen(s) found but none have a usable configuration"

i read the whole thing and it says something about vesa drivers... i understand that's some sort of default for the intel graphics, because i had to use vesa on a few live cd's such as the gparted live cd.

my screen resolution is 1280x800 (at least on windows...)

later, i managed to start setup from the livecd, but the same error appeared just before the live ubuntu was about to appear (just after the usplash proggress bar came to 100%)

i searched the forum a bit, and it seems this error appears on a few other threads, such as:
[http://ubuntuforums.org/showthread.php?t=500288](http://ubuntuforums.org/showthread.php?t=500288)
[http://ubuntuforums.org/showthread.php?t=498120](http://ubuntuforums.org/showthread.php?t=498120) (not in the first post)
[http://ubuntuforums.org/showthread.php?t=452697](http://ubuntuforums.org/showthread.php?t=452697) (same laptop and graphic card but different error)
these threads however didn't help me much beacause the error is not exactly the same...
any help is appreciated

---

### Post by tower_ on 2007-07-21
just try :

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xserver-xorg-video-intel

then edit your xorg.conf and change "Driver" to "Intel"

then add 

intel_agp
agpgart

to your /etc/modules file

finaly: restart xserver or reboot


see also:

[http://mytwu.blogspot.com/2007/07/how-i-installed-ubuntu-feisty-fawn-on.html](http://mytwu.blogspot.com/2007/07/how-i-installed-ubuntu-feisty-fawn-on.html)

---

