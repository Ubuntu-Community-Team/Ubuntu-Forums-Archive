---
title: "Dell laptop fan gets stuck on high untill poweroff/suspend"
date: 2013-02-09
forum: Hardware
---

### Post by cipx2 on 2013-02-09
Hi everyone,

I have a Dell Vostro 3750 with the dreaded Nvidia Optimus and Ubuntu 12.10 on it.
Everything works pretty well except the fan (and other known things which I don't bother that much).
Power consumption is good (maybe a bit better than in W7). All works well until I do some intensive work and the CPU temperature gets high. At some point  the fan hits max rpm (~4200) which is normal.
The issue is that even  the CPU & Co cools down at < 45 C, the fan remains stuck at max rpm. The only way to reduce the fan speed is to go through a power off or a suspend (restarting ubuntu doesn't help). Sounds like a hardware problem but in W7 doesn't happen - when the CPU temp decreases, the fan rpm goes down. In Ubuntu I can leave it alone for 3 hours, the cpu cools down to 35 degrees, cpu load is 2-4% but the fan stays on max rpm until I suspend the pc and resume.

Any clues as what to check and where to start?
Thank you.

---

### Post by tgalati4 on 2013-02-09
Do you have any settings in BIOS that control fan speed behavior or temperature setpoints?

Open a terminal:

```
sudo apt-get install fancontrol
man fancontrol
```

It could be a bug in BIOS, try flashing an update to your BIOS.

---

### Post by cipx2 on 2013-02-09
Thanks for the suggestions.
Unfortunately  the laptop/MB doesn't have a PWM sensor/fan, lm-sensors doesn't detect one and fancontrol relies on it. 

No, there are no settings in BIOS.
The BIOS is up to date (oct 2012 version) and it's the third update since I bought the laptop. None of the updates made no diff. I had this issue since day 1 when I tried the 11.10 (or even 11.04?).

Now I see there's no /proc/acpi/fan folder:
```

$ ls -R /proc/acpi

/proc/acpi:
bbswitch  button  event  wakeup

/proc/acpi/button:
lid

/proc/acpi/button/lid:
LID0

/proc/acpi/button/lid/LID0:
state

```So it seems the fan is controlled by the BIOS.

---

### Post by tgalati4 on 2013-02-09
Does the module i8k load?

```
sudo modprobe i8k
sensors
```

---

### Post by cipx2 on 2013-02-09
Nope.
That's what I tried from day 1 as my previous laptop was also a Dell and I had i8kutils and the win version in use.

---

### Post by tgalati4 on 2013-02-09
I have an old Inspiron 600m that I could load i8k to get fan speeds and control them if I needed to, but the BIOS seems to control them OK.  Sounds like you are stuck at the moment.

Send an email off to Dell support.  We need more humor on this forum.

---

### Post by cipx2 on 2013-02-09
SOLVED SOLVED SOLVED SOLVED SOLVED SOLVED SOLVED SOLVED SOLVED SOLVED

Solution:
```
 sudo gedit /etc/default/grub
```Modify line 12, instead of:
GRUB_CMDLINE_LINUX=""
make it:
GRUB_CMDLINE_LINUX="acpi_osi=\"Linux\""
save, close gedit and then:
```
sudo update-grub
```I found this solution some time ago related to a fan problem and also to other issues but I tried it with [s]GRUB_CMDLINE_LINUX="acpi_osi=Linux"[/s], with [s]GRUB_CMDLINE_LINUX="acpi_osi="Linux""[/s] and with [s]GRUB_CMDLINE_LINUX="acpi_osi='Linux'"[/s] (I think?) with no luck
Today I found another link
[http://www.maximumpc.com/article/news/ubuntu_1010_%E2%80%9Cmaverick_meerkat%E2%80%9D_officially_released#comments](http://www.maximumpc.com/article/news/ubuntu_1010_%E2%80%9Cmaverick_meerkat%E2%80%9D_officially_released#comments)
and said "Whoaaa, where was my head?! How about some java/C syntax?? I tried and voila!

I did intensive tests, run the cpu up 85 C (couldn't get it higher), now the fan  has all the speed steps as in win (instead of 4), reaches top speed at 80C (instead of 72C) and beautifully reduces its speed as soon as the temp gets back to 70_something.  

Me happy\\:D/

Thanks for assistance guys!

P.S.: tgalati4, "Dell support"?! What's that? Aaaa, the guys at [http://www.dell.com/support/home/us/en/](http://www.dell.com/support/home/us/en/) that put on all pages in upper right corner "Dell recommends Windows"? Thanks but no thanks :)

---

### Post by tgalati4 on 2013-02-09
Well, Microsoft did loan them $2 billion dollars.  I would put that in my signature if I was paid $2 billion.  Even $1 billion.

Glad you got it fixed.  Would hate to think of your suffering while using Windows.  A billion dollars would lessen that suffering greatly.

---

