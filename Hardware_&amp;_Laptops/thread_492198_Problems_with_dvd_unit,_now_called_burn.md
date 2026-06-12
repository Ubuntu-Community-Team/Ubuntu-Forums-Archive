---
title: "Problems with dvd unit, now called burn:///"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by kirbyboy on 2007-07-04
Hi, i think this goes here and not in multimedia, if not, just move it.

Now, when i insert a dvd in my normal dvd reader, the unit is called burn:///(instead of /media/cdrom0, i think), and looks like a dvd recorder because it wants i put files to burn(really).  The problem is that i cannot see the files inside the dvd, i have to put the dvd in my dvd rw unit (/media/cdrom1).  The hardware has not been touched and before worked, what can i do?  may some program have renamed my unit or something?, the only program i have installed for write cd's is k3b and was a lot of time ago i don't run it.

EDIT:
The syslog output is the next:
Jul  4 22:03:22 pedro-desktop kernel: [ 5321.888103] cdrom: This disc doesn't have any tracks I recognize!
Jul  4 22:03:22 pedro-desktop NetworkManager: <debug info>^I[1183579402.268910] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_empty_dvd_rom'). 

And suposses is an empty dvd to burn(in a dvd reader?), and yesterday worked ok, and works ok in my XP partition.

EDIT2:
I could mount it manually with no problems(/dev/hdc) and i can see the dvd, but if unmounted, the unit is again burn:///, i really need help, i don't want to mount it manually each time i want to see a dvd

---

