---
title: "Dell Inspiron 3847 - Mouse/Keyboard intermittently unresponsive on boot"
date: 2014-06-26
forum: Hardware
---

### Post by sorceror171 on 2014-06-26
My parents got a new computer - Dell Inspiron 3000 class, Core i5, 8GB, etc. I put in a second hard drive and installed Xubuntu 14.04. I've had fun getting it to work with UEFI, and the Windows 8.1 it came with removing Grub, and so forth - finally had to disable Secure Boot. But at this point *almost* everything works. (Thankfully, I've got them using Linux for everything - particularly web and email - except a couple Windows-only programs and games.)

But, sometimes, when the computer boots up to Xubuntu, the login screen comes up but doesn't respond to the mouse and keyboard. The system itself is running, but even unplugging and plugging in the devices doesn't get them working. The only option is to hit the power button, let the computer shut down and reboot, and hope the mouse and keyboard work next time. Only once has it failed twice in a row, but it worked the third time. If they work on boot, I've never seen them stop working after that.

I suspect some race condition in, say, ACPI assigning interrupts or something. Any hints on logs should I look at or settings should I examine?

---

### Post by setaou on 2014-09-15
I have had this problem on the same hardware (Dell Inspiron 3847).
Upgrading the kernel to 3.16.2 (using the "mainline" packages) seems to have solved it.

---

### Post by Matt_Sandefur on 2015-01-11
I am also experiencing the same issue on Dell Inspiron 3847 using the related Linux Mint 17 version.  Did anyone find a solution?

---

### Post by mörgæs on 2015-01-11
The poster above you did.

---

### Post by Matt_Sandefur on 2015-01-11
Sorry, wrong question.  Is this a recognized issue with the older 3.13 kernels?

---

### Post by mörgæs on 2015-01-11
I don't know. 
As a rule of thumb I always recommend using the latest of software, especially on new hardware.

---

