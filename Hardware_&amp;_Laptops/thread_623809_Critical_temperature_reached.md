---
title: "Critical temperature reached"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by ruhollah on 2007-11-26
On my new laptop  (Compaq 6910p), I have installed Ubuntu 7.10.  As soon as I log in and start a simple window, firefox for example, it goes to shitting down, due to “reaching critical temperature”.
Following error is produced:
Critical temperature reached (127 C)...

I did google a lot! It seems to be very common on these new laptops. The spec of laptop:
 Core2Du, graphic ATI Mobility Radeon X2300

Any idea? 
Is there any suggestion to disable acpi?

---

### Post by scrooge_74 on 2007-11-26
you can go into grub and put acpi=off at the end of the line for the kernel you are using

Please someone correct me if I said an incorrect thing.

Also maybe check if you could use another distro

---

### Post by ruhollah on 2007-11-26
I did this, and then I ran: 'sudo update-grub'

But it didnt work!

By the way, I updated my ATI graphic driver twice: fist, by using  Synaptic package manager; and after that, I used envy. 
But the problem still EXIST!
Any suggestion is welcome and appreciated

---

### Post by ruhollah on 2007-11-26
[I][COLOR="Red"][B]Is there anyone there to help? I am in urgent situation!!!
PLEASE participate[/B][/COLOR][/I]

---

### Post by scrooge_74 on 2007-11-26
> **ruhollah said:**
> I did this, and then I ran: 'sudo update-grub'

But it didnt work!

By the way, I updated my ATI graphic driver twice: fist, by using  Synaptic package manager; and after that, I used envy. 
But the problem still EXIST!
Any suggestion is welcome and appreciated

Did you reboot after updating GRUB?

You should check to see if another distro works better on that PC

---

### Post by ruhollah on 2007-11-28
Yes! I rebooted after upgrading the grub. 
I also tried CentOS5_x86_64 as well, but it didnt work, too.

---

### Post by ruhollah on 2007-11-28
:( please help :confused:

---

