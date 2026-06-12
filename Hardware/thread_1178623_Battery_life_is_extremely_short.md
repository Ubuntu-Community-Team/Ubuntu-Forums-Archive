---
title: "Battery life is extremely short"
date: 2009-06-04
forum: Hardware
---

### Post by the_fury on 2009-06-04
Hi all, I'm running Ubuntu Jaunty, 9.04 with all the latest kernel and updates. 

I'm using a Sony VAIO VGN-FZ240E laptop, and I've noticed that ever since I switched from Vista to Linux, my battery life ranges from the 5 to 15 minutes.

I was just wondering whether or not this is because of my laptop, the battery, or perhaps if there is something I can do to lengthen the battery life. (It's very annoying when I can't do anything without being plugged in.)

So, is it my fault? And is there something I can do to fix it?

Thanks in advance.

---

### Post by utnubuuser on 2009-06-04
yeah it's your fault...  

must be something in the acpi not doing it's job.  There are probably acpi settings peculiar to that make/model laptop.  Have you tried googling: yourmake/yourmodel ubuntu?

I seem to recall seeing battery life threads for sony's.  

Try googling "sony battery life ubuntu", or "vaio battery life ubuntu"

---

### Post by T500 on 2009-06-06
I have the same problem: with Windows the battery works for something less than 7 hours
with ubuntu 9.04 no more than 2 hours and half as i posted some days ago. Ubuntu still needs 29 Watts, Windows only 11 :-( 

Battery is ok of course (more /proc/acpi/battery/BAT0/state and more  /proc/acpi/battery/BAT0/info).

I've (of course enabled laptop mode adding in /etc/default/acpi-support ENABLE_LAPTOP_MODE=true) removed compiz, decreased the cpu speed, tried the powertop advices (disabling bluetooth, usb and dvd  and modified the VM writeback), modified some conf files(cd /etc/laptop-mode/conf.d),  i only gained half an hour more (from 2 hours to 2 hours and half about). But it's still 2.8 times more consuming than windows.
With the previous versions of linux it was the opposite.

I also saw the Italian Ubuntu forum with a lot of people with the same problem. 

Some new advices?

---

