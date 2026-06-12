---
title: "Ubuntu ISOs are corrupt!?"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by themusicalduck on 2009-05-22
I've been trying to do a clean install of 9.04, but it seems like every ISO I try to burn is corrupt. I've downloaded three ISOs from different mirrors and each one has failed to burn to a disc, except for one, which I first burnt from my current Ubuntu install (which is now inaccessible).

The one which did work, wouldn't install because of an error at about 88%. I managed to make a USB live disc from the ISO, but that also gives an error at 88%. Although I can see that the files have copied over to the drive from the attempted installs, grub hasn't been installed so I cannot boot into it. (super grub disk doesn't help, gives an error 15, trying to install it manually says that it can't find stage1)

I tried the alternative disc as well, with the same result. Two downloads were from UK mirrors and one from a Belgian mirror. I don't think it's my burning hardware, because I have two which both gave same result, and the USB drive failing to work suggests it isn't that.

Something very weird is going on, and now I only have a live USB disc to use for an OS.

---

### Post by taurus on 2009-05-22
Use torrent to download it.  Then, burn it at a slow speed, not at the default speed.

---

### Post by themusicalduck on 2009-05-22
Unfortunately I can't use a torrent because they are blocked on my network. I did burn them at a low speed, and besides it still wouldn't explain why the flash drive would have the same problem.

Is there another way to install grub from a live CD? Then I may be able to attempt to boot into what has been installed.

If I do it the normal way, after command:

find /boot/grub/stage1

I get:

Error 15: File not found.

---

### Post by taurus on 2009-05-22
Did you run the checksum to check the integrity of the ISO image first before you burnt it?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=(burn)|(iso](https://help.ubuntu.com/community/BurningIsoHowto?highlight=(burn)|(iso))

---

### Post by themusicalduck on 2009-05-22
MD5 seems to be fine. I should probably add that the error happens after the CD has been burnt. It says 'Creating image checksum' and then fails saying that the CD may be corrupt.

---

### Post by taurus on 2009-05-22
Is it a CD-R or a CD-RW?

---

### Post by 0per4t0r on 2009-05-22
Okay, musicalduck, what country do you live in, and what general area of that country. Also, if all else fails, just order a free CD.

EDIT:
also, after examining your post, I have determined that I should also advise you to try a different CD. Or, erase the current CD in use first, and then burn the ISO.

---

### Post by themusicalduck on 2009-05-22
I've actually tried around 5 CDs now, both CDRs and DVDRs.

I tried again to burn another and this time it worked, I'm trying to install it now to see if ubiquity can complete it and get past 88%.

I live in south-west of England.

---

### Post by 0per4t0r on 2009-05-22
Yeah, I live in Michigan in the U.S., and the MIT Media Lab mirror works great for me.

---

### Post by themusicalduck on 2009-05-22
Well ubiquity crashed again at 88%. Looking at the report the title says 'ubiquity crashed with the InstallStepError in cofigure_ma()'

It doesn't look like I can save the report as a text file so it's difficult to post the whole thing.

I'll have a go with the MIT mirror, but probably won't try again tonight. I'll try it tomorrow and post afterwards.

Thanks for the help so far.

---

### Post by 73ckn797 on 2009-05-22
Did you run the disk self test option when the LiveCD menu comes up?

---

### Post by 0per4t0r on 2009-05-22
> **themusicalduck said:**
> 
I'll have a go with the MIT mirror, but probably won't try again tonight. I'll try it tomorrow and post afterwards.

Thanks for the help so far.

Whoah, hold your horses! You're supposed to use the mirror nearest you. With that MIT mirror, it could take hours for you, and maybe 25 minutes for me! Try to find one that fits your location. Also, what software are you using to burn the ISOs?

---

### Post by sevenones12 on 2009-05-22
> **themusicalduck said:**
> MD5 seems to be fine. I should probably add that the error happens after the CD has been burnt. It says 'Creating image checksum' and then fails saying that the CD may be corrupt.

I am having the same problem as you right now. It downloaded fine, and the first part of the image burns the way it should, but then when writing checksum with usually about 2 minutes left, it just freezes. 

I also have an unrelated question. And excuse my probable newbness. I just installed Ubuntu 9.04 off of Wubi to try it out after my friend suggested it. In one gay I realized I want to partition my discs and run ubuntu without having to go through a windows file. Is downloading the .ISO and reinstalling Ubuntu the easiest way to do this. Or sence I'm already running 9.04, can I change it around so it runs as a true dual-boot?

Thanks, and sorry if these are dumb questions.

---

### Post by 73ckn797 on 2009-05-22
> **sevenones12 said:**
> I am having the same problem as you right now. It downloaded fine, and the first part of the image burns the way it should, but then when writing checksum with usually about 2 minutes left, it just freezes. 

I also have an unrelated question. And excuse my probable newbness. I just installed Ubuntu 9.04 off of Wubi to try it out after my friend suggested it. In one gay I realized I want to partition my discs and run ubuntu without having to go through a windows file. Is downloading the .ISO and reinstalling Ubuntu the easiest way to do this. Or sence I'm already running 9.04, can I change it around so it runs as a true dual-boot?

Thanks, and sorry if these are dumb questions.


Uninstall the WUBI deal then just install Ubuntu. It will create a dual boot menu as part of the installation process.

---

### Post by sevenones12 on 2009-05-22
So basically, I do need that CD to finish writing?

---

### Post by 73ckn797 on 2009-05-22
> **sevenones12 said:**
> So basically, I do need that CD to finish writing?

You will need a good LiveCD to do the install.

---

### Post by sevenones12 on 2009-05-22
So now we're back to the original problem, with no solutions except waiting for a CD to be delivered.

---

### Post by themusicalduck on 2009-05-23
I managed to get the install to work using an alternative CD and everything went pretty much perfectly then.

I'd like to restore my packages from an APTonCD iso I made if that's possible. What's the best way to restore everything from it? Ideally I'd just like to install everything and have my system back to how it was rather than use it as an extra repository.

---

