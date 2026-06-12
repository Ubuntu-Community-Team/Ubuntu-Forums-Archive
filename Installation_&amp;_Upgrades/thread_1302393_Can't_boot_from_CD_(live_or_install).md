---
title: "Can't boot from CD (live or install)"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by IWYLLPA on 2009-10-27
Hey everyone

I am new to this community, but I'm well acquainted with forums and I know my way around a computer.  I just finished building an AMD Athelon II 620 X4 2.6Ghz Quad-Core based computer that I intend to install Ubuntu on. The motherboard, for what it's worth, is a Biostar TA790XE and I have 4GB (2X2GB)of dual-channel OCZ Reaper DDR2 1066 RAM and a Gigabyte GV-N95TD3-512I GeForce 9500 GT PCI Express 2.0 video card (mobo has no onboard video.)  This info may or may not be useful in troubleshooting, I'm not sure.  I've dabbled with Linux a few times over the last few years, and now I want to give it another try.  Ok, on to my problem itself...

I cannot get my computer to recognize the Ubuntu CD and boot from it.  I've tried the Karmic Koala RC live netbook remix CD and the RC AMD64 install CD with no luck.  I've tried burning at full, 8X, and 4X.  I've tried burning on a Mac using Toast and on a PC using Windows XP using ImageBurn, and no luck.  I have read around about a few posts (over the last few years) of people with similar problems.  Yes, I have set the BIOS to boot from my CD drive.  The drive, for what it's worth, is an HPdcd840i IDE CD/DVD Burner with LightScribe support.  I can put my Windows Vista disc in it (from the install I did on the computer I'm typing on now) and it will boot to it.  I cannot figure out why it will boot to this Vista disc (the Windows Vista Home Premium including SP1 64-bit OEM DVD, for what it's worth) but yet it will not boot to a Karmic Koala RC CD.

I've already tried all the advice I could find in other threads - make sure the BIOS is set to boot from CD/DVD drive first, burn it at a lower speed, and try burning it using different software.  It's also worth noting that my three other computers - a Dell running XP, a Macbook with OS X 10.5, and a custom-built i7 based computer running Vista 64 bit (the one I'm typing on now) - can all see the install CDs and recognize them.  I've even booted from the live CD just fine on my i7 machine.

I figure if nothing else I'll wait until Karmic is officially released and then I'll work on putting it on a USB drive so I can try an install that way if I'm still having no luck with the CD route.  I'll also probably try installing and using a different CD/DVD drive (though the current one can boot a Windows Vista DVD just fine so I don't know why it shouldn't boot a Karmic RC CD.)

Basically, I'd like to get this issue resolved - if not for me, then for the rest of the community.  I'm optimistic that I'll find some way to make this darned thing work, but if this truly is a bug I'd like to get it reported so that future users won't run in to this same problem.  I'm happy to try whatever else you can think of (so long as it's within my ability) to troubleshoot this.

I've heard great things about the Ubuntu community; hopefully some of you can help me out here :)

---

### Post by efflandt on 2009-10-27
Does memtest86+ work (or from separate memtest86+ boot CD)?  Maybe the installation CD makes use of RAM that Windows does not pay attention to.

Years ago I purchased OCZ PC3200 RAM at Frys for my AMD64 3200+ and it appeared to work in WinXP, but I think I had issues in Linux, and memtest86+ revealed occasional errors.  OCZ exchanged it for different model RAM that worked (and has been working fine for years).

It is an HP PC, and dvd+rw-mediainfo /dev/dvd shows its drive as an older HP DVD Writer 300c.  I just installed Ubuntu for the first time last weekend (64-bit v9.04), which I am running on now.

---

### Post by IWYLLPA on 2009-10-27
> **efflandt said:**
> Does memtest86+ work (or from separate memtest86+ boot CD)?  Maybe the installation CD makes use of RAM that Windows does not pay attention to.

Hmm, I must admit, checking the RAM is not something I'd considered.  Unfortunately, I can't boot the Ubuntu CD at all on that computer so I can't get to the memtest.  I also tried downloading memtest86 3.5 and burned it to a CD, but that computer won't boot from it, either.  I just noticed, though, that you mentioned memtest86+, not memtest86, so I'll go try the "+" one and see if that works.

EDIT: I downloaded the memtest86+ v4.00 iso and burned it to CD and the computer won't boot from it, either.  I've also tried to get it onto a USB drive, but I can't seem to boot off of that, either.  It doesn't have a floppy drive, so I can't test that.  Am I missing something with the "[SIZE=2][Pre-Compiled EXE file for USB Key (Pure DOS)]("http://www.memtest.org/download/4.00/memtest86+-4.00.exe.zip")" option?  All I get is an .exe - I try running it in Vista 64 and it errors saying it's not 64 bit, I try it on XP and it just opens a DOS window then closes it again.  I copy that .exe onto a USB drive but the computer won't boot from it (it does acknowledge the USB drive and it brings up a line about removing it then restarting.)  I tried the  "[/SIZE][SIZE=2][Pre-Compiled package for Floppy (DOS - Win)]("http://www.memtest.org/download/4.00/memtest86+-4.00.floppy.zip")" and I can launch it just fine on XP but it errors out since there's no floppy drive - I want it to install on the USB drive instead.  I'm hoping for some USB drive options since I am having no luck at all with the CD/DVD drive.

EDIT: OK, so I'm still not sure about booting to a USB drive - I've seen some posts that say I should format it FAT (instead of FAT32) o I tried that but still no luck with memtest86+ (it still won't boot it off the USB drive.)  However, I did finally get memtest86+ to work!  Apparently it's built in to my motherboard - in the BIOS there was an option to enable a memory test and when I did and restarted it went in to memtest86+ 2.11 (same version as when I used the ubuntu Karmic RC live CD on a different computer) so yeah, I managed to do a memory test!  The timing for my RAM isn't quite right - it's DDR2 1066 so I'll need to clock it up sometime but nevertheless I ran a full memtest86+ test on it and it passed.

In short, the memory does not seem to be the problem.
[/SIZE]

---

### Post by IWYLLPA on 2009-10-27
Hmm...a bit more testing and a bit more data - the plot thickens :P  Since I've tried a Vista install DVD and it worked fine, I figured I'd try an XP install CD and see if it worked, too.  I put it in and no luck.  However, when I take that same CD (that came with a Dell PC several years ago) and put it in a different computer, it boots to it without any problems.  Also, I downloaded the 9.04 i386 install CD and burned it to a CD (at 4X speed using ImageBurn on Windows XP) and this AMD computer still won't boot from it.  However, I put that same 9.04 CD into a different computer and it boots to it without any problems.  I ran the 'check disk for errors' thing and it successfully completed without detecting any errors.  Just to be sure it was working, I even used that 9.04 CD to do memtest on that other computer and it did so without any problems.

To make matters worse, I figured I'd double check the Vista install DVD and now the AMD machine won't boot to it, either (even though it did once.)  On the plus side, it seems that this isn't a bug but rather some sort of problem with my hardware.  Bad news is I'm really not sure what the heck is going on.  I think I'll try to scavenge a DVD drive from another computer and put it in this AMD machine and see if that works.

EDIT: Alright! Finally got it to boot! I swapped out an old IDE DVD drive from a computer that is sort of scrapped at the moment and I finally got this AMD machine to boot from the CD!  The first time I turned it on and gave it a try (after swapping DVD drives) it still gave me the same errors.  I went in to the BIOS and reset the IDE for the CD/DVD drive to "Auto" instead of "CD/DVD" and then I had to go back to the boot order and set this new CD/DVD drive as the first boot priority.  Now I just booted up 9.10 in live mode and it works!

This still leaves me with a few questions:
1) How did it manage to boot from a Vista DVD once and then somehow it no longer could?  Is the drive just going bad?  Perhaps I'll try and test out the drive later, once I get Ubuntu fully installed and stable.
2) How do you install things (like memtest86+ or even an Ubuntu install) to a USB drive and make it bootable?  I've heard about an old HP utility that lets you format USB drives as bootable (similar to how you'd format a floppy disk as bootable.)  Hmm, something to puzzle another day.

Oh well, at least it works now :)  If anyone has a similar problem, please post here and let me (and the rest of the community) know.

---

### Post by cwsnyder on 2009-10-28
1)You may have gotten lucky.  If you had tried to complete an install, it probably would have choked somewhere in the process.
2) Look for [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

