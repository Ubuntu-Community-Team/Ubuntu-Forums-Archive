---
title: "You are my last hope..."
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by husky55 on 2009-01-19
for installing ubuntu 8.10 on my new laptop (see signature).

I installed ubuntu 8.10 on 2 desktops and my dell inspiron laptop without any problem.

But over the holiday I got a new Gateway FX and vista home premium 64 bit. I did check the mdsum of the downloads, used either 32 or 64 bit ubuntu, burn cd at lower speed. All to to no avail.

The live CD works but no connection to the internet via intel wifi mini pci 5100.

Installed ubuntu seems to be ok, but hung on reboot. Over and over again.

I don't know what causes this, pretty sure it's hardware incompatility. Could be the video card (newly introduced), DDR3 ram, or etc.. Since I cannot even get to the boot screen all diagnostic are not available to me.

So  I am ready to give up and you are my last hope. If not, I will use my other computers for ubuntu and wait for 6 months for a new revision.

:confused:

---

### Post by husky55 on 2009-01-30
There was some help on the notebookreview.com forums from epr194:

Hey Husky,

As a recent 7805 owner and Ubuntu fan, I too ran into the same problem with Ubuntu 8.10 64 bit installation.

My Wireless did work with the Live CD though...

Even when trying to boot in Kernel Recovery/Safe mode, it still failed to boot. FYI: It stopped with a line about a SCSI drive.

I got lucky and got it to work though.

So, I thought that I would make the effort to post my accidental fix in the hopes that it might help others.

I was going to uninstall GRUB and Ubuntu, but to do that I needed a Vista boot disk to run the "fixmbr" utility to get rid of the GRUB bootloader. I am not sure if that would have actually worked though...

So, I pop a vista installation disk in the DVD drive, then reboot. 

I got distracted and came back to my lappy 10 minutes later to see that Ubuntu has loaded successfully.

WTH?!?!

So, I reboot again to make sure I'm not seeing things.

It asked to hit enter or any key to boot from the CD/DVD drive and I let it time out again.

Then the Grub bootloader screen came up and it then booted successfully into Ubuntu.

I tried it again without the bootable CD in the drive, and it failed to boot again.

So, re-inserted the CD, rebooted, Ubuntu loaded and I then promptly got the 250mb worth of patches installed. It applied a new kernel during the patch.

Removed the Vista CD, Rebooted and Presto! 

Ubuntu works flawlessly now.

My problem is ubuntu lockup after install and reboot. The only way I can get out of the lockup was to pull the battery and power plug.

It seems to me there is a problem with the windows boot loader. I hesitate to create a partition just for ubuntu because of potential MBR conflict with Vista64 which I really need.

Any help is appreciated.

---

