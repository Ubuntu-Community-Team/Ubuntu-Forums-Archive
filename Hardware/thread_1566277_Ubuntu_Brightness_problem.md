---
title: "Ubuntu Brightness problem"
date: 2010-09-02
forum: Hardware
---

### Post by RuneLacroix on 2010-09-02
Hey.

I recently changed from from Open Suse to Ubuntu. 
Since i installed Ubuntu, the highest level of Brightness isn't satisfying. Using Open Suse (and windows before that) the highest level of brightness was higher than in Ubuntu. The brightness control is working fine.
Im using a Asus Eee pc 1008p (netbook). 
Is there any way to overextend the brightness?

Kind Regards. Rune

---

### Post by RuneLacroix on 2010-09-03
Nobody have any help?

---

### Post by pavolzetor on 2010-09-03
hi, please post output of this command ```
sudo cat /sys/class/backlight/acpi_video*/max_brightness
```

---

### Post by RuneLacroix on 2010-09-03
> **pavolzetor said:**
> hi, please post output of this command ```
sudo cat /sys/class/backlight/acpi_video*/max_brightness
```

```
runelacroix@Shakti:~$ sudo cat /sys/class/backlight/eeepc/max_brightness
15
runelacroix@Shakti:~$
```

Can i change it?

---

### Post by RuneLacroix on 2010-09-03
* its a read only file...

---

### Post by pavolzetor on 2010-09-03
for max. brightness try this command
```
sudo sh -c 'echo 15 > /sys/class/backlight/acpi_video0/brightness'
```

---

### Post by RuneLacroix on 2010-09-03
Nothing happens...

Dont you think it could help to change the number in the file max_brightness? I just dont know how... since its a read only file...

---

### Post by pavolzetor on 2010-09-03
please, post output of this command ```
ls -l  /sys/class/backlight/acpi_video0/
```

---

### Post by RuneLacroix on 2010-09-03
Since i installed the eee control daemon the folder is called eeepc not 
acpi_video0
```
runelacroix@Shakti:~$ ls -l  /sys/class/backlight/eeepc/
total 0
-r--r--r-- 1 root root 4096 2010-09-03 18:51 actual_brightness
-rw-r--r-- 1 root root 4096 2010-09-03 19:32 bl_power
-rw-r--r-- 1 root root 4096 2010-09-03 19:34 brightness
lrwxrwxrwx 1 root root    0 2010-09-03 18:51 device -> ../../../eeepc
-r--r--r-- 1 root root 4096 2010-09-03 19:34 max_brightness
drwxr-xr-x 2 root root    0 2010-09-03 18:51 power
lrwxrwxrwx 1 root root    0 2010-09-03 18:51 subsystem -> ../../../../../class/backlight
-rw-r--r-- 1 root root 4096 2010-09-03 18:51 uevent
runelacroix@Shakti:~$ 

```

---

### Post by pavolzetor on 2010-09-03
hmm, as you can see, you have maximum level

---

### Post by RuneLacroix on 2010-09-03
Cant i change that? I know the hardware can take more... Since it was lighter when i used Open Suse

---

### Post by pavolzetor on 2010-09-03
try this (sets level to max) ```
sudo sh -c 'echo 15 > /sys/class/backlight/eeepc/brightness'
```
and then try another level e.g. "5" to check, if it works

and why do you replace ACPI with this "special" acpi interface?

also I am idiot, sorry

---

### Post by RuneLacroix on 2010-09-03
I changed it because with the eee control daemon, can make some specific eee pc hot keys work...

Im able to change the brightness level with this code... but that doesn't help me, since i want to change the highest possible brightness, so that i becomes higher....  It must be possible :)

???

---

### Post by RuneLacroix on 2010-09-03
```
runelacroix@Shakti:~$ sudo sh -c 'echo 20 > /sys/class/backlight/eeepc/max_brightness'
sh: cannot create /sys/class/backlight/eeepc/max_brightness: Permission denied
runelacroix@Shakti:~$ 

```

Would it be possible to change the max_brightness file?

---

### Post by pavolzetor on 2010-09-03
okey, how much steps do you have? try it by command

---

### Post by RuneLacroix on 2010-09-03
? Which command... Im very new with ubuntu... So i have no idea about what to do :)

---

### Post by pavolzetor on 2010-09-03
Have you tried this [http://forum.eeeuser.com/viewtopic.php?pid=731466](http://forum.eeeuser.com/viewtopic.php?pid=731466) ? (your post)

in Open Suse, did you use ACPI modification?

---

### Post by RuneLacroix on 2010-09-03
Yes... But nothing happens... I will ask in that forum for more help

---

### Post by RuneLacroix on 2010-09-03
> in Open Suse, did you use ACPI modification? 	

Yes... but the brightness was low i Ubuntu even before i installed Eee control

---

### Post by pavolzetor on 2010-09-03
I will try find something on Internet

Could you provide your data there, please?

[http://ubuntuforums.org/showthread.php?p=9802030#post9802030](http://ubuntuforums.org/showthread.php?p=9802030#post9802030)

---

### Post by pavolzetor on 2010-09-03
hmm, try min and max steps via command line, and get kernel version in opensuse (you can try it viac live CD)

---

### Post by pavolzetor on 2010-09-05
Hi, try set up max brightness in grub and then boot into ubuntu

---

### Post by RuneLacroix on 2010-09-05
How?

---

### Post by pavolzetor on 2010-09-05
I don't know, I read it on bugzilla.kernel.org

Maybe, try FN keys

---

### Post by pavolzetor on 2010-09-05
please, provide me output of ```
lspci
```

---

### Post by RuneLacroix on 2010-09-05
```

runelacroix@Shakti:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
runelacroix@Shakti:~$
```

---

### Post by pavolzetor on 2010-09-05
sudo setpci -s 00:02.0 f4.b=ff

Has grub brightness worked?

---

### Post by RuneLacroix on 2010-09-05
Any idea how?

---

### Post by pavolzetor on 2010-09-05
restart computer and whilu you are in grub, adjust brightness by FN keys to max

---

### Post by RuneLacroix on 2010-09-05
```
sudo setpci -s 00:02.0 f4.b=ff 
```Works :) Can i write something to make it even brighter?

Its disappears when i restart... How can i make the brightness level stay high?

--- And... what does grub mean?

---

### Post by pavolzetor on 2010-09-05
grub is in most of cases bootloader (when you selecting kernel and OS what you want to start)

I don't know, how you can set it brighter, sorry

It's probably kernel bug, please, report it


Try add it before "exit 0" in /etc/rc.local

And please, if you put it to max. can you cahnge it by FN keys down and up in all range?

---

### Post by RuneLacroix on 2010-09-05
:) :) :)
Its working! 

And yes, the brightness adjustment still works!

Thank you very much for all the help :)

---

### Post by pavolzetor on 2010-09-05
Could you report bug?

and my pleasure, I feel that I am not useless

---

### Post by RuneLacroix on 2010-09-05
How do i report? alt F2, ubuntu-bug is the only way i know, but i don know what package the problems is with, and i think that this problem is maybe only concerning Asus Eee 1008p.
 I will report it to the creator of the Eee control daemon.

---

### Post by pavolzetor on 2010-09-05
I think, it is global problem, report it for kernel, thanks and post link here

---

### Post by RuneLacroix on 2010-09-06
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/631323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/631323)

---

