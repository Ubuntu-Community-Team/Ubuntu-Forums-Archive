---
title: "Netbook Install"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by Redeyes_Gambit on 2009-02-13
}{'lo all! Long time no post!

Ok, so here's the scoop: I recently acquired a nice little second-hand netbook that I'd love to put a flavor of Ubuntu on. The catch is the unit cannot boot to USB, has no floppy drive, and the power supply to the CD-ROM drive is missing.

I could net-boot the device but from reading the docs at [https://help.ubuntu.com/community/Installation/LocalNet]("https://help.ubuntu.com/community/Installation/LocalNet") it looks like a major hassle.

So, my question is can I dump the CD's installation files to the netbook's drive from another machine (I have an IDE-to-USB adapter) in a way that lets me start setup on the netbook directly from the netbook's hard drive?

So, this is kinda what I'm trying to do:

1. Pull netbook's internal hard drive
2. Hook netbook's drive up to 2nd machine via IDE-to-USB adapter
3. Copy installations files to netbook's hard drive
4. Place netbook's hard drive back in netbook
5. Start Ubuntu setup on the netbook from the internal hard drive

Is this possible? I was thinking about using the dd command to just dump an install CD to the hard drive but I'm not sure if there is a more official method.

---

### Post by kerry_s on 2009-02-13
why not just install straight through the usb, just remember to install the boot loader on that drive. just read carefully and know where your putting things.

---

### Post by yey365 on 2009-02-13
unetbootin will create the usb media for the install and dump the files on to the drive.  Reboot, boot from usb and 20 minutes later you're done.

---

### Post by Taemojitsu on 2009-02-13
if it already has Windows on it, you can install from Wubi from inside of Windows, which creates the Linux filesystem inside a file saved inside your Windows partition.

or do what kerry said. you just need to know which device is the netbook's hard drive for both partition/install and grub.

> 
3. Copy installations files to netbook's hard drive
4. Place netbook's hard drive back in netbook
5. Start Ubuntu setup on the netbook from the internal hard drive
This will not work because it would not boot. The MBR of the drive needs to point to the right boot files, and the MBR isn't a file you can copy/paste. You could use a program to alter the MBR, but it's just as easy to just install it via the USB=>IDE.

(besides given the way the LiveUSB works, you wouldn't be able to install Ubuntu to a partition if it was already running 'live' from it, even if you could get it to boot from the install files. CD boot isn't the same as Hard Drive boot, and the Create LiveUSB option doesn't let you select external hard drives >_<)

---

### Post by Redeyes_Gambit on 2009-02-13
Many thanks for the great suggestions! :D

I was aware of unetbootin and was actually talking about earlier today. Lol, for some reason I was mentally overcomplicating the problem and so didn't even think of unet. 

Unfortunately after many attempts unet isn't working. All I get is a blinking cursor at boot on the netbook. I started out with a multi-partition setup so I could boot live on partition 1 then run the install to partition 2. That didn't work (blinking cursor at boot) so I tried repartitioning to a single, thinking that was my problem. Alas, still no dice. 

I'm also not really enthused with installing to the USB drive from a live CD on another machine because Ubuntu would be setting up for hardware other than what is installed on the netbook (correct?) I've done the whole "brain transplant" thing with windows in the past and the OS just never quite forgets it's "past life". I really want to run the setup on the machine it will be installed in. *shrug* I'm too perfectionist I know :P .

---

### Post by kerry_s on 2009-02-13
linux detects what to load at boot, so your good there.
just so you know: linux is modular, it detects and loads the modules you need every boot. so if its not there it's not loaded.

---

### Post by Redeyes_Gambit on 2009-02-13
Ah, well that's good to know! I may try that then. I'll let you know how it goes.

...Worked perfectly! Now I just need to get the resolutions set right.

---

