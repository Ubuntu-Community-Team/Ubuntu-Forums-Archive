---
title: "Modify Grub to boot from USB"
date: 2008-07-14
forum: General Help
---

### Post by jukingeo on 2008-07-14
Hello all, 

I know this is a topic that has been brought up time and time again.  I HAVE searched the forum and while I have come up with a several solutions, all seem to be very vague at getting to the goal.  So I am going to attempt to describe my EXACT situation and hopefully I can get a straight forward solution that would suit my needs.

Ok, then.  I initially started with a Dell Dimension 4600 with Windows XP loaded onto the main hard drive which is an IDE 80gig Maxtor.   I then installed a second hard drive, a Seagate SATA 500gig drive as my secondary drive.  This drive is set up to be the boot drive for a Linux installation and also extra storage space.  I set up Ubuntu to boot from this drive.

Thus because I have a dual boot system, I had to install Grub.

Grub has been successfully installed and it is set to default to the Ubuntu installation.  Windows XP is the secondary.

Now what I want to do is add another option to Grub to boot from USB.  The reason for this is because I want to set up Puppy Linux on a USB flash memory for a specific project.

My machine WILL NOT boot to USB from Bios.  But I was told that since I boot up to Grub first, that I could have Grub do it. So my goal is to add an entry to Grub that would allow me to boot to USB.

Thus given my situation, I am looking for the most straightforward way of accomplishing this task WITHOUT messing up my current dual boot to Ubuntu and Win XP.

Thank You,

Geo

---

### Post by mikewhatever on 2008-07-14
I may be wrong, but if your hardware can't boot from USB, what makes you think GRUB bootloader can?

---

### Post by jukingeo on 2008-07-14
> **mikewhatever said:**
> I may be wrong, but if your hardware can't boot from USB, what makes you think GRUB bootloader can?

Don't know...that is why I am here to find out.  It is true that I am not 100% sure if my machine can boot or not.  USB IS recognized by my bios.  But the question is can it BOOT from it.  There is no selection in the boot up sequence (bios now, not grub) for USB.  But then again, I never had a bootable USB device in the port on boot up.  I guess that is something I would have to try out.

But I would have to assume, "No" it will not boot.

Outside of this situation here, I do have older machines that I know for a fact will not boot from USB.  So acquiring the knowledge to work around this problem still is of use to me.

EDIT:  [SOLVED]

Hello all, as of today I have cleared up the issue in regards to whether my machine can boot from USB or not.  The answer is yes it can.

I performed this test:

[http://www.pendrivelinux.com/2007/09/17/testing-your-system-for-usb-boot-compatibility/](http://www.pendrivelinux.com/2007/09/17/testing-your-system-for-usb-boot-compatibility/)

It passed.

My computer BIOS recognized the bootable USB drive and from there I got a new boot order select and I put the USB drive on priority.

Doing this I don't even need to edit Grub anymore.  My system will recognize a bootable pendrive and automatically boot from it.  If it isn't there, it simply just boots up the way it normally does.

Thanx,

Geo

---

