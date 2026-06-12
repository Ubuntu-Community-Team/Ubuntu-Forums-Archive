---
title: "How can I upgrade from Windows 95 to 98 on a laptop?"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by bravofan71 on 2009-01-07
Someone gave me an old laptop with Windows 95.I have a CD Drive for the laptop. My desktop has XP,and I have an A drive for floppy discs. Is there a way that I can download Windows 98 or higher to a floppy,then download it to my laptop? Will I have to clean out the laptop before I install the new software? Or can I just download 98 onto a CD and then download that CD onto my laptop that has windows 95? This is confusing to me. Any help would be appreciated!

I have a wireless adapter that only works on Windows 98 or higher. Someone mentioned something about Linux! I know nothing about that.

---

### Post by Noel96 on 2009-01-07
If I'm understanding you correctly, you should be able to put all your 98 files from floppies onto a single CD and use that to install onto the laptop. They'll need to be in the root directory of the CD and not individual directories. If you have the 98 upgrade, you can install from once you have booted into 95. If your version of 98 is the full install, you will need to boot from the CD.

Ubuntu might work ok, but if it's an older computer, the demands on the processor could be great.

Regards,
Noel

---

### Post by Nevart on 2009-01-07
Well, this is an interesting question, mostly because of where you asked about it.

This forum is intended for Ubuntu users, and Ubuntu is a certain type of Linux (although of course I'm sure Windows users are very welcome). :lol:

Windows is a very different system, and unlike Linux it is definitely not free, so the first thing you should check is that you actually own a copy of Windows 98.  If not, you'd need to buy one.  I don't mean *have* a copy, I mean *own* a copy - the two are not necessarily the same.

Having established that you do in fact have a legal copy of Windows, your next step would be to back up everything on the laptop unless it doesn't matter to you if the existing contents are wiped out. 

You also should know that sometimes things go wrong during an OS install, and it is possible for the hard drive to no longer be bootable if this happens.  You would then need to use a boot repair utility to fix it, and there is no guarantee that this approach would work.

Anyway... the most important thing is: make sure you are aware of the risks and happy to accept them.  In the (somewhat) unlikely event that something does go wrong, you could end up being unable to run either Windows 95 or Windows 98.  :-({|=

Your next step is to discover if you could actually just boot from the Windows98 CD.  If this is possible, you'll avoid all of the more technical steps, and from the wording of your original post, it sounds like you'd be happy to avoid too much messing around at the command prompt. [-o<

If you are able to boot from CD, everything will be very straightforward (apart from the many problems with hardware detection and so on... Windows installs are rarely fun). The setup program will guide you through each step of the process, checking whether you want to do a "clean install" or upgrade your Windows 95 to 98, or dual-boot between them (this means that you can run either one, not really recommended because very few applications will run only in Windows95 but not 98, and you're unlikely to encounter them).    

Then it will do the basic things like checking your time zone and the date, things like that, and will set up the hardware (expect to spend a lot of time hunting for driver CDs, doing downloads, and generally being very stressed out).  When setup finishes the first stage, it will require you to reboot, and then it will begin the second stage which actually takes place inside the newly installed Windows98 system.

The final choice you will have is whether you want to register Windows98 (if you're not given a choice, select Antarctica as your location and it will tell you it is unable to register from there, and there will be no problem!). :-$

Now, if - and this is very likely - your old laptop cannot boot from CD, you don't need to copy the whole Windows98 CD to floppy disks.  Instead, you should be able to make a boot disk via your desktop machine. This disk will allow you to go to the CD drive manually.  I will tell you how to do that in just a moment, but first, we need to get to the boot disk business.

Because it is an awful lot of work (if you don't know what you are doing) to make boot disks manually, you should probably try downloading the files you need from this site...  

[http://www.svrops.com/svrops/dwnlddisk.htm](http://www.svrops.com/svrops/dwnlddisk.htm)

The disk you will need is "Windows 98 boot disk with CD-ROM support (DOS/Win98)".

When you boot the laptop with this disk inserted in the floppy drive, it will boot to a DOS prompt (usually looks like "A:\" with a blinking underscore character where you can type commands).

You would then type something like "d:\setup.exe" without the quotes, and the actual first letter depends on what letter your CD drive is assigned (this is determined by the BIOS).

Then it will all go as described earlier, with you making choices and being told what to do by the setup program.

Or of course, you could just pay an expert to do this for you.  They'll probably charge you something between $20 and $50.  Explain that this is a laptop you got 2nd-hand or you could find yourself in a Garry Glitter type of situation if there's anything on there that should not be! :shock:

If none of the above works, just come on back, but really your best bet is to go to a forum that specifically is aimed at helping Windows98 users.

---

