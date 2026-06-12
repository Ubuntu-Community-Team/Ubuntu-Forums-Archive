---
title: "Installing Ubunutu 9.04 on an external HDD from scratch"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by Lawand on 2009-08-20
I searched the forums but haven't found a guide or tutorial about this...

---

### Post by Bartender on 2009-08-20
Well, I'll tell you what I did.  This probably isn't the most elegant solution but it works.  

I did this on a laptop, which is considered more difficult to work on than a desktop.  I don't agree with that necessarily; it only takes about five minutes to swap drives in the laptop.

I installed Ubuntu to a HDD (we'll call it HDD #1) while it was inside the laptop.  Then I removed HDD #1 and put HDD #2 in its place.  (HDD #2 has Ubuntu installed)  HDD #1 gets plugged into a NextStar HDD dock.  Unlike an external HDD enclosure, there isn't any "installation" involved - you just drop the HDD into the dock's slot.

Then I went into the laptop's BIOS and re-ordered the boot priority.  I told it to boot from USB first, then HDD.  

If I have the dock plugged into a USB port on the laptop and it's spinning HDD #1, the laptop boots from the external device and it acts just like it would if HDD #1 was inside the laptop.  A little slower of course :)  

I just have to remember to power up the dock before starting the laptop.

If I don't want to boot from USB, then I leave the dock turned off or unplugged.  The BIOS takes a quick look for bootable USB devices when starting up, then moves on to HDD #2.

It's really quite simple and works well.  Of course, I can go either way with this - pull HDD #2 out of the laptop, put HDD #1 back in, and put HDD #2 in the dock.

One interesting note - HDD #1 is the laptop's original HDD.  The laptop came with Vista.  I set HDD #1 up as a dual-boot.  While Ubuntu is happy to run from the USB dock, guess what Vista does?  That's right - it refuses to run.

---

### Post by Lawand on 2009-08-20
My external HDD isn't in an external HDD box (or adapter), rather it is closed and I can't open it and it's not a laptop HDD...

---

### Post by Bartender on 2009-08-20
What kind of external enclosure is it?

As far as the "not a laptop" part, accessing the insides of a desktop is usually easier than a lappy...

---

### Post by Lawand on 2009-08-20
[This]("http://www.mwave.com.au/newAU/mwaveAU/productdetail.asp?SKU=22100153") is the HDD I am talking about, I don't think I can open it and put it in the laptop...

---

### Post by Bartender on 2009-08-20
OK, I'm just going to wing this off the top of my pointy little head - so if it doesn't come out quite like I describe please don't be mad.

We can always do this the old-fashioned way.  
We'd need an Ubuntu installer CD that you are confident is working.  It hasn't been burned at 32X, it's not a CD-RW, it's not some cheap generic media -

Plug in the external.  Power it up.  Make sure your PC's BIOS is set to boot from the optical drive, pop the installer CD in the drive, restart the PC.

The Ubuntu installer CD should do its thing.  At the first screen, click on "Use Ubuntu without making any changes" or whatever the latest version says...it'll be something similar to that.

When you get to the desktop, go to System>Administration>Partition Editor and click on it.  You'll get a map of your PC's main HDD.  It should be identified as "sda".  Up in the right-hand corner there's a box that lists identified HDD's.  Click on that box and see what other drives the partitioner identifies.  It should see the external, identified as - well, I can't say for sure what yours will be identified as, but I'm running this little exercise on a Linux PC as I'm typing this, and the external is identified as "sdb".  If in doubt, you can tell by the size.

Write down the name it gave you - let's assume "sdb" - and get out of the Partition Editor.  Go back to the desktop, click on "Install", go thru the first five steps of the installer, when you get to the partitioner, make _absolutely sure_ that you navigate to "sdb" before you start installing or changing partitions.

At this point, I am not absolutely 100% for sure what to tell you is the best advice, but if it were me I'd install Ubuntu entirely to the external.  That means at the last step of the installation you click on the little "Advanced" button and install GRUB to "hd1".  This part is a little tricky because GRUB identifies the devices differently than Ubuntu.  For example, if your first HDD is sda in Ubuntu, it'll be hd0 in GRUB.

If the external was identified as sdb in the partitioner, then GRUB will see it as hd1.  If the labels I supplied are correct, you must make sure that GRUB installs to hd1 in that "Advanced" window.

If you have questions about your external and GRUB, come back to the forum with the name that the partitioner gave to the external device.

There's a concept going on here that trips up almost everyone at first.  GRUB's default setting is to install a small bit of itself to the first HDD.  That small bit of code points the PC to the second part of the bootloader.  If you let GRUB install in the default mode, the PC will not boot up without the external plugged in and spinning because GRUB can't find its way.  If you tell GRUB to install itself entirely to the external, then the PC can start up without the external plugged in because GRUB did not tweak the PC's HDD.

The above is true whether it's Windows or Linux on the main HDD.

if you install entirely to the second HDD, then you would still want to tweak the BIOS to boot from USB, and start the PC with the external plugged in and spinning, as described earlier.

I'm not at all sure this is the best or only way to do what you want, but it's one way...

[SIZE="4"]**HOLD THE PHONE **[/SIZE]

You know what, there's another way to do this that would be much safer!!  Pop the Ubuntu installer CD in the tray after you've set BIOS to boot from the optical drive, and shut down the PC instead of restarting.  Open up the PC and unplug the power cable from the internal HDD.  Restart the PC.  That way, when you get to the LiveCD desktop and go into the partitioner, you'll know that you're installing to the external HDD, not the internal.  The biggest benefit to doing it this way - if there is only one HDD involved, GRUB will automatically install to that HDD without you having to go into "Advanced".  I was nervous about trying to describe that part to you.  Unplugging the internal HDD or HDD's would allow us to detour around the scariest part.

EDIT:  You posted the link as I was writing this.  My so-called plan depends on having the USB external spinning and available very early in the process of starting up the PC.  My external HDD has an external power source so it's up and running before the laptop starts.  BIOS sees the device and boots from it.  All you can do is try it and see what happens although I'm not very optimistic.

---

### Post by Lawand on 2009-08-21
[QUOTE=Bartender]Open up the PC and unplug the power cable from the internal HDD.  Restart the PC.  That way, when you get to the LiveCD desktop and go into the partitioner, you'll know that you're installing to the external HDD, not the internal.[/QUOTE]
Interesting!, I'll try it and get back to you :)

---

### Post by russu52 on 2009-08-21
i agree with bartender's idea. i also wish to have ubuntu running on an external hdd without installing anything on my netbook. as external hdd i have a 320 gb ide in an enclosure which connects via usb, with an external power supply. i was planning to open up my desktop, connect this hdd (via ide) and install ubuntu on it as if it is the pc's main hdd. then i remove and plug it as usb to my netbook and boot from it. i just hope it works. if it does, i will post here.:P

---

### Post by FrankDeGroot on 2009-08-21
I got redirected here by russu52 (thanks!) from a similar post. I guess I was looking for this:

> If you tell GRUB to install itself entirely to the external, then the PC can start up without the external plugged in because GRUB did not tweak the PC's HDD.

Being used to Windows this is a pleasant surprise! I think I'll give it a try with my wife's laptop now.

---

### Post by presence1960 on 2009-08-21
> **Bartender said:**
> OK, I'm just going to wing this off the top of my pointy little head - so if it doesn't come out quite like I describe please don't be mad.

We can always do this the old-fashioned way.  
We'd need an Ubuntu installer CD that you are confident is working.  It hasn't been burned at 32X, it's not a CD-RW, it's not some cheap generic media -

Plug in the external.  Power it up.  Make sure your PC's BIOS is set to boot from the optical drive, pop the installer CD in the drive, restart the PC.

The Ubuntu installer CD should do its thing.  At the first screen, click on "Use Ubuntu without making any changes" or whatever the latest version says...it'll be something similar to that.

When you get to the desktop, go to System>Administration>Partition Editor and click on it.  You'll get a map of your PC's main HDD.  It should be identified as "sda".  Up in the right-hand corner there's a box that lists identified HDD's.  Click on that box and see what other drives the partitioner identifies.  It should see the external, identified as - well, I can't say for sure what yours will be identified as, but I'm running this little exercise on a Linux PC as I'm typing this, and the external is identified as "sdb".  If in doubt, you can tell by the size.

Write down the name it gave you - let's assume "sdb" - and get out of the Partition Editor.  Go back to the desktop, click on "Install", go thru the first five steps of the installer, when you get to the partitioner, make _absolutely sure_ that you navigate to "sdb" before you start installing or changing partitions.

At this point, I am not absolutely 100% for sure what to tell you is the best advice, but if it were me I'd install Ubuntu entirely to the external.  That means at the last step of the installation you click on the little "Advanced" button and install GRUB to "hd1".  This part is a little tricky because GRUB identifies the devices differently than Ubuntu.  For example, if your first HDD is sda in Ubuntu, it'll be hd0 in GRUB.

If the external was identified as sdb in the partitioner, then GRUB will see it as hd1.  If the labels I supplied are correct, you must make sure that GRUB installs to hd1 in that "Advanced" window.

If you have questions about your external and GRUB, come back to the forum with the name that the partitioner gave to the external device.

There's a concept going on here that trips up almost everyone at first.  GRUB's default setting is to install a small bit of itself to the first HDD.  That small bit of code points the PC to the second part of the bootloader.  If you let GRUB install in the default mode, the PC will not boot up without the external plugged in and spinning because GRUB can't find its way.  If you tell GRUB to install itself entirely to the external, then the PC can start up without the external plugged in because GRUB did not tweak the PC's HDD.

The above is true whether it's Windows or Linux on the main HDD.

if you install entirely to the second HDD, then you would still want to tweak the BIOS to boot from USB, and start the PC with the external plugged in and spinning, as described earlier.

I'm not at all sure this is the best or only way to do what you want, but it's one way...

[SIZE="4"]**HOLD THE PHONE **[/SIZE]

You know what, there's another way to do this that would be much safer!!  Pop the Ubuntu installer CD in the tray after you've set BIOS to boot from the optical drive, and shut down the PC instead of restarting.  Open up the PC and unplug the power cable from the internal HDD.  Restart the PC.  That way, when you get to the LiveCD desktop and go into the partitioner, you'll know that you're installing to the external HDD, not the internal.  The biggest benefit to doing it this way - if there is only one HDD involved, GRUB will automatically install to that HDD without you having to go into "Advanced".  I was nervous about trying to describe that part to you.  Unplugging the internal HDD or HDD's would allow us to detour around the scariest part.

EDIT:  You posted the link as I was writing this.  My so-called plan depends on having the USB external spinning and available very early in the process of starting up the PC.  My external HDD has an external power source so it's up and running before the laptop starts.  BIOS sees the device and boots from it.  All you can do is try it and see what happens although I'm not very optimistic.

+1

That pointy little head has a lot of good info!

---

### Post by presence1960 on 2009-08-21
> **russu52 said:**
> i agree with bartender's idea. i also wish to have ubuntu running on an external hdd without installing anything on my netbook. as external hdd i have a 320 gb ide in an enclosure which connects via usb, with an external power supply. i was planning to open up my desktop, connect this hdd (via ide) and install ubuntu on it as if it is the pc's main hdd. then i remove and plug it as usb to my netbook and boot from it. i just hope it works. if it does, i will post here.:P

no need to open up the box & disconnect anything. You can install Ubuntu to the external without affecting the internal disk. Also tt the Ready to install window click the Advanced button and choose sdb (assuming you have 1 internal and no other hard disks inside. This will put GRUB on MBR of sdb(external).

---

### Post by Lawand on 2009-08-21
@Bartender: your method worked and everything went OK, thanks mate :)

---

### Post by dames-fr on 2009-08-21
Hi everybody,
 
This note :
 
> **presence1960 said:**
> no need to open up the box & disconnect anything. You can install Ubuntu to the external without affecting the internal disk. At the Ready to install window click the Advanced button and choose sdb (assuming you have 1 internal and no other hard disks inside. This will put GRUB on MBR of sdb(external).
 
 
is the only need to setup Ubuntu on an external usb hard drive. It was quite simple but not documented and the setup is simply a bad development (Why hiding this parameter in a screen where there are only information? Why the partitonning tool is so limited?).
 
For information, I doesn't want to setup from cdrom but from a usb key but nothing works using the usb key generated with another Ubuntu desktop (using builtin usb creator).
 
Previously, I was using a SLAX distro on this external drive. I configured my laptop to boot first on USB and to boot on my SATA hard drive on a second time. SLAX use Syslinux, and I setup it to let BIOS to boot on the next device in the boot order after 5 second. It works great. My OS on the internal disk boot if I doesn't press any key. For information, I just use this command :
 
[FONT=System][SIZE=2]PROMPT 0[/SIZE][/FONT]
[SIZE=2][FONT=System]TIMEOUT 30[/FONT][/SIZE]
[SIZE=2][FONT=System]DEFAULT /boot/vesamenu.c32[/FONT][/SIZE]
 
[FONT=System][SIZE=2][...][/SIZE][/FONT]

[FONT=System][SIZE=2]LABEL local[/SIZE][/FONT]
[SIZE=2][FONT=System]MENU LABEL Boot Local Operating System[/FONT][/SIZE]
[SIZE=2][FONT=System][COLOR=red]LOCALBOOT -1[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=System]TEXT HELP[/FONT][/SIZE]
[SIZE=2][FONT=System]More about currently selected:[/FONT][/SIZE]
[FONT=System][SIZE=2]Run local disk Operatin System.[/SIZE][/FONT]
[SIZE=2][FONT=System]ENDTEXT[/FONT][/SIZE]
[FONT=System][SIZE=2]LABEL xconf[/SIZE][/FONT]
[SIZE=2][FONT=System]MENU LABEL Slax Graphics mode (KDE)[/FONT][/SIZE]
[SIZE=2][FONT=System]KERNEL /boot/vmlinuz[/FONT][/SIZE]
[SIZE=2][FONT=System]APPEND initrd=/boot/initrd.gz ramdisk_size=6666 root=/dev/ram0 rw autoexec=xconf;telinit~4 changes=/slax/[/FONT][/SIZE]
 
[FONT=System][SIZE=2][...][/SIZE][/FONT]
 
 
The special value -1 causes ISOLINUX to report failure to the BIOS, which, on recent BIOSes, should mean that the next boot device in the boot sequence should be activated. 
 
 
Ubuntu use Grub loader. With this configuration, I am unable to boot the OS in my SATA disk (Windows) without removing the external disk first.
 
Anybody know how to do the same with Grub loader?
 
There are many functions but I haven't found how to do this.
 
Hope this post help somebody.
 
Thanks.

---

### Post by Bartender on 2009-08-21
Hey, guys, I wanted to revisit this and sort of check in.  presence 1960, thanks very much for the clarification and I apologize if I caused confusion.  You're saying that the drive is identified in Linux-speak (sd_) instead of the more confusing GRUB terminology (hd_) in the "Advanced" option?

I'll have to remember that.  

I think it's appropriate to suggest the extra step of unplugging the internal drive (or *drives*, I should have mentioned that) just because it's too easy to screw up when you're new at this.  Making the external the only spinning drive in the system guarantees that GRUB goes where we want it to in this particular situation.

Lawand, I'm very glad to hear it worked out.  I was afraid that it would not.  With my NexStar dock, the power is supplied by a wall-wart and I can turn the external on before I boot the laptop.  My concern with a USB-powered external such as yours was that the BIOS would look for a bootable USB device but not see anything because the external would not be up to speed or might not even have power to it yet.  If BIOS saw nothing on USB it would move on to the main HDD.  Glad to hear that was not the case.

---

### Post by presence1960 on 2009-08-21
> **Bartender said:**
>  

I think it's appropriate to suggest the extra step of unplugging the internal drive (or *drives*, I should have mentioned that) just because it's too easy to screw up when you're new at this.  Making the external the only spinning drive in the system guarantees that GRUB goes where we want it to in this particular situation.



I agree with that, I said it wasn't necessary. Either way will work. I was just presenting another way to do the same thing. besides I as well as most others look for results before methods.

Actually everything you said is right on. Usually in Linux there are more than one way to accomplish the same task. So I believe putting all options out there not only helps the newer members but also some of the veterans. I am always looking to learn something new.

Gparted Live CD still shows IDE/PATA hard disks as hda, etc and SATA as sda, etc.

---

### Post by russu52 on 2009-08-22
> **presence1960 said:**
> no need to open up the box & disconnect anything. You can install Ubuntu to the external without affecting the internal disk. Also tt the Ready to install window click the Advanced button and choose sdb (assuming you have 1 internal and no other hard disks inside. This will put GRUB on MBR of sdb(external).

hello, just to confirm that i tried it too and it works. did not work on linux mint gloria, at startup says cannot mount partition, but on jaunty works well.

@presence1960
thanks for the hint, i didn't need to open up box etc.

---

### Post by presence1960 on 2009-08-22
> **russu52 said:**
> hello, just to confirm that i tried it too and it works. did not work on linux mint gloria, at startup says cannot mount partition, but on jaunty works well.

@presence1960
thanks for the hint, i didn't need to open up box etc.

Glad you got it up & running. Enjoy Ubuntu!

---

### Post by rubie on 2009-08-24
> **Bartender said:**
> Hey, guys, I wanted to revisit this and sort of check in.  presence 1960, thanks very much for the clarification and I apologize if I caused confusion.  You're saying that the drive is identified in Linux-speak (sd_) instead of the more confusing GRUB terminology (hd_) in the "Advanced" option?

I'll have to remember that.  

I think it's appropriate to suggest the extra step of unplugging the internal drive (or *drives*, I should have mentioned that) just because it's too easy to screw up when you're new at this.  Making the external the only spinning drive in the system guarantees that GRUB goes where we want it to in this particular situation.

Lawand, I'm very glad to hear it worked out.  I was afraid that it would not.  With my NexStar dock, the power is supplied by a wall-wart and I can turn the external on before I boot the laptop.  My concern with a USB-powered external such as yours was that the BIOS would look for a bootable USB device but not see anything because the external would not be up to speed or might not even have power to it yet.  If BIOS saw nothing on USB it would move on to the main HDD.  Glad to hear that was not the case.

FYI in my case the preset value under Advanced appears as (hd0), but if I click the drop-down box my disks are listed as sda and sdb. I installed choosing sdb from the list but booting fails after about two minutes with the PC hanging and a blank screen. I've been trying to do a full install on a USB HDD. I will now try typing in (hd1) manually and see what happens.

---

### Post by Bartender on 2009-08-24
rubie, let me know what you come up with.  I'm going to spin an Ubuntu install CD right now and see what happens.

---

### Post by rubie on 2009-08-24
Ok, typing in (hd1) in the Advanced options has the same result afaict: The machine hangs after loading grub and starting the boot process. I did the following to produce a successful boot after installing onto the USB flash HDD:

1. Set Primary Master to OFF in the BIOS drive options. This resulted in the install program recognizing only the USB drive.
2. Installed normally (install onto available contiguous free space) with default options (default destination for boot loader options seen as (hdo), device as sda in listbox under Advanced).
3. Shut down and booted up with the USB drive in. Internal HDD still in OFF mode.

It took a while, but the system did boot to the desktop which I could use normally thereafter. On shutting down though the system seemed to hang, so I shut it down forcibly (held on/off button). I then set the primary HDD back to AUTO, booted from USB (to see if it will boot with the internal HDD on) and once again the PC hung. I have no longer been able to boot from the USB drive, either with the internal HDD turned on or off. So there you have it, that's the latest situation :)

---

### Post by presence1960 on 2009-08-24
> **rubie said:**
> FYI in my case the preset value under Advanced appears as (hd0), but if I click the drop-down box my disks are listed as sda and sdb. I installed choosing sdb from the list but booting fails after about two minutes with the PC hanging and a blank screen. I've been trying to do a full install on a USB HDD. I will now try typing in (hd1) manually and see what happens.
sda will put GRUB on MBR of that disk and sdb will put GRUB on MBR of sdb. if you choose sda1 that will put GRUB on the first sector of sda1- which is very useful for adding extra linux distros to chainload (like windows chainloads) off the GRUB on MBR which takes over when you boot. The other partition entires i.e. sda2, sda3, sdb1, sdb2 etc do the same thing.

---

### Post by Bartender on 2009-08-25
I haven't visited the "Advanced" button for a while.  It sure is different than I remember.  I got what you guys describe - the box just said hd(0), then the dropdown showed /dev/sda, /dev/sda1, /dev/sda-1. /dev/sdb, and dev/sdb1.

The developers have obviously put some work into making this more fool-proof, but I'll admit I was confused.  No matter what they put under the "Advanced" mode there's a problem.  If the operator doesn't know *exactly* where he/she wants to put the bootloader, the options will seem confusing.

Worldwide confusion over GRUB is not something that the devs can fix by tweaking the "Advanced" options :)  If they were to somehow build an interactive guide into the installer that recognized the possibilities and suggested options maybe.

BTW, I set up partitioning options on my test PC, then went into the "Advanced" button, then Quit.  The drives were unaffected.  So it looks like you can bail out of an installation even after setting up the partitioning scheme and not make any changes to your hardware.

EDIT:  rubie, that was good thinking on your part to "Disable" the internal drive in BIOS.  I've got two suggestions for you, but they're just guesses.  Your internal drive is Windows?  Correct?  I'd try fixing the mbr on that drive.  Zillions of posts on that subject.  Get Windows working again, then you'll feel better about this experimental stuff.  As far as the external goes, I'm just wondering if there's something in the way the external identifies itself?  Since Ubuntu is installed entirely on that external, it's like a portable PC.  Got a few friends who wouldn't mind letting you tweak their BIOS, then spin the external?

---

### Post by rubie on 2009-08-26
Ok, I installed Ubuntu onto an actual external HDD (instead of a thumb drive), and it works like a charm :) FYI I kept the internal drive on and chose /dev/sdb in the bootloader options. No change was made to the internal drive and I can boot Windows normally.

---

### Post by Bartender on 2009-08-26
Glad to hear it! =D>

Installing to a thumb drive is different - I don't know why, and I haven't tried it...

---

### Post by russu52 on 2009-08-26
i tried installing both on external thumb drive and external hdd. used same procedure for both. both work well, except that hdd is faster.

---

