---
title: "8800 GTX blank screen"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by greatkingrat1972 on 2007-07-10
Alright, live cd, full install, anything i do gets me a blank screen on ubuntu
i've been trying ot get this working for months, people say the 8800 is supported , and i can get a gui without nvidia drivers (though i require nvidia drivers) but i am starting to doubt.

Either way, tested out teh newest download of 7.04 (i had beta before) 
won't boot the live cd, or rather it does, but to a black screen, monitor doesnt' shut off but also doesn't show anything...

anyone have any ideas:?

---

### Post by renatoc8 on 2007-07-10
Um, not sure, I have a NVIDIA 8800 GTS and it worked fine out of the box. One note though, if you get it working, don't install the Nvidia driver from Ubuntu (if you try to enable desktop effects it will ask you to), this caused my X to no longer work, instead just visit NVIDIA's website and download from there. I believe it does this because the version in Ubuntu does not support the 8800 series yet.

 -Renato

---

### Post by dabl on 2007-07-10
Use Envy to install the latest Nvidia driver (you must use the 100.14.11 version), and then check out the boot menu edit toward the end of this thread, which may apply to your TFT screen:

[http://kubuntuforums.net/forums/index.php?topic=3084816.30](http://kubuntuforums.net/forums/index.php?topic=3084816.30)

:)

---

### Post by greatkingrat1972 on 2007-07-10
thanks guys, i'll test out teh new 7.10 right now, see if i get a gui to install the drivers from envy or manually

in ubuntu, is it kernel-devel or kernel-source that needs to be installed for manual installation?

testing it now, and i'll post on the results in an hour or so

---

### Post by flowsuit on 2007-07-10
I have the same issue with my EVGA 8800GTS..  looking for answers.. and hoping to fix the problem.

BTW: I've tried booting 64-bit and Alternate Gutsy Gibbon Tribe 2 Live CD

---

### Post by S3NTYN3L on 2007-07-10
I'm a COMPLETE NOOB when it comes to Linux...

I've got an 8800 GTS and I can change the display mode while running from the Live CD (F-4 key) from VGA to the highest res on the list and that works. Graphics suck, but I at least don't have a blank screen...

Now, the install went just fine, but I get a blank screen whenever I boot Ubuntu up...

I've tried booting into the repair/recovery console thing and typing in " sudo dpkg-reconfigure xserver-xorg " but that fixes nothing. Maybe I'm just not configuring it right. I am a complete noob, after all...

Can someone please, for the love of God, hold my hand on this one?

This is about to make me breakdown and :cry:...

---

### Post by greatkingrat1972 on 2007-07-11
alright fellow linux noobs with overpriced gfx cards, we're in this one together, it's been 6 months for me, we're going to find a solution!


Heres what i've found out:

yes, 7.10 gutsy doesnt' fix anything
7.04 DOES work with teh 100.14.11 drivers (though obviously i can't confirm that personally)


i started swapping an old x550 in to get a gui to download the drivers, but i kept missing packages needed for a manual install and got really annoyed with rebooting and switching cards for 3 hours straight.

So, in command line (from recovery mode) how do i download and install envy, cause it said it failed for one reason or another when i did it with teh x550 in in the gui

i don't know much about the command line, i need to download envy, i need to install envy, and then run envy.  If it does indeed install the 100 drivers and all teh extra stuff (kernel source, libc, etc) then in thoery it'll work with 7.04, i've seen posts from guys who have that setup complaining about a problem with winex or whatnot, i WISH i could have issues with wine, that would be much more enjoyable then a black screen (wine atleast i know a bit about)!

---

### Post by greatkingrat1972 on 2007-07-16
Alright, update:
I successfully got envy installed (   it kept giving me errors ><   ) and ran it as envy -t in command line with the 8800 GTX back in.  Black screen , and sometimes it shuts off the monitor.

this is with the 100 drivers, i checked xorg.conf and it says nvidia, i'm slightly confused....
drivers are installed correctly, nothing
i thought teh 100 drivers fixed this problem, i checked out teh other thread, and don't quite understand all of it  :D 

what is the next step to try, i checked the monitor settings, they should work fine...good refresh rates etc.
so as i said before, i'm at a loss to know what to do next.

---

