---
title: "Can't boot into Ubuntu"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by ploof on 2009-03-08
Sorry if this is obvious.  I've checked 20+ posts on the same topic but haven't found a solution that seems related to whatever issue I'm having.

I've downloaded the latest 32bit ubuntu, run the checksum and burned a few different disks at 1x using imgburn (on windows xp pro) and verifying them.  I can't check the memory of my system or the disc because of the issue I'm having though.

When using the live disc, I get through the language selection and can select any option I want, all of which seem to bring me to the BusyBox.

so then this happens...```
BusyBox v1.10.2 (ubuntu 1:1.10.2-1Ubuntu6)
(initramfs) [    97.184049]ata5.00:exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen

[97.184106]ata5.00:cmd C8/00.08:00:00:00/00:00:00:00:00/e0 tag 0 dma4096 In
[97.184108]     res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
```

Anyways, sorry if that's a lot of pointless text and some of the formatting may be off, but the BusyBox keeps spewing that stuff out endlessly, never getting anywhere.  I tried to install within windows instead, using wubi, and everything works fine until a certain point.  It installs Ubuntu in Windows, restarts, loads up what looks like the ubuntu desktop to finish its business, erases some stuff, and then restarts the computer.  Maybe I'm leaving a step out, but hopefully this makes sense.  After that, in shows the Ubuntu load screen and looks like it has the proper resolution now (smaller load bar) then goes to the BusyBox and ends up saying "cannot find disc, dropping to shell" or something of that sort. Then it just goes through the same process described above.

Anyone know what I can do to fix this? I've installed and used ubuntu on a bunch of computers, but consider myself far from an expert with anything but Windows.  My hardware is old, my bios might need an update, and maybe that has something to do with it.  I'm trying to dual boot with windows XP pro, running on a single hard disk that's 320gb, although there is a second hard disk formatted as NTFS that I use for data.

---

### Post by zvacet on 2009-03-08
> I can't check the memory of my system or the disc because of the issue I'm having though.

Did you try to check memory with live CD?You have memtest option and it will take hours,but at the end you will know if it is memory issue or not.

---

### Post by morficus on 2009-03-08
I'm trying to install Ubutnu 8.10 and I'm getting a very similar error (even when just trying to boot in live mode):

```
[ 204.868106] ata1.00: exception emask 0x0 sact 0x0 serr 0x0 action 0x6 frozen 
[ 204.868223] ata1.00: cmd a0/01:00:00:00:08/00:00:00:00/a0 tag 0 dma 2048 in

[ 204.868234]          cdb 28 00 00 02 90 00 00 00 01 00 00 00 00 00 00
[ 204.868244]          res 40/00:03:00:00:08/00:00:00:00/a0 Emask 0x4 (timeout)
[ 204.868435] ata1.00: status: { DRDY }
```

ata1.00 is my CD-ROM drive, and it's the only drive on that channel. My hard drive is on ata2.00 (again, only drive on that channel too) - both IDE.

I already did a memtest and it came up clean
I also tried burning another 8.10 CD at a lower speed (4x) and nothing has changed.


I've seen many other threads (some from other distros) that talk about this error meaning that the hard drive is going bad. But that can't be the case with me, since it's complaining about the CD-ROM (ata1.00) not the HDD (ata2.00).

I'm downloading 8.04TLS and will try installing that once it's done to see if anything changes.

if anyone has any info on how to solve this, sharing it would be gratefully appreciated :-D

---

### Post by ploof on 2009-03-10
well, managed to do the mem check with the live disc, thanks for that.  It looks like there is an issue:

Pass 0:
```
_Tst_   _Pass_   _Failing address_           _good_      _bad_        _Err-Bits_    _Count_    _Chan_
4       0    00055c91770-1372.0MB      101b5641  111b5641   01000000    1
```

Pass 2:
```
_Tst_   _Pass_   _Failing address_           _good_      _bad_        _Err-Bits_    _Count_    _Chan_
4       2    00055c91770-1372.0MB      84be148e  85be148e   01000000    246
```

I'll wait for a reply and then I guess I'll try to just replace the memory, don't know what type of RAM I'm running right now but it's over 5 years old at this point.  As far as the previous post, I'm fairly sure my issue isn't with old hard disks, these drives are almost new and brand new, respectively.

---

### Post by morficus on 2009-03-11
so I was able to install Ubuntu on my VIA box by booting up the 8.04TLS disk and everything works fine :-)

I'm still not sure why 8.10 refused to work...and I don't dare to update to it since it may break haha - so 8.04 will have to do for now

---

### Post by Kevbert on 2009-03-11
> **ploof said:**
> well, managed to do the mem check with the live disc, thanks for that.  It looks like there is an issue:

Pass 0:
```
_Tst_   _Pass_   _Failing address_           _good_      _bad_        _Err-Bits_    _Count_    _Chan_
4       0    00055c91770-1372.0MB      101b5641  111b5641   01000000    1
```

Pass 2:
```
_Tst_   _Pass_   _Failing address_           _good_      _bad_        _Err-Bits_    _Count_    _Chan_
4       2    00055c91770-1372.0MB      84be148e  85be148e   01000000    246
```

I'll wait for a reply and then I guess I'll try to just replace the memory, don't know what type of RAM I'm running right now but it's over 5 years old at this point.  As far as the previous post, I'm fairly sure my issue isn't with old hard disks, these drives are almost new and brand new, respectively.

It may be that you have a memory seating problem with an intermittant connection. Try removing and then refitting the RAM, Is it dusty inside the computer ? Try carefully using a vacuum cleaner to remove as much dust as possible (especially around the RAM sockets).

---

### Post by OKKARE on 2009-03-11
I think I had a problem similar to this when trying to load that Sabayon Live CD. I again using an external DVD drive (the same one I used to burn the DVD and it worked fine. So if you have another drive you can try it on, give that a shot.

I can't say for sure it's the same error but shouldn't hurt to try this.

---

### Post by salemboot on 2009-03-12
Here are a couple of options:

Live Media:

1.1 Press F6
1.2 At the command line move the cursor just ahead of the dash, --
1.3 type ide=nodma
1.4 Attempt to boot by pressing enter

Reason behind that is libata enables dma by default on the media device (DVD/CD ROM) in 8.10 and possibly 8.04 etc.
This is also good if you are experiences any squashfs errors, a sure indicator of the dma problem. 

Live Media Cont.
2.1  Press F6
2.2  Again just ahead of the dash -- 
2.3  type ide=nodma noacpi noapic irqpoll=off noirqpoll 
2.4  Attempt to boot by pressing enter

I'm not sure about the irqpoll paramater but one of those will be ignored.

I still think Ubuntu among other distributions need to ship with a failsafe kernel.  

Make it work:
Boot to the console with the alternate CD/DVD

That should work, debian's default install is that wizard.  I can't really stand it sometimes coming from a Slackware background but it will allow you to configure encryption and such.

Also I've never manage to get anything but 6.06 to install on one of my old boxes.  2.6.17-2.6.24 are a good series of kernels for old boxes.  Anything after those look out.

---

### Post by asci on 2009-03-12
hi guys, i've got a problem too, so, I installed ubuntu 8.10 but is not working on my notebook <pentium dual-core t2310> it was installed into windows but when i try to boot ubuntu and than the scream frozen, what can i do to solve this bit problem?

thanks so much

---

### Post by ploof on 2009-03-12
Haven't tried Salemboot's ideas yet, will do.  I did "clean" my ram, vacuumed, dust-off'd, and hoped, I also cycled all of the ram through all three slots in my mother board, one stick at a time (they're 1 gig sticks) in every slot to no avail, same errors.  I haven't done a new ramtest, but it seems unnecessary at this point.

I don't think I mentioned that I've tried my best to install Ubuntu 7.4 "Gutsy Gibbon" as well, with errors that looks very similar, but perhaps some of the numbers are different.  I could paste those up and see if it helps as well.

I think for now I'll try Salem's ideas, and then try an older distro + hope.  Like I said, this box is over five years old and I'm not 100% sure of all the hardware's integrity, excepting perhaps the hard drives.

---

### Post by betogf on 2009-03-13
Had very similar errors. I read in some other thread that typing 'all_generic_ide=1' in the command that shows after pressing F6 would help. I decided to try it with 8.10 with no luck. Then I tried 8.04 and seemed to let the live CD do its thing. When I attempted to install it from after the live CD loaded, it kept giving me errno 5 complaining about the exact same I/O errors. After many failed attempts, I decided to install from the initial menu with the 'all_generic_ide=1' option and BAM! Installed and ready to use. I have a Dell PowerEdge sc420. I hope this helps someone. Good Luck!

---

### Post by ploof on 2009-03-14
well, I've tried everything that anyone has suggested so far, in various orders and multiple times, blah blah.

Nothing has worked.  I think I'm gunna try a different distribution...bummer, I like Ubuntu :/

Anyone have a suggestion for something similar? I'm comfortable with gnome and probably wouldn't have a problem with KDE.  Since it seems like I can have either or both on pretty much any distribution, I guess i'm more interested in a good distro for someone who doesn't know much about linux but is willing to learn.  I'm dual booting with XP for my gaming needs, its mostly the nerd in me that has fun with this linux stuff, its fun.

So...something fun?

edit: well, got openSUSE to install, piece of cake! Now I just have to learn how to use it :0

---

### Post by salemboot on 2009-03-24
Glad to hear you got something to finally boot.

---

