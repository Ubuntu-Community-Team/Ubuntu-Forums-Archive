---
title: "Upgrade issues."
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by running_rabbit07 on 2009-08-04
Last night I started upgrading my laptop with no working cd drive from 8.04 to 8.10 and it took over three hours.(Not complaining)

This morning I upgraded the same laptop from 8.10 to 9.04 and it was messy.(Not complaining here either, was just bored out of my mind) It was taking forever so I left and came back 2 hours later to find that the thing had overheated and locked up. I restarted and it went past the splash screen to a solid orange and then stopped. Luckily I went in to system restore and made it restore the Jaunty kernel which allowed it to finish the upgrade. 

I must say that JJ and my laptop do not like each other. The graphics start getting lines all over the place and when it starts loading anything the screen starts getting static glitches. 

Is there any way to roll back Xubuntu to 8.10 being it looked and acted great?

If I go into system restore and click on the kernel for Intrepid and restore it, will that be the way to fix it?

There are no files other than system files on this laptop so there is no worry about losing anything. This laptop only gets used by my 5 year old when she feels like playing tux math and I use it with Samba as my file server to hold backups while making changes to my desktop system.

The laptop is an HP Omnibook with 1300MHz processor and 384 MB RAM.

Thank you to all who help.

---

### Post by Sef on 2009-08-04
> Is there any way to roll back Xubuntu to 8.10 being it looked and acted great?

No.  You must do a clean install.

> If I go into system restore and click on the kernel for Intrepid and restore it, will that be the way to fix it?

There is no system restore for Ubuntu.

---

### Post by running_rabbit07 on 2009-08-04
> **Sef said:**
> No.  You must do a clean install.



There is no system restore for Ubuntu.

By system restore I meant interrupting Grub and restoring the kernel that is there for 8.10. When I restored the one for JJ after the lockup there was still the option for the II and HH kernels. I have no means of doing a clean install. The CD ROM doesn't work and the system will not boot from USB. I guess I will have to figure out how to do the network install thing.

---

### Post by snowpine on 2009-08-04
> **running_rabbit07 said:**
> By system restore I meant interrupting Grub and restoring the kernel that is there for 8.10. When I restored the one for JJ after the lockup there was still the option for the II and HH kernels. I have no means of doing a clean install. The CD ROM doesn't work and the system will not boot from USB. I guess I will have to figure out how to do the network install thing.

Yes, you can boot using one of the old kernels. You will be running Jaunty with an old kernel, though, not Intrepid or Hardy. It is worth a try...

---

### Post by running_rabbit07 on 2009-08-04
> **snowpine said:**
> Yes, you can boot using one of the old kernels. You will be running Jaunty with an old kernel, though, not Intrepid or Hardy. It is worth a try...

Just did it and it is working great. No more glitches o lines in the screen. It is running JJ with the old kernel. Saves a lot of work, for now. I will have to set Grub to load this way every time.

---

### Post by running_rabbit07 on 2009-08-04
Is there any way to force Xubuntu while running to start an install disk? Or to tell the system during shutdown to boot the external disk?

I have a new Xubuntu image to install but during startup the machine does not recognize USB devices. I have tried using a Flash drive install and external disk but neither are recognized.

---

### Post by snowpine on 2009-08-04
My netbook doesn't have a CD drive, and I've had pretty good luck with Unetbootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by running_rabbit07 on 2009-08-04
I'll give it a try.

 The selection on that page of all the different distro had me debating trying something new. Maybe another day. I did find it sad that I can't find Xubuntu II ISO anywhere. Only HH and JJ.

---

### Post by snowpine on 2009-08-04
Here you go:

[http://cdimage.ubuntu.com/xubuntu/releases/8.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.10/release/)

---

### Post by running_rabbit07 on 2009-08-04
> **snowpine said:**
> Here you go:

[http://cdimage.ubuntu.com/xubuntu/releases/8.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.10/release/)

Cool, thanks, I found that when using Unetbootin it will download all the way back to 6.x.

---

### Post by running_rabbit07 on 2009-08-04
Unetboot didn't work, there is no selection to boot with USB.

---

### Post by running_rabbit07 on 2009-08-04
Can anybody tell me how to use the sbm.bin file on a floppy to where it will work? I have copied it from the ISO image and placed it on the floppy yet the machine still says it is not a bootable disk.

Edit: SBM stands for Smart Boot Manager.

---

### Post by snowpine on 2009-08-04
> **running_rabbit07 said:**
> Unetboot didn't work, there is no selection to boot with USB.

Unetbootin has two modes; USB and hard drive. If you choose hard drive, you don't need an external USB at all...

---

### Post by running_rabbit07 on 2009-08-04
> **snowpine said:**
> Unetbootin has two modes; USB and hard drive. If you choose hard drive, you don't need an external USB at all...

Thanks for mentioning that. I didn't see it earlier and I just had my laptop in peices trying to get the cd drive to work.  I think the motor is shot. Unetbootin is now installing Xubuntu Intrepid for me. Dude, you rock, thanks for saving my laptop from velocity testing. I am sure Physics would have been correct and lots of plastic would be everywhere, just kidding.

---

### Post by running_rabbit07 on 2009-08-04
Laptop officially trashed until I find a way to boot via LAN. The unetbootin froze when it got to 6% now it has grub error 15.

---

### Post by Shadow Warrior on 2011-05-04
My attempts to install Ubuntu 8.04 on the system described has only resulted in the elimination of the Windows 2K Pro partition that existed on the system when I was lent the system by my sister. From the get go, the system has the following limitations...


[LIST=1]
[*]0122496 KB of RAM
[*]10 GB Hard Drive
[*]Because of its age...
[LIST=1]
[*]071 - CMOS Battery Bad
[*]070 - Real Time Clock Error
[/LIST]
[/LIST]
I haven't had any problems proceeding through the installation process using the CD. The closest I've gotten the system to booting on its own (from the hard drive) is when I somehow was able to select the LILO boot loader instead of grub. Yet, even then, it seemed wanting for a boot option. When the Guided Install selects the grub boot loader instead, it announces it's passing through grub stage 1.5 then one additional step before locking up completely.

The only addtional option that I've put into the install is ACPI=FORCE.

I'm about to turn this ThinkPad into a frisbee, unfortunately, buying another computer at this point isn't an option.

:confused: Please help me retain my sanity!

---

