---
title: "Help installing on super old desktop. SCSI or PCMCIA..."
date: 2015-12-02
forum: Hardware
---

### Post by Salty-san on 2015-12-02
So this old desktop I am making for someone is so old it has a Floppy Drive <,<...But also 2 USB ports so maybe it was just being a thorough release, lol. It seems to be circa 2005. Tried to install light weight ones, but the problem is they all fail before even booting giving various errors or just unpacking and then showing nothing. Porteus finally gave a message letting me know that "Porteus data not found. You are maybe using an unsupported boot device (eg SCSI or old PCMCIA)."...Tried reading the PCMICIA howto on Linux and it's just too convoluted for me, so I am hoping for a more hands on approach.

Anyone know some small Linux distro I could try and maybe how to configure it or make the live enviroment? I am doing this more so for curiosity and an experiment at this point. A sort of blast to the past.

The only thing I managed to boot into is a Hiren's Recovery Tool, on its Mini XP and sort of try some stuff there but I got various errors and on the Parted Magic Linux enviroment which I had to do as Low RAM spec too because it told me it only had 189 RAM of space available. ;/...used it to format as NTFS.

I tried the super light weight Slitaz, and it boots, shows the options, just like Porteus, then unpacks and for a bit I see a very tiny arrow cursor then nothing.

Slax unpacks but then does the same thing too as far as I remember.

Lubuntu or LXLE give Kernel failures before even showing the live boot options menu.

I know there are plenty of other small ones out there and I figure one is bound to work but posting this for some extra help as I try it. I did them with Rufus mostly and no permanence but I got UNetbootin too. Would appreciate it if you all see this as some sort of a lolzy challenge to get something super old to work, and hope it can be fun for everyone. ;p

---

### Post by tgalati4 on 2015-12-03
Motherboards from the 2004 to 2006 era often have bad capacitors.  Inspect the motherboard carefully for bulging or leaking capacitors.  It's also possible that the power supply is bad--can't provide enough current to get a full boot.  Have you seen this desktop boot fully in Windows?  Ever?

---

### Post by oldfred on 2015-12-03
Some info on old hardware. But at some point it becomes not worth the effort.

 Older hardware suggestions - mörgæs
[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by Salty-san on 2015-12-03
> **tgalati4 said:**
> Motherboards from the 2004 to 2006 era often have bad capacitors.  Inspect the motherboard carefully for bulging or leaking capacitors.  It's also possible that the power supply is bad--can't provide enough current to get a full boot.  Have you seen this desktop boot fully in Windows?  Ever?

Yeah I haven't seen it boot into Windows myself. Came with 2 bad Windows installs on it neither of which worked because of some disk not seen issue, and I formatted it later. Also heard from the guy that he had problems about Windows but wasn't clear what, I think just the installation. So you are right, it could be some hardware problem. It can not boot from the CD drive either, tried it with a Win XP disk, just stops after it said to press the key. But the thing is I did some Linuxes on the USB as Disk images too but nothing showed on boot, so what does that say?

Because from USB I did see it boot into a few things. Mini XP on the Hiren kit, its Parted Magic enviroment (couldn't load graphics so had to do low RAM) and I also tried to do some UBSs with free XP downloads and such and it managed to load into Bart PE Windows XP.  But my Windows attempts failed, they are just really old and weird to use with USBs, I must have not done something right.

Tried to go for low spec linuxes, got Tiny Core Plus, which is like the smallest, and it loads up to a point then it tells me it could not load certain things, sostill no boot. I could give the lines if you think it might help...


> oldfred	 [INDENT]Re: Help installing on super old desktop. SCSI or PCMCIA...
						Some info on old hardware. But at some point it becomes not worth the effort.

 Older hardware suggestions - mörgæs
[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640) [/INDENT]


Thanks will read and try it, althought Lubuntu still feels high spec to me. I was actually thinking of trying Puppy Linux because its damn small and if it won't work then nothing will but I don't get what's up with the .pet downloads on the distro, any help on that? 

Also the computer only has 1 hard drive of about 40 GB, and I formatted it as NTFs and set as boot. Maybe I can work something out with format types and maybe some swap space for linux?

I am doing this just for curiosity and for funny value of still having a floppy comp, but I am ready to drop it at any point and toss the comp somewhere if need be. I am also in no particular rush so I will at least continue until I figure out for good actual evidence that it is broken.

---

### Post by tgalati4 on 2015-12-03
If you can't boot Damn Small Linux, then your system is toast.  That can run on x486 machines, definitely old school.  The initial boot you are seeing is actually the bootstrap or mini-linux that loads into RAM and then loads the full kernel--the initial RAM disk (initrd) and then the kernel, which will start to enumerate your hardware.  If it can't get past the bootloader, then perhaps it is a RAM problem.  If your CPU is bad, then the bootloader will not load and you get no display, except error beep codes.  Did you thoroughly clean the motherboard and reseat the RAM sticks?

---

### Post by Mike_Walsh on 2015-12-04
> **Salty-san said:**
> Thanks will read and try it, althought Lubuntu still feels high spec to me. I was actually thinking of trying Puppy Linux because its damn small and if it won't work then nothing will but I don't get what's up with the .pet downloads on the distro, any help on that?

.pet:-

Some people used to refer to this as 'Puppy's Extra Treats'. In fact, it stands for Puppy Extended Tarball. But I agree with tGalati:- If you can't boot DSL, then you may have some kind of hardware problem.  

Even so, my own Compaq desktop is 2005. My HDD is 500 GB; even the original was 160 GB. My USB's are all 2.0's, not 1.1's.....and I have 13 of them. And I believe floppy drives were still being fitted by some manufacturers, upon request, as late as 2009.

I rather think you might have a problem with Puppy, even. I suspect your major problem is either bad RAM.....or a serious lack of it. As in, you need some more.

Either that.....or you've got a dodgy PSU..


Mike. ;)

---

### Post by Salty-san on 2015-12-04
> **tgalati4 said:**
> If you can't boot Damn Small Linux, then your system is toast.  That can run on x486 machines, definitely old school.?

Oh, lol, I actually meant Linuxes that are pretty small, not the one named that way, but thanks for reminding me. Will try that one too.


> [ The initial boot you are seeing is actually the bootstrap or mini-linux that loads into RAM and then loads the full kernel--the initial RAM disk (initrd) and then the kernel, which will start to enumerate your hardware.  If it can't get past the bootloader, then perhaps it is a RAM problem.

Yeah various ones give some Kernel Panic thing. It's more than just the botloader, there is unpacking and such for some stuff, but then right when it was supposed to boot into it something happens.

> If your CPU is bad, then the bootloader will not load and you get no display, except error beep codes.  Did you thoroughly clean the motherboard and reseat the RAM sticks?

Uuhh, I didnt open it up and fiddle inside it no. How should I reset RAM and sticks then? 

Also, any idea what to do with these .pet files from Puppy?

---

### Post by Mike_Walsh on 2015-12-04
Hi, Salty-san.

> **Salty-san said:**
> Also, any idea what to do with these .pet files from Puppy?

Quite simple, actually.

What do you do with a .deb file (Debian/Ubuntu)?

What do you do with a .rpm file (Red Hat)?

What do you do with a tar.gz file (Slackware)?

You download it. And then, to install it, you click on it.....

A Puppy .pet file is no different. Inside it, the binary source code is identical to that in files for the same package from the other distributions.  Each distribution, however, packages files in such a way that they work best with, and are recognised by, its own package management system.

Puppies are considered quite odd by many. For a start, they run as /root all the time (Shock; Horror... :lol:) There **are** Puppies in which you can install **any type** of package....and yet they all play happily together!

However, as I said, I think your problem is one of two things. Either your RAM needs re-seating.....or you just don't have enough **of** it.

As you will doubtless soon be told, Puppy is not supported in any of the various sub-forums here. Why not come and look us up at the Puppy Forums? We can soon help you out.....more easily than **I** can **here**.

[http://www.murga-linux.com/puppy/index.php](http://www.murga-linux.com/puppy/index.php)


Regards,

Mike. ;)

---

### Post by Salty-san on 2015-12-04
> As you will doubtless soon be told, Puppy is not supported in any of the various sub-forums here. Why not come and look us up at the Puppy Forums? We can soon help you out.....more easily than **I** can **here**.

I was going to get on those forums actually because I want to use Puppy for many things. But I meant...I am on Windows on some other machine now. How do I make a bootable USB with Puppy since those files are .pet? So that I can then try to boot into it from there.

Anyway, UPDATE!: tried Damn Small Linux, it booted, but it did give some error while Kernel loaded. Once in DSL I didnt have much to do, couldn't even find the install function. But I also couldn't mount my only Hard Disk so that is something. What does this mean?

I also registered the TinyCore error it gave after Kernel loaded, if it means anything to anyone:

```
tcobox:~$

udevadm settle-timeout of 5 seconds reached, the event queue contains:

 /sys/devices/pci0000:00/0000:00:10.4/usb1 (970)

 /sys/devices/pci0000:00/0000:00:10.4/usb1/1-0:1.0 (971)


tcobox:~$

```

So since I now know some Linuxes seem to boot...anyone have any other suggestions of super small Linuxes besides DSL, Slitaz, Porteus, Slax, Lubuntu? I hear Debian is very good for old machines also.

---

### Post by tgalati4 on 2015-12-04
Looks like a bad or shorted USB port.  Check for dirt in the ports.  To reseat the RAM,  gently take out the RAM, blow out the dust, move them around to different slots, then re-insert.  Watch some Youtube videos for how to do it.

---

### Post by Mike_Walsh on 2015-12-04
Hi, Salty-san.

This page might explain a few things. Don't worry about the date; Puppy's mode of operation hasn't essentially changed since it was first created, over 11 years ago! Which just goes to show how avant-garde it **was** at the time.....

[http://www.puppylinux.com/flash-puppy.htm](http://www.puppylinux.com/flash-puppy.htm)

Hope that helps.


Regards,

Mike. ;)

---

