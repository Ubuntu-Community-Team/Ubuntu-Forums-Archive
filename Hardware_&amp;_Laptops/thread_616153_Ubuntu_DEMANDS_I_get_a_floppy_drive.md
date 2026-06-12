---
title: "Ubuntu DEMANDS I get a floppy drive"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by gt24 on 2007-11-17
I recently installed Ubuntu on my repaired laptop.  I had an issue with the Live CD where it almost didn't boot... it was generating errors about Buffer I/O errors on device fd0.  While my laptop has a media bay and can take a floppy drive in that bay... I don't have a floppy drive for that bay.  After waiting for 10 minutes, Ubuntu gave up. believed that there was no floppy drive to annoy, and I got into the Live CD and installed Ubuntu.  :)

Now... I installed gparted.  This program will NOT work.  It is stuck on scanning devices.  The syslog viewer shows constant Buffer IO errors reading fd0 and IO errors reading fd0.  Pretty much, I cannot run gparted because it cannot read from my nonexistant floppy drive that Ubuntu thinks exists.

About 10 minutes later... Ubuntu finally gives up and gparted works.  Thank goodness.

This isn't very amusing though.  How can I "REMOVE" this floppy drive?  The laptop model is a Compaq Armada m700.

---

### Post by FrostDust on 2007-11-17
Have you tried going into the BIOS and disabling the Floppy Drive from there?

---

### Post by gt24 on 2007-11-17
It's a Compaq...  in other words it is definition of crippled bios.  I can't even tell the thing to stop trying to network boot.  So, from the bios side of things... I cannot do anything in there.

---

### Post by gt24 on 2007-12-18
An update...

I found a question on this topic which will allow me to temporarily fix this problem.
[https://answers.launchpad.net/ubuntu/+question/7697](https://answers.launchpad.net/ubuntu/+question/7697)

> As Antonio said, don't worry. If it bothers you, try blacklisting the module. In a terminal:

sudo kate /etc/modprobe.d/blacklist

and add this at the end:

# floppy driver since I don't have one
blacklist floppy

Also, if in the file /etc/fstab there is an entry like this:

/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

Add a # in front.

Reboot and let us know if you still get the error message!

This appears to be a kernel related bug.  There is now a bug report on it as well.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/95857](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/95857)

Additionally, it seems to effect other Linux distros.  It tends to effect laptop systems since there is no options in the BIOS to choose if there is a floopy or not since you can shove one into a multibay at any time.  The kernel simply cannot accept that there is no readable content at fd0 and gets hung up on it forever.

Sadly, this appears to have been a bug in 7.04, during 7.10 testing... and now in 7.10...  (ey)

Anywho, I'll have to test this later on this evening when I get home.

---

### Post by gt24 on 2007-12-18
Well, for some reason, I cannot blacklist floppy.  It launches no matter what I do.  I can rmmod floppy after the fact though.

Anybody know how I can blacklist that module?

---

### Post by Tanay on 2007-12-24
Hello to all...
I'm using 7.10 Gutsy Gibbon 32-bit, on a desktop. I also faced this problem. But disabling floppy in BIOS fixed it.

---

### Post by gt24 on 2007-12-25
This appears to be an Ubuntu specific problem to a degree.  I'm not sure if I should post my findings in some bug report...

Fedora 8... I tried that.  It does the same thing... no floppy drive access.  It tries twice and then posts an error message that says that it already saw this error two times and it is giving up.  The laptop seems "stuck" for maybe 15 seconds before going on.  This is much better than Ubuntu's policy of trying for 15-20 minutes before giving up.  Since every other distro gives up rather quickly, the bug isn't all that severe.  Since Ubuntu won't give up, it is a lot more severe in this case.

Eitherways, the Gnome partition manager program will generate this error reliably in any distro.  I saw the bug in a Fedora 8 live CD.  So, if anybody tinkers around with some live cds... you can post your findings here I suppose.

---

