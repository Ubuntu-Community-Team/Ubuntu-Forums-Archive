---
title: "My Toshiba laptop won't shutdown"
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by Lingxiao on 2005-07-13
I installed ubuntu 5.04 on my toshiba satellite 3000 laptop. But it won't shutdown by Clicking the shutdown button in Gnome, or the shutdown command in terminal. My laptop just freezes right after the screen turns black. What's wrong with it? Thank anybody here who can help me with such a problem.

---

### Post by varunus on 2005-07-13
What is the output of "lsmod"?  Do you see the text saying that processes are being shut down before the screen freezes?

---

### Post by springshades on 2005-07-14
Try going to run level 3, in lilo you can do that by hitting escape when the boot loader first shows up and then typing in the normal thing you boot to, then a space, then 3... in most cases it would look like

linux 3

Now, log in and try the halt command. If it gets all the way to a power down message and then simply stops, it means that you don't have ACPI working properly. ACPI is the power management for most laptops. If that is the case, then shutting down by just holding your power button at the end won't hurt anything. Your computer just doesnt have the ability to power itself down on its own.

ACPI is very important for a laptop, so it's something you'll probably want to look into. It contributes to battery life and keeping your computer from overheating.

---

### Post by varunus on 2005-07-15
ACPI is supported on Toshiba Satellite's from what I've seen, so its strange that it isn't working for you, however.  Maybe try loading the ACPI modules manually?

---

### Post by ruddyconsult on 2005-08-12
This thread is the closest answer I can find to my problem with my IBM Thinkpad X40 laptop.

As recommended below, I have been "shutting down by just holding your power button at the end". The need to do that only arises when I am exiting XP. I get a blue screen briefly, then the "IBM" screen, before the machine gets up the boot loader again.

What should I do to the Grub configuration so that XP can shut the machine off?

Thanks,
Thomas


[QUOTE=springshades]Try going to run level 3, in lilo you can do that by hitting escape when the boot loader first shows up and then typing in the normal thing you boot to, then a space, then 3... in most cases it would look like

linux 3

Now, log in and try the halt command. If it gets all the way to a power down message and then simply stops, it means that you don't have ACPI working properly. ACPI is the power management for most laptops. If that is the case, then shutting down by just holding your power button at the end won't hurt anything. Your computer just doesnt have the ability to power itself down on its own.

ACPI is very important for a laptop, so it's something you'll probably want to look into. It contributes to battery life and keeping your computer from overheating.[/QUOTE]

---

### Post by luca_linux on 2005-08-12
Just pass the kernel parameter "nolapic" at boot.
Anyway, is there a toshiba module loaded? Just type "lsmod" to see that.

---

### Post by Marrea on 2005-08-12
I have a related problem.  I installed Ubuntu on my Toshiba 1800 laptop and whereas it will shutdown, it won't restart.  It gets as far as shutting everything down and then says something like "restarting system", whereupon the screen goes dark, but the laptop is still running and I have to turn it off with the power switch.  I must have tried everything I can think of as an option at the end of the kernel line in Grub !!  Nothing makes any difference.

Strange, isn't it?

If I want to reboot, I just have to use shutdown and then restart manually.

---

### Post by GavinX on 2005-08-12
[QUOTE=Lingxiao]I installed ubuntu 5.04 on my toshiba satellite 3000 laptop. But it won't shutdown by Clicking the shutdown button in Gnome, or the shutdown command in terminal. My laptop just freezes right after the screen turns black. What's wrong with it? Thank anybody here who can help me with such a problem.[/QUOTE]
Follow the instructions which I posted in this  [http://www.ubuntuforums.org/showthread.php?t=55515](http://www.ubuntuforums.org/showthread.php?t=55515) thread and you should be ok.

Cheers, 
GavinX

---

### Post by Marrea on 2005-08-12
[QUOTE=GavinX]Follow the instructions which I posted in this  [http://www.ubuntuforums.org/showthread.php?t=55515](http://www.ubuntuforums.org/showthread.php?t=55515) thread and you should be ok.

Cheers, 
GavinX[/QUOTE]

Hi GavinX

Those instructions obviously work for a Toshiba that won't shut down.   Any idea what might work for a Toshiba that won't reboot, as in my case?   Actually, **acpi=off** is one of the many options I have tried in the hope it might solve the reboot problem, but no joy.

---

### Post by GavinX on 2005-08-12
[QUOTE=Marrea]Hi GavinX

Those instructions obviously work for a Toshiba that won't shut down. Any idea what might work for a Toshiba that won't reboot, as in my case? Actually, **acpi=off** is one of the many options I have tried in the hope it might solve the reboot problem, but no joy.[/QUOTE]
Hi Marrea,

I'm not certain about the reboot situation. However, I will do some reearch and see what come of it. I will post shortly.

GavinX

---

### Post by Marrea on 2005-08-13
[QUOTE=GavinX]Hi Marrea,

I'm not certain about the reboot situation. However, I will do some reearch and see what come of it. I will post shortly.

GavinX[/QUOTE]
 Hi GavinX

Many thanks.  I'll wait and see if you come up with anything - but don't spend too much time researching just on my account !

---

