---
title: "Floppy disk drive not recognised in v 8.10"
date: 2008-11-16
forum: Hardware
---

### Post by lesliek on 2008-11-16
1. I boot up with my BIOS set to boot first from my floppy disk drive and with a bootable floppy disk (tomsrtbt) in my floppy disk drive. The floppy disk drive works and the boot up process completes satisfactorily.

2. I boot up with my BIOS set to boot first from my optical drive and with a Knoppix DVD (v 5.3.1) in my optical drive. When I get to the desktop, it shows my floppy disk drive. I insert a non-bootable floppy disk into my floppy disk drive and click on "mount". The floppy disk mounts.

3. I boot up with my BIOS set to boot first from my hard disk drive, which has Ubuntu v 8.10 on it. When I get to the desktop, I can't find my floppy disk drive.

4. Steps 1 and 2 tell me that my floppy disk drive works and step 2 tells me that my floppy disk drive works with at least one Linux distribution. I don't know enough though to know what I should be doing to make my floppy disk drive work under Ubuntu v 8.10.

5. I'd be grateful for some guidance. Thank you for reading this.

Leslie

EDIT: I discovered that the floppy module's no longer started by default. After I started the floppy module, I had my floppy drive.

---

### Post by pprjack on 2008-12-13
Ok, I hate to have to ask but, how do you start the floppy module and how do you get the floppy to automount nicely like the CD/DVD drive with out having to think about it and redo it every time you reboot the PC. I just think it would be nice for us to be able to use all the fantastic legacy devices we have on our PCs if we happen to be lucky enough to still have them.

Thanks for reading my question,
John :confused:

---

### Post by lesliek on 2008-12-13
Sorry, pprjack, not to be confident, but ...

My recollection is that you can load the floppy module by typing in the terminal:

sudo modprobe floppy

pressing Enter, then entering your password when prompted and pressing Enter again.

If that worked, when you afterwards type in the terminal:

lsmod | grep floppy

and press Enter, you should get output that discloses that the floppy module's been loaded.

That should work on a time-by-time basis.

To make sure that the floppy module loads on boot-up, I think you have to edit the file /etc/modules with a text editor to add floppy.

I hope the above's right. If not, I hope someone will correct me.

Leslie

---

### Post by cliff58 on 2008-12-13
I hopesomeone can confirm what lesliek says. I have the same problem, and being slightly noobish around Linux yet, I don't want to go editing files and doing soething wrong...8-[

---

### Post by pprjack on 2008-12-16
Thanks Leslie,

I have tried your suggestions, everything up to editing /etc/modules works. After editing /etc/modules to add floppy my CD DVD drive does not work. Removing the edit to see if that allows the DVD drive to work again.

John

---

