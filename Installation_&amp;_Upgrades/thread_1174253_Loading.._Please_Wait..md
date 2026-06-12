---
title: "Loading.. Please Wait."
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by cabaret on 2009-05-30
Downloaded the Ubuntu 9.04 Desktop Edition disc today, burned it (followed the tutorial) and tried to install. 
I get the menu where I can choose 'Install Ubuntu'. I chose that option, since that's pretty much what I want to do. Next screen: black, saying 'Loading.. Please Wait'. I waited. Three hours.

I figured there might be something wrong with my disc. The Ubuntu menu conveniently offers me the option to check the disc for errors. Tried it. 'Loading.. Please Wait'. I didn't bother waiting three hours this time.

I searched the interwebs and these forums but I didn't find a solution to my problem. Hopefully someone here can help me, I'd really like to have it installed.

EDIT: After reading what merlinus posted, I now have two Ubuntu discs. Both from the same .iso, one burned at whatever speed, and another one burned at 4x. The .iso isn't corrupted, according to the md5 hash check. Both discs hang on 'Loading.. Please wait', no matter which option I choose. I've tried 'Run and try', 'Install' and 'Check disc for errors' and they all give me the same result. 
I've installed Ubuntu on another computer without problems in the past, but now I'm losing my faith a bit. I hope someone can help me fix this..

---

### Post by merlinus on 2009-05-30
This may seem obvious, but did you run the cd test?  If so, and there were no errors, your downloaded .iso may be corrupt.  

You can do a checksum to make sure:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If everything still checks out, try burning the .iso at a slow speed (4x or less).

---

### Post by cabaret on 2009-05-30
> **merlinus said:**
> This may seem obvious, but did you run the cd test?  If so, and there were no errors, your downloaded .iso may be corrupt.  

You can do a checksum to make sure:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If everything still checks out, try burning the .iso at a slow speed (4x or less).

It tells me the checksums are the same. 

I guess I'll try burning the iso again at 4x or less then..

---

### Post by cabaret on 2009-05-30
Burned at 4x. Still the same problem: 'Loading.. Please Wait' with a blinking '_' on the next line.

The only difference I see is that the text is in another font. :(

---

### Post by merlinus on 2009-05-30
From the opening cd menu, choose try ubuntu without changing anything, and see if that will run.

Also, you might post system specs.

---

### Post by cabaret on 2009-05-30
This is what the 'My Computer' tab tells me:

Intel(R) Core(TM)2 CPU 
6300 @ 1.86Ghz
1.86 Ghz, 1,00 GB


I'll reboot again now and try that first option. I'll edit this post afterwards.

EDIT: Hangs on 'Loading, Please wait...' aswell.

---

### Post by cabaret on 2009-05-31
Bumpety-bump. Tried with yet another disc, still no progress. :(

EDIT: Tried discs on another computer. 'Run without install' works fine there. Nothing wrong with the discs.. It's my computer. I don't know how to fix this :(

---

### Post by wickedwookie on 2009-06-10
I am having the same trouble. "Loading... Please Wait." without end. I am trying to install the 64bit 9.04 Desktop version. These are my sys specs, maybe it's a compatibily issue?
```

Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz, 3264 MB RAM, SB Live! 24-bit, ATI Radeon HD 4670, Optiarc DVD RW, AsRock P45R2000 Mainboard
```Just before Ubuntu goes into "eternal idle" mode, I noticed a "ValueError: invalid literal for int() with base 10", although I forgot to write down *what* reported that error. Did you notice this error as well, cabaret?

Edit: as per: [http://ubuntuforums.org/showthread.php?t=1136019](http://ubuntuforums.org/showthread.php?t=1136019) maybe we should see if it works w/o ACPI..

---

### Post by wickedwookie on 2009-06-10
> **wickedwookie said:**
> Edit: as per: [http://ubuntuforums.org/showthread.php?t=1136019](http://ubuntuforums.org/showthread.php?t=1136019) maybe we should see if it works w/o ACPI..
This didn't solve the issue for me. Still having the same symptoms. Also checked the CD integrity (just fine)..
Any thoughts?

---

### Post by R33D3M33R on 2009-06-10
See here: [http://ubuntuforums.org/showthread.php?t=185724](http://ubuntuforums.org/showthread.php?t=185724)
or here: [https://answers.launchpad.net/ubuntu/+question/43379](https://answers.launchpad.net/ubuntu/+question/43379)

Maybe it's a DVD drive problem.

---

### Post by dE_logics on 2009-06-10
Try testing the RAM from the BIOS.

I think there should be a bug report for this.

---

### Post by wickedwookie on 2009-06-10
> **dE_logics said:**
> Try testing the RAM from the BIOS.RAM checks run through just fine.. 
The PC is a mere couple of months old and has been working flawlessy on WinXP 64Bit. (I didn't get Ubuntu 8.10 to work with the Radeon 4700 and have been waiting for Ubuntu 9 since then.)

---

