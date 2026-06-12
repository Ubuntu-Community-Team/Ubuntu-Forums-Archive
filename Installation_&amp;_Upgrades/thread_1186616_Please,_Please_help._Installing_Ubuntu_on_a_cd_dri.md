---
title: "Please, Please help. Installing Ubuntu on a cd driveless laptop"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by Chaos Punk on 2009-06-13
I have a pretty old laptop that I recently found in storage. We had stopped using it because the Windows OP that was on it caught a virus and will no longer boot. I recently installed Ubuntu on my dekstop, and made a bootable USB installer, only thing is, my laptop's BIOS does not support booting from USB. I'm sure this question gets asked alot, but I need a way to boot what's on my USB thumb drive using a floppy. I've searched for a while and found that all instructions for installing GRUB on a floppy are in linux, but I need to install it using Windows XP. Again, CD installation is not a possibility and it will not boot from USB. Please, someone tell me there's a way to install Ubuntu OR Windows on it, preferrably Ubuntu, I love it.

---

### Post by Chaos Punk on 2009-06-13
Bump, sorry, I really need this to work.

---

### Post by kerry_s on 2009-06-13
do you have another laptop? you can pull the drive install on another laptop and put it back in.

try this:
[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

---

### Post by Chaos Punk on 2009-06-13
Nope, no other laptop, and noone will let me use theirs because their afraid I'll break theirs, even though I've explained over and over again that THEIR hard drive will not be in the system.

---

### Post by joyneo04 on 2009-06-13
download from net...install it in flash drive....

---

### Post by Chaos Punk on 2009-06-13
> **joyneo04 said:**
> download from net...install it in flash drive....
I said twice "booting from USB is not an option". And I just cannot get bootmanager on my floppy, I'm getting very frustrated.

---

### Post by joyneo04 on 2009-06-13
deeply apologize...

---

### Post by Chaos Punk on 2009-06-13
okay, I manged to finally get Smart Boot Manager on my floppy, but does it support booting from USB? If so, how do I do it? And couldn't I just flash my BIOS or something to make is support usb booting?

---

### Post by kerry_s on 2009-06-13
> **Chaos Punk said:**
> okay, I manged to finally get Smart Boot Manager on my floppy, but does it support booting from USB? If so, how do I do it? And couldn't I just flash my BIOS or something to make is support usb booting?

plug in your usb, boot from the floppy, select usb.

---

### Post by Chaos Punk on 2009-06-13
> **kerry_s said:**
> plug in your usb, boot from the floppy, select usb.
It doesn't give that option, that's why I assume that it can't do that. It only gives me the same options as the internal BIOS does, harddrive or floppy.

---

### Post by kerry_s on 2009-06-13
> **Chaos Punk said:**
> It doesn't give that option, that's why I assume that it can't do that. It only gives me the same options as the internal BIOS does, harddrive or floppy.

what is the make/model of this laptop?
can it even run ubuntu?
have you looked at floppy distros?

---

### Post by Chaos Punk on 2009-06-13
> **kerry_s said:**
> what is the make/model of this laptop?
can it even run ubuntu?
have you looked at floppy distros?

Its a cf-28 pansonic toughbook, and yes, it can run ubuntu, it has xp on it, but its unbootable. My problem is that i cant boot the instalation disc or usb drive. Yes, i have looked at floppy distros, but i want to either install ubuntu or reinstall xp.

---

### Post by jamvaru on 2009-06-16
I have this same problem, sort of:

Old dell laptop with pentium II 266 (i think), like 128 mb ram, and no cd-rom, though it does have a floppy...

I remember there was a knoppix floppy or something that would boot and scan the usb for a certain version of linux installed on that usb... but i can't find it now

another one i tried was able to boot to my pcmcia usb 2.0 card, ie-enable it, so i could copy win 2k files to the hard drive (i had used fdisk to format the drive)

I now want to install ubuntu on it but forgot where i got the floppy's and no longer have them.

(oh, yeah, i'm going to try this:  [http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/), but... we will see)

SO,

I need:

1.  floppy img to boot and enable usb access
2.  version of linux that will then format the hd and install from the usb.

i imagine it would also run from the usb.

so, can i put linux on a usb from windows and then use that with a floppy boot loader to install to the laptop?

---

### Post by Chaos Punk on 2009-07-15
> **jamvaru said:**
> I have this same problem, sort of:

Old dell laptop with pentium II 266 (i think), like 128 mb ram, and no cd-rom, though it does have a floppy...

I remember there was a knoppix floppy or something that would boot and scan the usb for a certain version of linux installed on that usb... but i can't find it now

another one i tried was able to boot to my pcmcia usb 2.0 card, ie-enable it, so i could copy win 2k files to the hard drive (i had used fdisk to format the drive)

I now want to install ubuntu on it but forgot where i got the floppy's and no longer have them.

(oh, yeah, i'm going to try this:  [http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/), but... we will see)

SO,

I need:

1.  floppy img to boot and enable usb access
2.  version of linux that will then format the hd and install from the usb.

i imagine it would also run from the usb.

so, can i put linux on a usb from windows and then use that with a floppy boot loader to install to the laptop?
In theory, yes, that's what I was trying to do, but the floppy bootloader that was supposed to support usb booting didn't give that option no matter what, so it didn't work.

---

### Post by BbUiDgZ on 2009-07-15
can you do a [network boot and install?](https://help.ubuntu.com/community/Installation/LocalNet)

---

### Post by Chaos Punk on 2009-07-15
> **BbUiDgZ said:**
> can you do a [network boot and install?]("https://help.ubuntu.com/community/Installation/LocalNet")
I've been having trouble with LAN installs, and I successfully got Debian installed with internet install, so I prefer to stick to that. Plus, those directions are all as if I was in linux, I'm currently running windows on this machine and am trying to install ubuntu on another, so I can't use these instructions, otherwise I'd go ahead and give it a go.

---

### Post by Chaos Punk on 2009-07-15
would it be possible to split the minimal CD onto multiple floppies?

---

### Post by nsche on 2009-08-13
I was able to get a similar system running (celeron 366, 192 mb, no cd, not bootable over usb).  It has windows 98 running on it.  
I got a copy of linld and was able to boot it up on the alternative ubuntu cd (files copied over to the windows file system).  Google for the instructions.  Works fine now, upgraded recently to 9.04.  Performance not so good with so little memory.  Thinking about redoing it with gentoo but we will see.

---

