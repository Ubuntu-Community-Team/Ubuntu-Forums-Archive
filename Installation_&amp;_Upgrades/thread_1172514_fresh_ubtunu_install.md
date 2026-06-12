---
title: "fresh ubtunu install"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by nategerr on 2009-05-28
My last request for help thread seems to have disappeared after one reply so here goes again:
I am having one helluva time getting linux on this machine of mine and breaking the old ball and chain of Windows XP. First I downloaded mandriva and tried to boot up. No dice ("fatal initialization error"). Now Im testing my luck with ubuntu 9.04. I downloaded the iso file, **copied the image to cd**(check!) with Active ISO **and** Fienman ISO recorder ,stuck both copies in and tried to install on a freshly formatted 80G hard drive. do I need to do something in the format (NTFS or FAT32)? I have one partition of each just to be safe. I tried downloading both the 32bit and 64bit versions of ubuntu still nothing. What operates on this bit rate? my procesor? File system on hard drive? My computer won't even boot with cd or at all since it's formatted. just says "remove disk, media and press anykey to restart" ARRRGH! I did build this computer myself with only minor electrocutions and fire so I'm not usually a dumbass around these things but without a command prompt, I'm lost. I would welcome any help, advice or prayers

Here's my computer
Asus p4pe ,P4 2GHz
512Mb pc2700
80G Western Digital
Fujitsu DVD Burner/reader

Thanks guys
Nathan

---

### Post by merlinus on 2009-05-28
Since I was the one who replied to your original message, here goes again.

You stated that you **copied the image to cd.  **Have you looked at the contents to make sure that there are directories and files, and not just one file?  If so, then you might try burning it at a slow speed (4x or less), and do a checksum on the .iso.  (info on this here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM))

I do not believe your processor is 64-bit, so use the 32-bit version.

---

### Post by wpshooter on 2009-05-28
copied the image to cd(check

NOT CHECK !!!

Try "BURNING" the ISO image to the CD instead of **_copying_** and I believe you will be on your way.

P.S. - Make sure after you get the ISO properly burned and boot to it that the FIRST thing that you do is, check the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu.

---

### Post by nategerr on 2009-05-28
yup, all the files/directories are there 698Mb. wubi.exe, readme etc. check sum =
66fa77789c7b8ff63130e5d5a272d67b matches what I'm told should be there for 
ubuntu-9.04-desktop-i386.iso. is this the right down load for me?

---

### Post by wpshooter on 2009-05-28
> **nategerr said:**
> yup, all the files/directories are there 698Mb. wubi.exe, readme etc. check sum =
66fa77789c7b8ff63130e5d5a272d67b matches what I'm told should be there for 
ubuntu-9.04-desktop-i386.iso. is this the right down load for me?

If for nothing else but my piece of mind, can you confirm that you **BURNED** the ISO image to the CD and not just copied as DATA ?

Thanks.

---

### Post by nategerr on 2009-05-28
10-4. burned with Active ISO Burner and Feinman ISO Recorder not just copied and pasted. My new CD will open and is explorable on my XP machine but will not boot my formatted drive.

---

### Post by merlinus on 2009-05-28
Just to be sure, check that your machine's bios is set up to boot from the cd drive first.

And yes, the .iso you have should work on your computer.

---

### Post by wpshooter on 2009-05-28
> **nategerr said:**
> 10-4. burned with Active ISO Burner and Feinman ISO Recorder not just copied and pasted. My new CD will open and is explorable on my XP machine but will not boot my formatted drive.

Well, then good lord, you do have your CD drive as FIRST boot device in BIOS, don't you ?

---

### Post by nategerr on 2009-05-28
Yup, CD drive is set to boot first. I have no problems starting my computer up from my ASUS cd to get to all my disk utilities and windows XP will happily infest my machine again with it's goodness. Mandriva even half *** works then fails when detecting USB storage devices givingme a "fatal initialization error". I'm sure it's something simple and appreciate you guys giving me a hand here. I've been banging my head against the wall on this

---

### Post by wpshooter on 2009-05-28
> **nategerr said:**
> Yup, CD drive is set to boot first. I have no problems starting my computer up from my ASUS cd to get to all my disk utilities and windows XP will happily infest my machine again with it's goodness. Mandriva even half *** works then fails when detecting USB storage devices givingme a "fatal initialization error". I'm sure it's something simple and appreciate you guys giving me a hand here. I've been banging my head against the wall on this

Then try this.

If you having NOTHING on this machine that you need to keep/preserve, then get [www.killdisk.com](www.killdisk.com) and WIPE the hard drive on that computer completely clean and then after having done so, if it will not boot to those CDs (and the CD drive is not defective), then I will eat my hat !!!

---

### Post by merlinus on 2009-05-28
You might try a reburn at slow speed -- no more than 4x.  Also, can you try it on another machine?

---

### Post by nategerr on 2009-05-29
It ended up being a setting in my bios that enabled me to run the ubuntu cd. After trying the mandriva cd once more I selected fault logger when it froze. turns out a sr0 buffer I/O underrun was causing the problem. Switched out my DVDROM for my DVDburner. Same thing. Went to BIOS and changed drive type from AUTO to CDROM. no dice. Changed to UDMA2.** SUCCESS**!
Hopefully this might save someone else from turning perfectly good cds into coasters and a day of grief.
Thanks a million guys for helping me eliminate all the variables of my problem and getting this machine up and running. I guess wpshooter might not have to eat his hat after all!

---

