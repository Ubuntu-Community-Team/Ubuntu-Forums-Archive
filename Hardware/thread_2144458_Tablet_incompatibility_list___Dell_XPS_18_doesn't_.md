---
title: "Tablet incompatibility list?   Dell XPS 18 doesn't work with Ubuntu 13.04 x64"
date: 2013-05-12
forum: Hardware
---

### Post by fr33z0n3r on 2013-05-12
_Where is the AIO or tablet incompatibility list?_   lol...  I figure I'll make a new post here instead of posting it in the desktop or laptop lists, only to be chastised by both groups that my device doesn't belong there.  :)


Ubuntu 13.04 x64  Live DVD
Dell
XPS 18  (it's an AIO, it's a tablet, it's a PC!)

I got the Ubuntu 13.04 x64 DVD to boot in UEFI mode (only modifying the UEFI boot order when dvd drive connected)  but it will not handle touch at all.  Also couldn't get programs to open from the Dash bar with the Enter key (generic Amazon keyboard here)  But Enter worked in other places inside Ubuntu.  I'd be happy to try and collect info from the device to assist with future driver support, but will need to know what to do to collect it from a live DVD.


**[SIZE=6]UPDATE[/SIZE]**:   **Ubuntu 14.04 finally provides touchscreen support for the Dell XPS 18.**

Read on here for new issues:
[http://ubuntuforums.org/showthread.php?t=2144458&p=12992838#post12992838](http://ubuntuforums.org/showthread.php?t=2144458&p=12992838#post12992838)

---

### Post by fr33z0n3r on 2013-05-13
based on a Dell patch, I think the VID and PID are one of these.  But I'll verify later in the week.

SYSTEM\CurrentControlSet\Enum\USB\VID_0457&PID_1039
SYSTEM\CurrentControlSet\Enum\USB\VID_2149&PID_230A&MI_00
SYSTEM\CurrentControlSet\Enum\USB\VID_2149&PID_2316&MI_00
SYSTEM\CurrentControlSet\Enum\USB\VID_2149&PID_270B&MI_00
SYSTEM\CurrentControlSet\Enum\USB\VID_222A&PID_0018

---

### Post by tahdas on 2013-05-14
Does any ubuntu work on this system? I want to get an dell 18 sometime in the future, so i'd like to know if i can run ubuntu on it.

---

### Post by fr33z0n3r on 2013-05-15
Well,  It seems like Ubuntu generally worked.  The exceptions I noticed are:

1.  No touch
2.  No wireless keyboard (or mouse)  probably since this is the Logitech Unifying driver, not some generic bluetooth type.
3.  Issues with Enter key on generic USB keyboard.

I didn't try a USB mouse, since I ran out of USB ports.  I would imagine it would work, and is critical without touch support.

I'm not sure where to pursue getting support for the touchscreen added (the key issue).  But I plan on trying to probe the forums for info.

---

### Post by tahdas on 2013-05-15
Don't you have to get the touch driver or something like that? Or maybe its an issues with 13.04 64, maybe you should try regular 13.04 or 12.04. Please note that i am not a computer engineer or anything like, but just some kid who has an interest in computers. So take my advice with a spoonfull of salt.

---

### Post by tahdas on 2013-05-20
BUMP

did you ever get it working?

---

### Post by fr33z0n3r on 2013-05-21
I do not have access to the device.  It was a gift for someone else.  Next chance  I get I'll be trying a x64 Ubuntu USB stick to see if that works.  I doubt it will, but who knows.  I will also collect the data folks seem to ask for related to unsupported devices.

---

### Post by z_mikowski on 2013-06-09
> **fr33z0n3r said:**
> I do not have access to the device.  It was a gift for someone else.  Next chance  I get I'll be trying a x64 Ubuntu USB stick to see if that works.  I doubt it will, but who knows.  I will also collect the data folks seem to ask for related to unsupported devices.


Check this out: [http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)

Apparently, touch is possible.  I certainly would be interested in seeing this in action!

---

### Post by fr33z0n3r on 2013-06-09
I wrote up a big response and of course it got lost on submission.

 Different device. Will try to get touch working on Friday.

That post, does go through the convoluted process for getting Ubuntu installed on a UEFI system - which sounds like a pain.  I'm not sure I'm going that far yet.  Just getting it to boot to USB from UEFI was annoying enough. The USB stick design SHOULD be able to have the same driver support (since its a full install, not a live USB design).  This avoids the messy partitioning.

As I said I'll be trying to see if x64 USB will get me further in driver support.  I'll also consider the PPA noted in the post mentioned.

---

### Post by fr33z0n3r on 2013-06-14
well, I've opened a bug for this touchscreen issue.  Not sure if anything will be done.  But at least info is collected and shared.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1191008](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1191008)

The provided keyboard is working fine.  I am using a USB mouse without issue also.  This is all with the x64 Ubuntu 13.04 live DVD.  My attempt at a x64 USB stick failed - probably not truly UEFI bootable for some reason (no clue how to make it so).  I wil ltry to rebuild it from the live DVD now.

---

### Post by fr33z0n3r on 2013-06-16
I was reading up on how to build a USB stick for UEFI booting from the live CD, but just before I started the system got hosed and I had to leave.  So no more progress on this yet.

---

### Post by ussenterprisencc1701 on 2013-08-20
See ongoing bug for Dell XPS 18 Touch at URL: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1205494](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1205494) 

Also, you *can* boot an Ubuntu ISO written to USB flash drive (USB stick), however you will need to disable UEFI secure certificate.  Boot with left buttons depressed then press right button for 3-4 seconds, to get into setup.   But please verify the XPS 18 manual, or online info about getting into setup.   I am able to boot from USB flash drive no problem, having done this.  Once you changed the UEFI settings, then when you bootup, press the top left button, and while depressed, press the right side power button for 1-2 seconds, then release, and it will get you to a boot menu, so you can choose the USB stick.  

BTW the Dell XPS 18 touchscreen, is *not* a tablet computer per say (in the sense of iPad or Andoid tablets), it is a real/full computer running a real/full OS like any other PC which runs full Windows 8 (also Pro), but can also run Linux distributions.  It is an "all in one" PC computer with a touchscreen.

It does concern me that more Linux developers need to be involved or aware of the advent of these all-in-one TOUCHSCREEN Personal Computers which are now out there in the marketplace, and Linux needs to be able to support touchscreen to a much larger/better degree, including finger gestures, keyboard integration, and the like.    In other words work out the kinks amd klunkiness, and make it smooth.

Meanwhile, if you have Windows 8 on your Dell XPS 18 touch, you can install VMware Player, and install your favorite Linux distribution as a virtual guest OS, like Ubuntu, Mint, Fedora, etc. and those will support the touchscreen through VMWare Player's integration.     I know, I've done it and it works quite well.     I say "meanwhile" because when you boot Ubuntu 13.x, Mint 15, and Fedora 19, from USB flash drive, they do not support the touchscreen - I know, I've tried them.    So virtual is the way for the time being, and hopefully that will change soon.  To install a Linux distribution in VMWare Player, have the ISO image file handy on a USB flash drive, accessible to VMware Player through Windows 8.   I occasionally use Windows 8 for web browsing, but for real work I bootup Linux from VMware player.

---

### Post by fr33z0n3r on 2013-08-20
> **ussenterprisencc1701 said:**
> See ongoing bug for Dell XPS 18 Touch at URL: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1205494](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1205494) 
Meanwhile, if you have Windows 8 on your Dell XPS 18 touch, you can install VMware Player, and install your favorite Linux distribution as a virtual guest OS, like Ubuntu, Mint, Fedora, etc. and those will support the touchscreen through VMWare Player's integration.     I know, I've done it and it works quite well.     I say "meanwhile" because when you boot Ubuntu 13.x, Mint 15, and Fedora 19, from USB flash drive, they do not support the touchscreen - I know, I've tried them.    So virtual is the way for the time being, and hopefully that will change soon.  To install a Linux distribution in VMWare Player, have the ISO image file handy on a USB flash drive, accessible to VMware Player through Windows 8.   I occasionally use Windows 8 for web browsing, but for real work I bootup Linux from VMware player.

Regarding the use of Vmware - this does not eliminate the reason I am using Linux - which is to ensure that no malware could have control of my system.  Using linux inside a virtual environment simply provides access, but does not provide the same security.

At this point I'm hoping you can work with support to get this touchscreen issue fixed as I do not have easy access to the device.

---

### Post by fr33z0n3r on 2014-03-26
FYI, Trusty Tahr 14.04 daily images now appear to be able to provide touchscreen usage.  I've had someone test it and it seems to work with a USB DVD drive and the current daily TT image.  I'm now struggling to get it to work with a USB 3.0 thumb drive.  I suspect that it might work with a usb 2.0 usb stick.  BIOS A5 was supposed to fix a usb 3.0 boot detection issue.  I have A6 loaded but I believe this is the problem I'm seeing.   So all of the basic hardware works on this computer with Trusty Tahr.  Didn't test bluetooth, but it showed up.

EUFI boot worked from the x64 DVD (using a BIOS boot menu maybe?)

---

### Post by fr33z0n3r on 2014-04-18
As I started this thread a year ago,  and its still relevant  it rises again.  Hopefully someone comes back here.

1. I have spent the past month trying to get betas of Ubuntu 14.04 x64 working on USB sticks with my Dell XPS 18.   I was able to go into the BIOS and manually add in the USB stick (that was plugged in) selecting the boot efi file needed.  It was able to boot from that, while Windows 8 (and the UEFI) was still setup in secure mode.  

XPS 18:
UEFI boot
Secure Boot enabled

USB Stick:
GPT partitioning
EFI partition of 400MB
/boot  1GB ext2 partition
LVM (?) device for encryption  
 - /  ~16GB ext4  volume

But if you just plug the usb stick in and try to access it via the boot menu, it is NOT seen by the BIOS and can only go right to Windows.

Anyone have ideas on why a properly built USB stick would do that?  (I tried a USB 2.0 AND a 3.0 stick - different brands)  I also tested with a USB DVD drive, and it could (of course) boot a Ubuntu x64 disc from the boot menu.  

2.  I therefore switched to a dual boot method.    Same XPS 18 info as above.  I shrunk the Windows 8 partition  using its internal repartition tool that has FINALLY become modern.  in the 28 GB space I made the following:
 - /boot 1GB ext2
 - /  24 GB  ext4
 - /windows 4 GB FAT32 for windows file sharing 

I now have a red error that appears when the computer is booted saying "Secure Boot Violation - Invalid Signature detected.  Check Secure Boot Policy in Setup".

So, it does NOT prevent me from accessing Windows OR Ubuntu,   but who need a red error at every startup.  Does this sound like a UEFI secure boot config that that restricted the computer to only boot Windows?  Or does this indicate a secure boot issue with my Ubuntu?

---

### Post by e7ail on 2014-05-19
I just wanted to thank you for pursuing this. I own an 18 AIO, and I love it. I, for a little while, had Xubuntu running fine (insecure boot mode), and touch works pretty well on 14.4. I am going to spend some more time on getting it up and running in the coming weeks, but as a Linux noob I am always a bit hesitant. 

Touch works, and is pretty accurate (not perfect) with location.
The accelerometer does not work properly to auto-rotate the screen.
Keyboard worked fine once I had it configured to my liking. 

I could not figure out how to "right click"...

Thanks again.

---

### Post by Elizabeth_Moore on 2014-05-24
Hello! I'm new to this forum AND to Linux/Ubuntu. Therefore, I apologize for any noob comments from myself. I was able to install version 12.04 with no issues (I already had this version downloaded from having to use it previously to get information off of my computer). I'm now running the upgrade to 14.04. As of this moment, touch screen does not work. I didnt have any issues installing the OS like others have mentioned. The only thing that doesnt work that I know of is the touchscreen, which I hope can be fixed. One other issue I do notice is that every so often, the screen will flash and all windows, side bar and status bar disappear for a few seconds and then reappear. This will get highly irritating. I am hoping that it will be fixed with updating to 14.04, which is currently upgrading.

---

### Post by fr33z0n3r on 2015-01-08
> **fr33z0n3r said:**
> As I started this thread a year ago,  and its still relevant  it rises again.  Hopefully someone comes back here.

1. I have spent the past month trying to get betas of Ubuntu 14.04 x64 working on USB sticks with my Dell XPS 18.   I was able to go into the BIOS and manually add in the USB stick (that was plugged in) selecting the boot efi file needed.  It was able to boot from that, while Windows 8 (and the UEFI) was still setup in secure mode.  

XPS 18:
UEFI boot
Secure Boot enabled

USB Stick:
GPT partitioning
EFI partition of 400MB
/boot  1GB ext2 partition
LVM (?) device for encryption  
 - /  ~16GB ext4  volume

But if you just plug the usb stick in and try to access it via the boot menu, it is NOT seen by the BIOS and can only go right to Windows.

Anyone have ideas on why a properly built USB stick would do that?  (I tried a USB 2.0 AND a 3.0 stick - different brands)  I also tested with a USB DVD drive, and it could (of course) boot a Ubuntu x64 disc from the boot menu.  

2.  I therefore switched to a dual boot method.    Same XPS 18 info as above.  I shrunk the Windows 8 partition  using its internal repartition tool that has FINALLY become modern.  in the 28 GB space I made the following:
 - /boot 1GB ext2
 - /  24 GB  ext4
 - /windows 4 GB FAT32 for windows file sharing 

I now have a red error that appears when the computer is booted saying "Secure Boot Violation - Invalid Signature detected.  Check Secure Boot Policy in Setup".

So, it does NOT prevent me from accessing Windows OR Ubuntu,   but who need a red error at every startup.  Does this sound like a UEFI secure boot config that that restricted the computer to only boot Windows?  Or does this indicate a secure boot issue with my Ubuntu?


FYI - this was solved, and mentioned elsewhere.  But here is the missing note after encountering this "[COLOR=#ff0000]**red error**[/COLOR]".  It is not a big deal on my system, just an indication that the boot order does not have (the shimx64 entry for) Ubuntu first.

"I then realized that I could set the boot order in the BIOS! (UEFI) .   Sure enough, there were 3 entries now (1 for Windows, 2 for Ubuntu)  I  was so relieved when merely changing the order from using the grubx64  entry to the shimx64 entry fixed the boot error.  Unfortunately, both of  the boot entries for ubuntu have the same label, so are impossible to  distinguish.   I made an additional entry with a clear label to solve  that issue.  Now the owner boots to Windows automatically, and can press  F12 at boot to get into Ubuntu.  Sufficient for us."

To followup on this, whenever I updated the linux-firmware (via Software Updater), this UEFI boot order was reset and I had to again guess at which "Ubuntu" to use.  We finally just gave up with changing it, and "just figure it out" going forward since the "working choice" was always in the same position (until the next linux-firmware update)

---

### Post by ico_ico on 2015-12-29
Hi, 
I'm also new in this forum,. I use Ubuntu 14.04 on dell XPS 18. It's great. There are two things that not work properly. The hardware volume buttons. They work but down button make volume to 0% and up button to 100%. And the rotation (sensor). Except this everything work perfect. I will never use window$ 10 again :)

---

