---
title: "Dell 600m laptop lid stanby"
date: 2005-02-21
forum: Hardware &amp; Laptops
---

### Post by goodtone on 2005-02-21
I had the other post as well, I am new to linux, i was just wondering if someone knew  site that offered a fix for Ubuntu's power management  for Dell 600m laptop lid. I close the lid and the sys freezes...

thanks

[email]goodtone@gmail.com[/email]

---

### Post by poofyhairguy on 2005-02-21
[QUOTE=goodtone]I had the other post as well, I am new to linux, i was just wondering if someone knew  site that offered a fix for Ubuntu's power management  for Dell 600m laptop lid. I close the lid and the sys freezes...

thanks

[email]goodtone@gmail.com[/email][/QUOTE]

Yep. I use APM instead of ACPI. Search on the forum for how to do it (its pretty easy). Now standby works better than in Windows.

---

### Post by GilGalad on 2005-02-21
I had the same problem with Warty (D800 here). There are several posts discussing it. 
I recall that the problem with the computer freezing when closing the lid was with the kernel version. Update to the newest one (just saw that 2.6.10 has been backported to Warty).

---

### Post by Vesperan on 2005-02-23
Hi Goodtone,
the Ubuntu Wiki holds a solution for your problem - it works for me on my 600m.

[ Dell Laptop Suspend Fix](http://www.ubuntulinux.org/support/documentation/howto/dellat/view?searchterm=dell%20laptop%20suspend)

Hope it works for you

---

### Post by Vesperan on 2005-02-25
..and just to prove myself wrong, after doing a Warty reinstall, the laptop fix no longer works for me and it crashes the laptop.

---

### Post by Kokosnuss on 2005-02-27
I am experiencing the same problem with an Inspiron 8100 and I am very interested in a solution to this...
Well, all I can say is that the "nolapic" thing doesn't work...
Are there any other ideas?

Greetz
Felix

---

### Post by sargek on 2005-03-10
Well, I have a Gateway 4024GZ and my system freezes when the lid is closed as well. I have tried passing "nolapic" to the kernel at boot and that doesn't work.  The screen blanks (shuts off) from the screensaver in X and that works fine, but if I close the lid, the only thing that will wake it up is to hit the power button, in which case it forcefully powers down. This happens in X and at the command line. Frustration!

---

### Post by bnutting on 2005-04-14
Not  sure if anybody is still paying attention to this but I fixed my Dell Inspiron 5000 lid problem. I pass : apm=on acpi=off to the kernel and everything seems fine with Hoary now.

---

### Post by DHLawrence on 2005-06-29
What are the steps in doing that? I have a 600m and just installed Ubuntu this week, and would like to avoid this problem. I was practising with Linux on a Toshiba, whenever I went Log Out-->Hibernate it would hang on the screen saver and wouldn't actually hibernate.

---

