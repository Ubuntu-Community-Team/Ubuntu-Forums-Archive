---
title: "Ubuntu won't start when USB connected"
date: 2004-11-30
forum: Hardware &amp; Laptops
---

### Post by danpre on 2004-11-30
Ubuntu doesn't want to start
(it stops on Uncompressing Linux... Ok, booting the kernel.)
when I have DVDwritter connected via USB.

When I turn off DVD writter or diconnect it - everything goes ok.

When I connect or turn on DVD writter after log in - everything goes ok, no problems with mounting or burning.

Not a big problem but I have got pretty confused today morning when my Ubunt didn't want to start.

danpre
------
DVDwritter is:
TOSHIBA  DVD -R/+R A550U (USB 2.0)

Computer is:
Laptop Maxdata ECO 3150X
Celeron 2.4GHz
Chipset Intel 845GV
RAM 512 MB
Intel® 82845 GV max 64MB DDR RAM, AGPx4
VIA AC 97 Audio
HDD 20 GB
DVD/CD-RW Combo drive Eco 3200X

---

### Post by bmichel on 2004-11-30
I've got the same problem with external USB 20Go disk. I have to disconnect it to boot .

---

### Post by AsteriskNix on 2004-11-30
Same here, my only cdrom is an  externally connected usb2 one. I have a Dell D400 and wanted to install ubuntu on a slice of the drive. It detects and boots, but after selecting the install ( i've tried all the valid options in the list except the acpi one )

I am wondering if it's a kernel issue, not an ubuntu issue, since I have the identical problem with knoppix and gnoppix.

( I REALLY WANT LINUX ON THIS LAPTOP WORK IS FORCING ME TO USE XP AAAHH!! )

help me please :)

---

### Post by arctic on 2004-11-30
have you already tried editing the /etc/fstab file, adding some entries for your usb-devices? maybe that could prevent the "lockup". ;)

---

### Post by randy on 2004-11-30
At what point in the boot process does the lockup occur?

---

### Post by danpre on 2004-12-01
randy

Last message is see is:

Uncompressing Linux... Ok, booting the kernel

and that is all - computer stops responding

[QUOTE=randy]At what point in the boot process does the lockup occur?[/QUOTE]

---

### Post by AsteriskNix on 2004-12-01
And on mine, after uncompressing the kernel it says...

loading cdrom..
enabling dma for /dev/hd?[0-9]
then my hdd with some numbers then
Warning unable to find base module!
Can't find Morphix filesystem

dropping into busybox shell

( this is from the gnoppix cd which is ubuntu based but as I pointed out above, I get similar errors with ubuntu warty, and knoppix as well )

I've even chosen "boot from external usb connected cdrm v1 device and v2 device.

---

### Post by AsteriskNix on 2004-12-02
...



<crickets>

---

### Post by AsteriskNix on 2004-12-07
bump again. I'm seeing this issue on multiple forums now, any answers yet??

---

### Post by rcrcomputing on 2005-02-22
No answers, but the same thing happens if my SIIG raid card is in the machine.  :(

---

### Post by alastair on 2005-02-22
The problem is ... no output messages from the boot.

Try removing any "quiet" option from grub - so we can see where things stop i.e.

At boot - ESC (I think) to get to grub, then select your kernel and "e" to edit the command for boot.
Remove the "quiet" kernel argument - enter to boot ...

See if more is printed and report back.

---

### Post by DrSkrud on 2006-10-02
I have a similiar problem, except that Ubuntu will boot properly if I have my external LaCie hard drive plugged in -- it will refuse to boot if my iPod is plugged in.

---

