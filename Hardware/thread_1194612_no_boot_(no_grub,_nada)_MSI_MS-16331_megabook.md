---
title: "no boot (no grub, nada) MSI MS-16331 megabook"
date: 2009-06-22
forum: Hardware
---

### Post by beermotor on 2009-06-22
Ok, so I am borrowing my mother in law's laptop (an MSI megabook MS-16331, amd turion x64), I was hoping to use it to fiddle with and play old games in dosbox, etc.  It had a Xubuntu partition and a Windows partition on it, and worked fine.  But I got tired of xfce, and wanted to put 9.04 on the whole drive, so I booted to an install CD and installed it.

And then it died.  By died, I mean it no longer booted.  At all.  No grub, no nothing.  Just a black screen.  No amount of fiddling within the bios (an AMI bios, I think) seems to do anything - it won't even boot to a windows CD (or any other CD).  Plus there's no option to boot to a usb stick.  Ugh.  

I've googled the heck out of it, surprisingly there are very few links relating to this particular laptop.  Other MSI hardware issues note that there are serious issues with the RaLink wireless chipset apparently, which I do believe is what's in this laptop.  All of the sites I found mentioned doing things within grub, which I cannot do because it doesn't boot to anything at all.

The best I can do is disable all fast boot stuff and whatnot, and it will display a listing of all junk in the post, and pop up a "Press <esc> to boot..." dialog.  Pressing escape does nothing, and letting it time out to 0 does nothing either.  Just black screen.  Fans spin up too, so it seems stuck on something.

So my problem is, I've got a drive that is massively messed up.  Should I yank it out, buy a usb drive thingy and nuke it?  I cannot understand why the thing would stop booting from the CD drive, though.  HELP!
:confused:

---

### Post by terdon on 2009-06-23
Hi, this could be a master boot record (MBR) problem. If you had another boot loader installed (eg windows xp) there may have been problems when you installed grub. Try booting from the cd, then mounting your partitions and having a look if everything is ok.

Then you can try the following:

1) make a tmp dir eg. ```
mkdir tmp
```

2)mount your / partition. (Change /dev/sda1 to the appropriate partition). It may already be mounted in which case skip this step.
```
 sudo mount -t ext3 /dev/sda1 tmp
```
3) set the new directory as root
```
sudo chroot tmp/
```
4) rewrite grub to the MBR
```
sudo grub
```

This may fix your system and at the very least it will not hurt it :)

---

### Post by beermotor on 2009-06-23
That's the problem.  It won't boot from the CD.  At all.  I've tried everything I can think of ... even let it just sit there for 15 minutes, still nothing.  I think my next step is to pull the HD, put it into a external usb dock, and try to wipe it clean... any suggestions on how to do that from a command line?

---

### Post by terdon on 2009-06-23
Oh. OK. Harder than I thought :) It just won't boot into any cd!!?? I assume from your post that you DO have it set to boot from the cd right? ;)

I don't really see how the hard drive could be relevant. This seems like an upstream problem. In any case, you could wipe the drive using mkfs from the command line or dd. 

What happens if you autodetect the hard drives from the BIOS? Can the machine see them there? If it were simply that it cannot find the drives you would get an I/O error not a blank screen.

---

### Post by beermotor on 2009-06-23
> **terdon said:**
> Oh. OK. Harder than I thought :) It just won't boot into any cd!!?? I assume from your post that you DO have it set to boot from the cd right? ;)

I don't really see how the hard drive could be relevant. This seems like an upstream problem. In any case, you could wipe the drive using mkfs from the command line or dd. 

What happens if you autodetect the hard drives from the BIOS? Can the machine see them there? If it were simply that it cannot find the drives you would get an I/O error not a blank screen.


Yeah, it detects the HD in bios, no problem.  And yeah, I have tried disabling the HD in the boot sequence; it still refuses to boot from a CD.  I'm wondering if maybe I somehow corrupted the bios, but no idea how to fix it if it won't boot from any disk.  

I am thinking that there is some bios specific issue with a non-Windows OS being the only thing on the drive, or the thing in the first position.  Maybe.  I dunno.  It could just be that grub failed to install properly, it would not be the first time that I've seen a really wacky error because of grub.  However, this is the first time I've ever seen a machine refuse to boot from CD.:confused:

---

### Post by beermotor on 2009-07-04
MBR musta got screwed up somehow.  I pulled the HDD, stuck it into a 2.5" external USB enclosure, and fiddled/deleted the partitions with Gparted.  That was enough to get the thing to boot from CD, so I reinstalled WinXP on the first half of the drive (under the theory that MSI products required an M$ partition to boot from, I read it somewhere), and got 9.04 on the second half.  Works like a champ now.  Hooray for $10 fixes, versus dead mobos/etc.

---

