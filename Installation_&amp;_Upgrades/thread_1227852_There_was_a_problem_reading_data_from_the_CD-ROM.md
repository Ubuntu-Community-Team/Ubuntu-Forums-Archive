---
title: "There was a problem reading data from the CD-ROM"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by geraldm24 on 2009-07-31
Hi everyone... trust my first post [on this forum] to be an installation problem.
Hoping that I can find a solution without having to search the forum hi and lo.

Here goes...

I have tried many methods to run the installtion - with little success.
The last method I tried was the CD image approach.
After copying the ISO file to *hd-media* as suggested, it boots up fine and I can choose my language and keyboard.

I get the following message, saying it can't read the CD-ROM.
[CENTER]
[?] Load installer components from an installer ISO
blah, blah, blah
Failed to copy file from CD-ROM, Retry?

[/CENTER]
I click <No> and it goes back to the screen where I can select an ISO image on the HDD. When I select this, it finds the ISO image in the hd-media directory. I click continue and it goes back to "Failed to copy file from CD-ROm, Retty?

I'm trying to install the following ISO image: _ubuntu-9.04-desktop-i386.iso_
Having read some of the other threads, it seems I could be using the wrong ISO image.
I am now downloading _ubuntu-9.04-alternate-i386.iso_




Some history behind my problems...

I can successfully load _ubuntu-9.04-desktop-i386.iso_ on my work PC using Wubi.exe
However, as this is a work PC, I shouldn't actually be doing it - but the installation works on this PC.

So, I would prefer to run Ubuntu on my home PC, a Pentium 4 (1.6Ghz, 512Mb ram, 160Gb HDD with 2 partitions and a second 20Gb HDD - hope that's enough info), running Windows XP Professional at the moment.

I initially copied the ISO file onto a CD-ROM @ 8X speed - it failed
I then copied the files (unzipped) onto a CD-ROM - Failed to copy from CD-ROM.
I then tried again at a slower speed burning only the ISO file - successfully burnt, but also Fails to copy from CD-ROM at installation.

When I run Wubi.exe at home, it says the installation fails, reloading software will resolve the problem.

---

### Post by aesis05401 on 2009-07-31
Hello,

First thing to try is verifying the contents of the cd.  Problems could have occurred during download, during burning, etc... So Ubuntu has an option on one of the first menus you see to check the integrity of the disk. 

Try running this to see if the disc is written properly.

BTW, you should be using the burn iso method of transferring.

---

### Post by geraldm24 on 2009-07-31
By checking the contents of the CD, do you mean comparing the hash values in winMD5Sum?

I used InfraRecorder to burn the ISO image

---

### Post by aesis05401 on 2009-07-31
> **geraldm24 said:**
> By checking the contents of the CD, do you mean comparing the hash values in winMD5Sum?

I used InfraRecorder to burn the ISO image

Check sum in general.  Doesn't matter what program you use to generate.  The disc has the function on board if you boot from it.

---

