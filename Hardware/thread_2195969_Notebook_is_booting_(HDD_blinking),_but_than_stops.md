---
title: "Notebook is booting (HDD blinking), but than stops with black screen"
date: 2013-12-27
forum: Hardware
---

### Post by it-nachhilfe on 2013-12-27
Hello together,

I've switched from using Windows to Ubuntu quite a few weeks ago - I'm a newie. I'm working with a Samsung X20 Notebook, Centrino 1.6 GHz, 512 MB RAM, 40GB HDD. OS is Ubuntu 12.04 LTS with Gnome 2 until yesterday, now with xfce.

From the very first time on I've recently had a strange effect: The PC has booted (HDD symbol was blinking), but than stopped, that means the HDD symbol wasn't blinking any more and the screen stayed black. Pressing Ctrl+Alt+Del, following a new booting procedure, usually fixed the problem. This problem took place about each 2. to 5. boot procedure.

Since yesterday evening I'm working with the xfce environement, which gave the same effect (I guess booting procedure is independent from GUI). But an hour ago, as I switched on my notebook, it did neither start up regularly nor stopped the boot procedure as before, but something like a minimalistic shell appeared with some (error?) message. Unfortunately, I didn't note down the message. I will do this, when the error occurs for the next time. As I remember, there stood something about HDD and timeout...

If someone has an idea, what causes this problem, I will be pleased to know. If you need further information, let me know. 

Greetings
Markus

---

### Post by it-nachhilfe on 2013-12-27
I made a reboot and - as expected- the error occured again. This time I catched the error message: 

> Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
    - check rootdelay = (did the system wait long enough?)
    - check root = (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)

Alert! /dev/disk/by-uuid/... does not exist.
Dropping to a shell!

  I hope this helps for further diagnosing.

---

