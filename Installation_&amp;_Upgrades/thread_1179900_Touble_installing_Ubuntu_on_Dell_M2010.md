---
title: "Touble installing Ubuntu on Dell M2010"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by feeblminds on 2009-06-06
Hey

I've just decided to try installing Ubuntu on my Dell M2010 laptop/desktop replacement.  I use Ubuntu on my PC and at work with very little problems, however I can't install on the M2010.

I boot from CD, click install and it brings up the splash screen but the bar stops 3/4 of the way across the first run and the CD stops.  If I try to 'live' boot it does the same thing.

If however I add 'nousb' to the parameters, it works and takes me to the desired screen, but then I have can't use my USB keyboard or mouse (and the M2010 doesn't have PS/2)!!!  I do have bluetooth mouse and keyboard too but they don't work on the boot screens, I would assume that I need to configure them once in Ubuntu.

Any help or advice would be greatly appreciated as I'm running out of ideas, and don't really want to use another distro or Windows :(

---

### Post by feeblminds on 2009-06-06
Just tried using the 'alternative' ISO,  this gets me to the language selct scrren but then neither the usb or bluetooth key board work.  Strange thing is they both work 1 minute earlier on the splash screen where I selct 'Install'.

Check MD5, that's fine.  Checked BIOS, I have no option for USB legacy support.

Sooo very confused, any any help would be greatly appreciated!

---

### Post by wpshooter on 2009-06-06
What speed are you burning the Ubuntu CD at ?  Needs to be as slow as possible, preferably 4X or below.

Are you checking the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Have you tried the safe graphics mode parameter ?

---

### Post by feeblminds on 2009-06-06
Thank you for your reply.  I've tried the safe graphics, - no difference.  Also tried to verify the disc but it hangs (with the loading bar on screen) at exactly the same point as when I try to install or live boot.

I am just setting it to burn at 2x speed now as I have been burning at higher speeds.  I'm also going to try the v8.04 instead of v9.04 see if it makes any difference (altough I imagine that there has been little if nochanges to the installer).

Thank you for your advice, I will let you know how if the new CD works.

---

### Post by jayness on 2009-10-02
I have exactly the same issue!!  OMG!  So glad i found this thread.  It just stops at 3/4 and then doesnt do anything.  

I have tried a few things but im out of my depth i think..  :(

Any thoughts?

Damn i want this computer to work with Ubuntu!!

---

### Post by feeblminds on 2009-10-02
I thought it was a problem with the RAID0 on the M2010 drives so I reset them as non-raid.  Still same problem.

I've also tried kubuntu, crunchbang and ubuntu live disc.  Non of them work (all hang on splash screen).  On the other hand I ran an old version of knoppix that I had lying around and it worked perfectly.

I think its worth trying the alternative version, will try this weekend and see if I get anywhere with RAID off.

---

### Post by jayness on 2009-10-02
Ive also turned Raid off - i have had massive problems with Vista - and i believe it was the raid set up.  Not sure why but every month or so it would do something terrible to the hard drives and data would be lost - especially in outlook 2007.  

I have just downloaded Ubuntu 9.10.  Lets see if that works.  :)

---

### Post by jayness on 2009-10-02
Ok so it failed again but the set up screen was different - and i got a photo of it.  Does this help anyone!??  lol.

---

### Post by lrcaballero on 2009-10-02
Is your laptop a 32 bit or 64 bit? whatever your answer may be, maybe you want to check into that, I ones had this issue with Fedora, I needed a 64bit install cd/dvd and/or i686 cd/dvd. Try both i386 and/or i686. See if that helps......

:lolflag:

Luis

---

### Post by jayness on 2009-10-02
Laptop is capable of 64 bit..  and thats what i have tried so far. but downloading the 32 bit 9.10 beta version now as maybe it will work better.  Will let you know how i go!

---

### Post by jayness on 2009-10-03
Ok - so i tried again with the 32bit and it failed as well - in a different part i think.  Look at the photo for details...

---

