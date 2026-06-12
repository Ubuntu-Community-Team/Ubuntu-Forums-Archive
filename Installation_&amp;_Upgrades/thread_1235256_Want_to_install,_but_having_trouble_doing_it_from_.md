---
title: "Want to install, but having trouble doing it from CD"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by absolve on 2009-08-08
Hey all.  First time poster here :-)  

I've always used a Fedora or Red Hat flavor of Linux in the past.  I recently decided that I'd had enough of Windows and was going back to Linux for good, so I installed Fedora Core 11 on a separate drive.  Strange thing, though.  The DVD image that I burned would boot up just fine and would bring up the installation intro/options page just fine, but when it came time to actually perform the install I would get an error message that the disc image was not on the media.  Now, obviously it was.  And I checked and checked and re-checked the md5sum of the image/disc.  Anyway, long story short I was finally able to pull off the install by extracting the files from the disc image to the root of my C:\ drive in Windows Vista.  I was installing Fedora to a separate physical drive.  I was able to use the DVD to boot and then selected to install from Network, selected the hard drive that contained Windows as the location for the installation image, and VOILA!  I still don't understand it, but anyway it worked.  

So I've been using Fedora (again) for about 3 weeks now and I've become a little disenchanted with it.  Some things are just too difficult to pull off.  Just so I can keep this as short as possible, I'll skip to the point -- **I want to install Ubuntu now.  I want to install it on a different physical drive from Fedora (I'm just going to overwrite the Windows installation)**.

But it's like the same thing is happening with Ubuntu now.  I've downloaded the CD image and checked the md5sum.  Burned it to CD.  Booted from CD.  Boots up fine.  But when I selected "install," it gives me a drive I/O error and my only option at that point is to reboot.  The menu doesn't seem to have an option to install via a Network so I don't know what to do.  

I'm wondering if I can run the installation somehow from **within** Fedora, and just point to the other drive as the installation destination.  I guess that sounds far-fetched, but I'm sort of stumbling along here.  It's like my CD/DVD drive will boot but will then stop spinning and not be accessible.  

Any ideas on how I can either: 

a)  fix the CD problem, or
b)  install Ubuntu in a creative way?  

I'm anxious to get started and give Ubuntu a try, so all help is appreciated!  

Thanks so much, 

-abs

---

### Post by stlsaint on 2009-08-08
desktop or laptop? external drive or internal drive? what ubuntu version and where did you get the image from? just getting the primary info out the way!!

---

### Post by Greg Xix on 2009-08-09
*This is the same post I issued on another Thread:*


I personally have a Live USB installed on an old 1GB USB Flash disk. I used to sometimes get weird errors when installing from CD-RW's myself.

Not sure if you know how to make a Live USB:

1. download the 9.04 ISO file to Desktop

2. Use the GParted/Partition Editor tool to "format" the Flash disk. DO NOT Format it with a filesystem i.e. Fat32 or Fat16. Just leave it "Unallocated". I ran into problems when I did it that way. Let the ISO format/burn it how it wants to.

3. Goto System > Administration > USB Startup Disk Creator and mount/burn the ISO to the USB Flash disk

4. Of course then set your BIOS Boot Sequence to load from the USB Drive first, and hopefully it will install from there



This way has always worked like a charm for me. And it takes only about 15 mins to go from "Zero to fresh Ubuntu Install" on the Hard Drive, which is a lot faster than even when the CD installs actually did work.

If this doesnt work I'd request an officially burned CD from Ubuntu directly, somebody today told me they are Free coincidentally, but take about 3 weeks to arrive in the mail. But you get a cool looking CD and some stickers.

---

### Post by absolve on 2009-08-09
> **stlsaint said:**
> desktop or laptop? external drive or internal drive? what ubuntu version and where did you get the image from? just getting the primary info out the way!!
This is a desktop PC with an internal DVD/CD drive.  It's the latest version of Ubuntu which I downloaded from the Ubuntu website -- 9.04 for AMD64.

---

### Post by zkriesse on 2009-08-09
Is there a different pc that you can use? I once had the same issue and I fixed it by downloading the version of Ubuntu on an Ubuntu machine.

---

### Post by phillw on 2009-08-09
A common problem occurs when you burn the CD - use 4X, or even 1X to burn the image.
(4X seems to be most commonly recommended).

For whatever reason, many people report grief when burning at high speed (the default for most burners).

Regards,

Phill.

---

### Post by absolve on 2009-08-10
I don't have a very good feeling about the slow burning thing, but I'm willing to give it a try.  

What should I use for burning.  All I have installed in Fedora is Brasero, and I can't find a way to make it burn an image any slower than 8X.

The USB method sounds more complicated, but I'll try that next if a new CD doesn't work.

---

### Post by absolve on 2009-08-11
Well whaddaya know!  Burning a new CD w/Brasero at 8x did the trick.  I might have mentioned that the previous copy I was using was a CD-RW.  This one was a permanent burn.  

Anyway, thanks!  Plenty of exploring to do!  

-abs

---

