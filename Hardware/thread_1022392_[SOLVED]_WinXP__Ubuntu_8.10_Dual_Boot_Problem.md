---
title: "[SOLVED] WinXP / Ubuntu 8.10 Dual Boot Problem"
date: 2008-12-26
forum: Hardware
---

### Post by rich1939 on 2008-12-26
My primary computer is a Dell laptop that runs Windows XP (Media Center Edition). I had a spare USB hard drive that I wasn't using, so I decided to install Ubuntu 8.10 on it. The installation was successful...however, I don't want the USB drive to always be connected, so if I unplug it and then reboot, apparently Ubuntu also installed the GRUB loader in my Windows MBR and it hangs with "Error 21".

I'd rather have the laptop _ignore_ the fact that the USB drive isn't connected when it isn't and automatically boot Windows XP.

What can I do (edit, or whatever) to make this happen?

---

### Post by jnw222 on 2008-12-26
are you saying that when the flashdrive is unplugged, you cant boot?

---

### Post by rich1939 on 2008-12-26
> **jnw222 said:**
> are you saying that when the flashdrive is unplugged, you cant boot?

It's not a flash drive. It's an external USB hard drive (100GB)...and, yes, I can't boot! The black screen shows GRUB trying to run something like "step 1.5" (I'm not sure that's accurate), and then says "ERROR 21" on the next line and hangs.

I'm thinking that there must be some way to have the laptop ignore the fact that the USB hard drive isn't connected and then go ahead and boot from the internal hard drive.

I've tried changing the boot order and even if I make the internal hard drive the first choice, the computer won't boot unless the external hard drive is connected.

---

### Post by JCoster on 2008-12-26
It's not an ideal situation but you could just restore the Windows MBR using fixmbr/fixboot from the recovery console and then change the boot order from the BIOS to USB > HDD, so that if the USB drive is present it will automatically load Ubuntu but if not it will boot XP off of the hard disk?

This is assuming of course that your laptop BIOS supports boot from USB.

---

### Post by jnw222 on 2008-12-26
if drive is unpluged-cant boot
if plugged-can boot 

i would create a dedicated grub partition

---

### Post by rich1939 on 2008-12-26
> **JCoster said:**
> It's not an ideal situation but you could just restore the Windows MBR using fixmbr/fixboot from the recovery console and then change the boot order from the BIOS to USB > HDD, so that if the USB drive is present it will automatically load Ubuntu but if not it will boot XP off of the hard disk?

This is assuming of course that your laptop BIOS supports boot from USB.

I'm not sure what the "recovery console" is...but I'm willing to try anything that will do exactly what you're saying. Can you tell me how to proceed?

---

### Post by jnw222 on 2008-12-26
rich's idea requires either to boot off a windows install dics or boot XP and then type either fixboot or fix mbr (not sure maybe both)

t

---

### Post by JCoster on 2008-12-26
> **rich1939 said:**
> I'm not sure what the "recovery console" is...but I'm willing to try anything that will do exactly what you're saying. Can you tell me how to proceed?

To enter the recovery console and repair your MBR with instructions [here]("http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/").

(Make sure your primary boot device is your CD drive)

Then just re-order your boot devices to make it go CD > USB > HDD and you're done!

Let me know if you get stuck...

---

### Post by rich1939 on 2008-12-26
> **JCoster said:**
> To enter the recovery console and repair your MBR with instructions [here]("http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/").

(Make sure your primary boot device is your CD drive)

Then just re-order your boot devices to make it go CD > USB > HDD and you're done!

Let me know if you get stuck...

Apparently the link you sent was for a program that scans my PC and reports any problems it finds...and then wants me to pay for them to fix the problems. It didn't find anything wrong with the MBR.

I booted with my Windows CD and used the **Repair** facility console to enter the **fixmbr** command. It did indeed repair my MBR so that Windows XP now boots properly, but for some reason, even though "Boot from USB device" was allowed, it refused to do so.

I believe that when I installed Ubuntu 8.10 onto my external USB hard drive, it put a crucial part of the GRUB loader onto my internal (i.e., C:/) drive, so that the external hard drive doesn't now appear to be bootable!

I'm not sure how to cure this problem. If there is some way to make the external hard drive bootable, I'd like to do that. My current "Boot Order" settings are CDROM/USB Device/Internal HD.

---

### Post by caljohnsmith on 2008-12-26
Rich1939, you probably need to install Grub to the MBR of your USB drive, because Grub was previously in the MBR of your Windows drive. How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Also do:
```
sudo fdisk -l
```
And check that one of the primary partitions on your USB drive has the boot flag set (* under the "boot" heading); if not, you should set the boot flag on one of the primary partitions by doing:
```
sudo sfdisk -A1 /dev/[COLOR="Blue"]sdb[/COLOR]
```
And replace "sdb" if the USB drive is a different device. Then reboot and see if you can boot from the USB drive, and if not, please let me know what happens.

---

### Post by rich1939 on 2008-12-26
> **caljohnsmith said:**
> Rich1939, you probably need to install Grub to the MBR of your USB drive, because Grub was previously in the MBR of your Windows drive.

That sounds right to me. I'm going to give that a try and will let you know whether it solves my problem.

---

### Post by rich1939 on 2008-12-26
[QUOTE=caljohnsmith;6441919]Rich1939, you probably need to install Grub to the MBR of your USB drive, because Grub was previously in the MBR of your Windows drive. How about booting your Live CD...QUOTE]

**That was the definitive answer!**

Thanks a bunch. I booted the live CD, ran the commands you suggested, also found that the '*" was **not** present for my sdb drive, and set it, as you suggested.

Now my external hard drive boots Ubuntu when it's attached, and the internal hard drive boots Windows XP when the external drive is not attached.

Bravo!

I'm going to mark this one solved!!!

Thanks a bunch. I **love** these forums.

---

### Post by caljohnsmith on 2008-12-26
Glad to hear the Ubuntu drive is booting OK now, Rich; cheers and have fun with Windows and Ubuntu. :)

---

### Post by pmenefee on 2009-01-02
> **caljohnsmith said:**
> Rich1939, you probably need to install Grub to the MBR of your USB drive, because Grub was previously in the MBR of your Windows drive. How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Also do:
```
sudo fdisk -l
```
And check that one of the primary partitions on your USB drive has the boot flag set (* under the "boot" heading); if not, you should set the boot flag on one of the primary partitions by doing:
```
sudo sfdisk -A1 /dev/[COLOR="Blue"]sdb[/COLOR]
```
And replace "sdb" if the USB drive is a different device. Then reboot and see if you can boot from the USB drive, and if not, please let me know what happens.

I had installed 8.10 to my usb hdd and could not get it to boot until I followed your instructions.  Works like a charm now.  I looked back through lots of your posts and saw how many people you have helped...very impressive.  Many thanks and keep up the good work!!
Pete

---

### Post by award982 on 2009-01-02
> **pmenefee said:**
> I had installed 8.10 to my usb hdd and could not get it to boot until I followed your instructions. Works like a charm now. I looked back through lots of your posts and saw how many people you have helped...very impressive. Many thanks and keep up the good work!!
Pete
 
this is so simple ...what tha hell im such a noob

---

