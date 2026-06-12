---
title: "No sound and slow Internet on Skylake PC"
date: 2016-03-19
forum: Hardware
---

### Post by sanssadness on 2016-03-19
I decided to try Ubuntu on a Skylake computer recently. I wanted to use 14.04 LTS instead of the latest version because it's a work computer and I prefer stability over the latest features.

I'm now in over my head and really need some help. There are 2 problems with my installation:
1. Sound doesn't work (it's not muted)
2. My Internet is about half the speed of what it should be. Could this have something to do with my network driver not working?

[s]
I foolishly tried fixing the problems myself instead of asking for help. I came across this article here:

[https://www.pantz.org/hardware/motherboard/intel_skylake_with_an_asus_z170-ar_and_ubuntu_linux_14.04.html](https://www.pantz.org/hardware/motherboard/intel_skylake_with_an_asus_z170-ar_and_ubuntu_linux_14.04.html)

I foolishly ran the command suggested:

[FONT=courier new]sudo apt-get install --install-recommends linux-generic-lts-wily xserver-xorg-core-lts-wily xserver-xorg-lts-wily xserver-xorg-video-all-lts-wily xserver-xorg-input-all-lts-wily libwayland-egl1-mesa-lts-wily[/FONT]

Now my computer is completely messed up. When I try to boot into Ubuntu, I get taken to some kind of tty1 terminal instead of my desktop! Because the installation was encrypted, I'm now trying to figure out if I can mount it from external media. What a mess. If I can't fix this problem, I'll have to revert to my most recent backup, which is missing some fairly important data.[/s]

**TLDR summary**
I messed up my installation of Ubuntu trying to fix 2 problems: 1) slow Internet and 2) No sound (it's not muted). Both problems may be due to the hardware being too new. [s]I also could use some help mounting a LUKS-encrypted partition so I can copy over some data from it before I wipe the drive and reinstall.

Once I've recovered my data or decided to lose it, I still need to figure out how to get sound and my usual Internet speed back.[/s] Please help!

**Edit**: I just wanted to provide an update on the data recovery issue. I managed to mount the encrypted data and recovered what I need (yay!). At this point I'm going to wipe the partition and start over anyways, but I would still like to know why running that command above prevented Ubuntu from booting (for educational purposes). I used strikethrough on those parts to deemphasize their importance because my 2 main problems (network and sound) still remain.

---

### Post by sanssadness on 2016-03-21
Anyone?

---

### Post by mörgæs on 2016-03-22
Skylake is one of the latest CPU series available and one can't expect old software like 14.04 to work. I would go for 15.10 which is a highly stable release.

---

### Post by oldfred on 2016-03-22
I just built new Skylake system, and installed 16.04 as I do not worry if it does not boot as I have full installs on flash drives that should still boot.
But 16.04 with new kernel, support software & drivers just works, where older Ubuntu versions often need updates to in effect add the kernels & drivers that are now default in 16.04.
With very new hardware it takes a while for software to be updated, then further time before those updates are considered stable and included in a new distribution.

       oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)

---

### Post by sanssadness on 2016-03-22
Well I just tested Ubuntu 15.10 (live disc) from external media. I'm having the same problems. I have no sound at all and my download speed is about 15% of capacity.

---

### Post by sanssadness on 2016-03-22
I know people have no obligation to reply, but is there something wrong with my post? Maybe the title or the section I posted it in? I see a networking section and will use that one soon, but there's no separate section for sound!

It's been fun but I'm on the verge of going back to Windows. These problems are fatal for my work environment, and returning the computer isn't an option.

---

### Post by oldfred on 2016-03-22
What brand/model system?
Which skylake cpu?

 Intel's Skylake Audio Firmware Lands
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Skylake-Audio-Firmware](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Skylake-Audio-Firmware)
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-BXT-Firmware-Blobs](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-BXT-Firmware-Blobs)

---

### Post by goofprog on 2016-03-22
I had a problem with sound when I changed my hard drive to another computer.  I took it from a laptop to my tower computer that has no internet.  It had no sound but I found out why.  I was using HDMI so I just selected the sound output on the HDMI line under** system settings / sound**.  The internet being slow is always an issue.  I guess that is why some people can get PH.D degrees in computer networking.

---

### Post by sanssadness on 2016-03-22
That's true. I guess I should have been more clear that I suspected a driver problem that caused the slow network problem.

I'm totally lost on Ubuntu even though I've been using it for a while. Every time I need to figure out how to do something, I can only Google it. Even when I find an answer that works, I don't understand it most of the time. The best I can do is keep a list of commands known to work in a file. They don't teach you this stuff in schools, that's for sure.

I made some progress on the sound problem, but one potential fix requires installing the latest Alsa driver. I found these instructions:

[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

They led me to this page:

[https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages)

The right driver for Ubuntu 14.04 LTS is oem-audio-hda-daily-dkms - 0.201603221016~ubuntu14.04.1

However, there is no .deb file. Extracting the tar.gz file gives a bunch of folders and a Makefile. I run "make" in terminal, and it gives me some error message:

make: *** No rule to make target '.../oem-audio-hda-daily-dkms-0.201603221016-ubuntu14.04.1/buildroot/unpatched-source', needed by 'patched-source'. Stop.

Why won't it compile?

---

### Post by Drone4four on 2016-03-22
> **sanssadness said:**
> I know people have no obligation to reply, but is there something wrong with my post? Maybe the title or the section I posted it in? I see a networking section and will use that one soon, but there's no separate section for sound!

It's been fun but I'm on the verge of going back to Windows. These problems are fatal for my work environment, and returning the computer isn't an option.

Skylake is bleeding edge.  Ubuntu 14.04 was from 2 years ago. Skylake technology wasn&#8217;t invented yet when the 14.04 CPU driver (the Linux kernel version 3.13) was written.  Skylake hardware is only supported in kernel > 4.2 .  So it might be possible to get around the errors and obstacles your involved with 14.04, then install the latest kernel from an unofficial repository and then have a working system.  This is a &#8216;mission&#8217; for sure though, especially for someone new to Linux. It is doable though.  Instead you could spin the beta release of 16.04 on USB just to get a feel and see if it loads.  I know you said you only want stability.  Therefore I would recommend you wait until 16.04 is released at the end of April so you can be guaranteed stability to install Ubuntu native at that point.  Skylake will run smooth as silk, better than Windows.

I am really sorry to read that your first experience with Ubuntu is less than acceptable.  I would feel inconvenienced if I were in your position.

If you do choose to stay with Windows, then please understand that you are always welcome back in our community when its easier to Skylake software support is mature and ready for prime time.  

=D

---

### Post by oldfred on 2016-03-22
I would just try 16.04.

Then minute you have to start compiling your own drivers & kernel, you are now a developer and responsible for all dependencies.
And that is likely to be less reliable than just using 16.04.

---

### Post by sanssadness on 2016-03-22
Well good thing 16.04 is coming out next month. I took your suggestion and I'm going to test the 16.04 beta. My frustration is not with the occasional problem in 14.04, but the fact that everything appears to load perfectly (except the sound).

I have an update on the network problem. Turns out it was hardware related, which is actually great news. I'd much rather pay to replace a piece of cheap hardware than to spend days trying to get sound back!

This means the only major problem left is that I have no sound right now. If I can get it working, I will have the luxury of reading a book on Ubuntu (I'm running into so many problems that I'll probably save time in the long run reading a book once instead of Googling every little problem) and tackling the minor problems at my own pace.

If someone knows how to fix that compilation error, please help. The instruction page says there should be a .deb file but there isn't.

Edit: Just missed what oldfred posted. I already backed up all my data so I don't mind trying whatever crazy stuff will potentially fix this problem. If 16.04 does work, can I update to the final release when it comes out next month?

---

### Post by kurt18947 on 2016-03-22
My newest hardware is from about 2010 so I'm of no help with bleeding edge stuff. I'm just seconding the advice to check your sound sources and settings. That one bit me a time or two. The last I knew sound over HDMI is pretty unreliable for example. I've been using 16.04 daily for a month or more. On my older machines it is already quite stable for my uses. As a rule shiny new hardware families is best avoided if possible. Once a device or chipset has been available for  6 months or a year there is usually support for it without resorting to backports, PPAs and that sort of thing.

---

### Post by sanssadness on 2016-03-22
So many problems. I just tried 16.04 beta. When I try to boot from the USB disc, I get this message:

Missing parameter in configuration file. Keyword: path
gfxboot.c32: not a COM32R image

I type "help", then press ENTER again to boot (another thread suggested this as a fix). I apparently start to boot, but then my computer hangs at a purple screen (presumably the wallpaper).

After extensive searching, I then find out there's a problem with the Startup Disk Creator that causes this. I was skeptical that this was the real problem because the problem was reported back in Ubuntu 10.04!

What's the cost of a DVD compared to your time right? So I burn the .iso to a blank DVD instead of using a USB drive. Sure enough, it does boot. But I remember the purple wallpaper hang, so I take the time to choose the F6 option "nodemoset."

Still it hangs at the purple wallpaper.

---

### Post by mörgæs on 2016-03-23
> **sanssadness said:**
> If 16.04 does work, can I update to the final release when it comes out next month?

Yes, just do the normal updates and you will get to the final release.

---

### Post by oldfred on 2016-03-23
If you have a Skylake, it will be an UEFI system.
So you should not be getting a BIOS boot purple screen, but grub menu.
UEFI should offer two boot choices for flash drive or DVD. One should be UEFI:name and other just name or BIOS boot.

       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[URL="http://ubuntuforums.org/showthread.php?t=2299040"]http://ubuntuforums.org/showthread.php?t=2299040

      [/URL]
 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
    [URL="http://ubuntuforums.org/showthread.php?t=2299040"]
[/URL]

---

### Post by sanssadness on 2016-03-24
I am using BIOS (the system has an option to use legacy booting) because no free full disk encryption software is currently compatible with UEFI. The disc does boot properly when I set my BIOS to use integrated graphics, so the problem is most likely caused by my video card. If I can just figure out how to boot properly long enough to install the driver for my video card, then I'll be one step closer to ending this nightmare.

---

### Post by oldfred on 2016-03-24
What video card/chip.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

