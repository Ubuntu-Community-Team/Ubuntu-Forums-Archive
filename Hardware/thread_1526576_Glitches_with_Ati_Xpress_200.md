---
title: "Glitches with Ati Xpress 200"
date: 2010-07-08
forum: Hardware
---

### Post by DannyBiker on 2010-07-08
I know, that integrated card isn't supported by Ati since 7.04. Since then, things have gone downhill every release at a time. In Lucid though, things are getting worse. I get small lines that come and go all the time on my screen and sometimes, the screen just displays crazy glitches such as :

[IMG]http://membres.multimania.fr/mellow44/hpbimg/Capture.png[/IMG]

or

[IMG]http://membres.multimania.fr/mellow44/hpbimg/Capture3.png[/IMG]

and even this (it should be a image, not a black square !) :

[IMG]http://membres.multimania.fr/mellow44/hpbimg/Capture2.png[/IMG]

After a few seconds or minutes (!!!), everything goes back to normal. But only for a while...

What should I do to resolve this ? I've been testing Ubuntu on my machine for a long time now and while at first, I had problems due to specific hardware or needs, it's been several versions now that I have to struggle for basic stuffs such as browsing the web or connecting an external hard drive...What a shame.

I hope there is a solution for this problem. If not, well...Fedora here I come !:(

---

### Post by mörgæs on 2010-07-08
This might help:

[http://ubuntuforums.org/showthread.php?t=1525254](http://ubuntuforums.org/showthread.php?t=1525254)

---

### Post by DannyBiker on 2010-07-09
Actually, no...

---

### Post by JHCKX on 2010-07-09
I haven't had problems as bad as yours (I have a Packard Bell MZ35 laptop with a Radeon Xpress 200M video card) but I have noticed that video performance in 10.04 was slower than with 9.04 (9.10 never worked properly on my computer). For me, a solution was to install the xorg edgers package. This provides beta versions of video drivers, at the risk of system instablity. But in my case, video performance is much better and I've had no real problems. 

See the instructions on
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
 
Update your system and most of the Xorg programs will be updated.

See also [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/576125](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/576125)

---

### Post by DannyBiker on 2010-07-09
Thanks, I'll try that later today and will tell you how it went...;)

---

### Post by DannyBiker on 2010-07-09
Okay, the xorg ppa didn't worked for me. I got an error message on boot and can't access the OS.

---

### Post by DannyBiker on 2010-07-09
F***...I had to force the computer's shut down due to the error message and since then my wireless keyboard isn't working anymore !
If the thing is broken, this is my last Ubuntu install.

**** Linux.

---

### Post by mörgæs on 2010-07-09
I have never heard of Linux breaking a keyboard. Are the settings in bios correct? Does the keyboard work on a boot with a live CD?

---

### Post by Oriana on 2010-07-24
If Grub's still working, choose recovery mode (for single-booters I think you have to "press esc within 3 seconds of boot"), choose root terminal, install ppa-purge from the xorg-edgers ppa (assuming you didn't already remove it) and then remove the xorg-edgers ppa using ppa-purge. Like so:

```

# apt-get install ppa-purge
# ppa-purge xorg-edgers

```

It restored my computer from that same error with same cause to working again. Good luck!

---

### Post by r6_cannibal on 2010-07-27
I tried this as well, i'm basically running a dell optiplex with a slim ATi x600. 
I did some research before buying the card off of ebay for 10 bucks to make sure it had linux support, my mistake was not searching for my version (jaunty) =P

I also tried the edger source and updated, it installed a handfull of files but i am still getting the same artifacts on my desktop. for icons and such. i did not get any errors on boot, but no change to the problem either. 

How would i be able to tell that the changes took effect properly? 

Thanks!

---

