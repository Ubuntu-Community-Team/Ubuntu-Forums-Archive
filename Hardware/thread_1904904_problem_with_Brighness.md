---
title: "problem with Brighness"
date: 2012-01-05
forum: Hardware
---

### Post by mohammad110 on 2012-01-05
hi
1- i'm now leave Windows and migrate to Ubuntu 11.10, 64bit on laptop (Lenovo Y450).
Fn doesn't work for change Brightness.
i searched more but i can't fix this problem.

2- Also how i can understand used which hardware on my laptop. because i don't exactly my graphic brand (Intel or Nvidia) 

if doesn't any way to solve this problem please suggest to me for choice another Linux version like fedora or ...

sorry for my spelling...
Thank's

---

### Post by mohammad110 on 2012-01-06
from last night i reading all post about intel graphic problem on 11.10. i think this version totally has got problem with Intel VGA ...
what's your idea ? we must back to 11.4 ?
please tell us applied solution

---

### Post by Toz on 2012-01-06
To identify your video card, open a terminal window, type in the following command, and post back the results:
```
sudo lspci -vnn | grep -A10 VGA
```

If you have an nvidia card, make sure the proprietary drivers are installed and have a look at: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/540112]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/540112")

---

### Post by mohammad110 on 2012-01-06
> **Toz said:**
> To identify your video card, open a terminal window, type in the following command, and post back the results:
```
sudo lspci -vnn | grep -A10 VGA
```

If you have an nvidia card, make sure the proprietary drivers are installed and have a look at: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/540112]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/540112")

thank's for your answer

output: 
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device [17aa:3a02]
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at f4000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 3
	Kernel modules: i915


```

---

### Post by Toz on 2012-01-06
Yes, its an integrated intel video card.

Try adding **acpi_backlight=vendor** to your kernel boot options to see if that gives you control of your function keys and screen brightness. Follow these instructions: [[https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot")] to test to see if it works. 

If it does, you can make it permanent by following the instructions here: [[https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2]("https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2")] (edit /etc/default/grub to add the parameter then run sudo update-grub)

---

### Post by Basher101 on 2012-01-06
i have a laptop with exactly the same graphical onboard chipset...i will link my fix here once i found it

---

### Post by Basher101 on 2012-01-06
[failed double post]

---

### Post by Basher101 on 2012-01-06
found it > type in a terminal: ```
sudo gedit /etc/rc.local
``` and there you will see at the very most bottom a red colored [COLOR="Red"]EXIT[/COLOR]. Just above that "exit" type the command ```
setpci -s 00:02.0 F4.B=00
``` and save the settings. Next file you will have to edit is your Grub config file. Type into a terminal ```
sudo gedit /etc/default/grub
``` there you will see different settings. Now look for the line that looks like this: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and add "acpi_osi=Linux" at the end so that the line looks like this after editing:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Green"]acpi_osi=Linux[/COLOR]"

this should fix your problem. the only thing that got BROKEN is the indicator app that shows you that "bar" of the brighntess and that it is reversed (UP arrow increses brightness and DOWN decreses the brightness). But this is a price i gladly pay to change the brightness. 

If you do not want to make those "permanent" changes, you can also just adjust it by command with ```
sudo setpci -s 00:02.0 F4.B=[COLOR="Red"]XX[/COLOR]
``` where in XX you replace it with HEX code (reaching from 00 = 0 ([COLOR="DarkOrange"]brightest[/COLOR]) to FF = 255 ([COLOR="Navy"]darkest[/COLOR]))


regards

---

### Post by mohammad110 on 2012-01-06
thank's a lot Basher101 :p:p
finally i was comfortable after a week ...
your solution fixed Lenovo ideapad Y450 brightness ...

thank you very much :p:D:p:D:P:p

---

### Post by Toz on 2012-01-07
I'm curious. Did the acpi_backlight=vendor kernel parameter work?

---

### Post by mohammad110 on 2012-01-07
> **Toz said:**
> I'm curious. Did the acpi_backlight=vendor kernel parameter work?

i just following the eighth post.
Also can i set the number for average brightness when ubuntu coming up ?
because i don't see login page and i enter of maintaining password. the LCD totally dark !

---

### Post by mohammad110 on 2012-01-07
and when my computer wake up or exit from standby the brightness is dark ...

---

### Post by Basher101 on 2012-01-07
> **mohammad110 said:**
> and when my computer wake up or exit from standby the brightness is dark ...

have the same problem on my laptop, no permanent fix for that, just hit FN + Down..

also, i found a way where you lock the backlight upon startup. When in the Grub Bootloader, max out the brightness with FN + Up (it will be locked on that brightness until you reach the login screen where the /etc/rc.local script takes effect).

---

### Post by aeronutt on 2012-01-07
> **Basher101 said:**
> have the same problem on my laptop, no permanent fix for that, just hit FN + Down..

also, i found a way where you lock the backlight upon startup. When in the Grub Bootloader, max out the brightness with FN + Up (it will be locked on that brightness until you reach the login screen where the /etc/rc.local script takes effect).

This fix / script worked for me to set screen brightness at login (note that it's per account at login, not at boot.)

[http://blog.ishans.info/2011/09/25/set-brightness-automatically-at-the-startup-in-linux/](http://blog.ishans.info/2011/09/25/set-brightness-automatically-at-the-startup-in-linux/)

---

### Post by Basher101 on 2012-01-07
> **aeronutt said:**
> This fix / script worked for me to set screen brightness at login (note that it's per account at login, not at boot.)

[http://blog.ishans.info/2011/09/25/set-brightness-automatically-at-the-startup-in-linux/](http://blog.ishans.info/2011/09/25/set-brightness-automatically-at-the-startup-in-linux/)

dunno about that, i actually discovered the brightness in grub by accidently pushing those buttons (thank god i did) thats how i was able to make the install at all..(was using a small flashlight and could see that the screen had colors, but no backlight..)

---

