---
title: "Selecting OS when booting please help"
date: 2008-08-08
forum: General Help
---

### Post by miguelbuenca on 2008-08-08
I've just installed ubuntu 8.04 successfully in my desktop computer with Vista installed first. It booted normally but when the choice for OS opened up the keyboard up and down arrow is not responding. Is there anything I missed. Please help. 

System config:

Processor Core 2 Dou 2.4ghz. 
Mohter board Gigabyte S series GA EP31 -ds3l
Videocard Nvidea512

---

### Post by Sycron on 2008-08-08
What keyboard do you have ? I mean USB or PS/2 ?

---

### Post by brujoand on 2008-08-08
When the you can see the countdown to "loading grub" in white letters on black screen.. Press esc, and select the OS you want from the list.

 :)

---

### Post by Mgiacchetti on 2008-08-08
> **GrimmVarg said:**
> When the you can see the countdown to "loading grub" in white letters on black screen.. Press esc, and select the OS you want from the list.

 :)

he can see the selections, just cant move the cursor to each one.

See, Ubuntu defaults to no hidden grub.

---

### Post by dje on 2008-08-08
> **Mgiacchetti said:**
> he can see the selections, just cant move the cursor to each one.

See, Ubuntu defaults to no hidden grub.

if you have another operating system ;)

---

### Post by brujoand on 2008-08-08
Oh okay, I missed that part.. I'm all blank then.

---

### Post by Limbic on 2008-08-08
If the problem is just that you're unable to select anything in the Grub menu (but you can see the menu just fine, and the countdown clock is ticking down like normal), it may just be a matter of enabling BIOS support for USB in your BIOS.

On a reboot, go into your BIOS and look for an "Integrated Peripherals" setting or something like that.  There should be a keyboard setting and you can choose between BIOS and OS settings.  On my Abit IP35-e, the default setting is OS, so I had the exact same problem when I first installed Ubuntu.

---

