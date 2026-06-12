---
title: "PC shutdown, adaptor/USB port problems"
date: 2016-07-19
forum: Hardware
---

### Post by mistcloud-misty on 2016-07-19
I've had this laptop for almost 8 months, and it has randomly turned off (just clicked off out of the blue) 3 times. I believe the first time it overheated, but the other two times it did not. I've noticed the sudden shut down only occurs when I have not rebooted or shut down the laptop manually in at least 2 weeks, using suspend intermittently. I also notice in 16.04 that the longer I use the kernel without rebooting, the less healthy it becomes: for example, my wireless adaptor which is connected to a USB port (Since the internal one sucks) will randomly lose power when I move the laptop. This loss of power won't occur within the first few days (usually) of using the kernel except specific kernels which I avoid altogether), but occurs most often when I have moved the laptop or changed position and almost never when just sitting still.

dmesg records this:
```
[17284.537387] ath: phy1: Chip reset failed
[17284.537390] ath: phy1: Unable to reset channel (2437 Mhz) reset status -22
[17284.537392] ath: phy1: Unable to set channel
[17284.547412] ath: phy1: Failed to wakeup in 500us
[17284.657673] ath: phy1: Failed to wakeup in 500us
```

I'm not sure if both are related (kernel health and random computer shut downs with prolonged use), but I figured they may be clues to the real problem.

I am trying to figure out what hardware piece is responsible for the shut downs and why. I can avoid them just by rebooting my laptop every couple days which isn't a problem since the latest kernel only has a 50% chance of resuming from suspend without crashing (a problem I've been having with most of 16.04, really).

Any ideas? 

There are also no logs anywhere about anything happening system-side after a shut down occurs so I assume it is hardware related. 

Processor: Intel (i5)-2500u 
I am using that as graphics as well because the nvidia driver hasn't worked for me since 16.04. 

I have 8GB of memory and an HDD hard drive which is reported as healthy according to smart data.

---

### Post by sudodus on 2016-07-19
There could be several problems, both hardware and software for example

- poor cooperation between a piece of hardware and its driver (typically wifi and graphics)

- bad RAM, can be tested with memtest when booted in BIOS mode

Because of security updates and other updates of the kernel, it is a good idea to reboot, when a new kernel is available, unless you have very special reasons to avoid new kernels.

---

### Post by mistcloud-misty on 2016-07-19
The nvidia graphics isn't being used (open source driver used instead), so right now everything is run off intel and the wireless card. I'm not sure how I would be able to tell if the wireless driver is causing the wireless adaptor to interfere with the computer but I am always using the internet.

I will try and do a memtest tonight then and see if anything comes up.

Usually when the shut downs happen I do have an important update waiting for a reboot such as a new kernel, and this last time, shim-signed boot.

---

### Post by sudodus on 2016-07-19
Good luck and please tell us tomorrow what happened during memtest and after reboot with an updated kernel.

---

### Post by mistcloud-misty on 2016-07-19
I rebooted and was unable to find an option for memtest under GRUB menu... I had ubuntu, more options under ubuntu (other kernels only) and BIOS, which also had no place to run memtest.. is there something I'm missing? If I remember from windows running memtest was an option before booting.

---

### Post by sudodus on 2016-07-19
Memtest does not work in UEFI mode, but it works in BIOS mode. You can run it when booted from a DVD or USB drive (it is one of the options in the syslinux menu of Ubuntu in BIOS mode).

Press the Enter key, when you see two small icons near the bottom of the screen. After that you will get a menu to select language, and after that you are at the syslinux menu when the fourth option (line) is 'Test memory'. This is it :-)

***Edit:*** There are different tools to make USB boot drives. Some of them make different menus, and memtest might be omitted. Tools that use the cloning method will create menus like I describe above (they look the same as when booting from a DVD disk). Examples: mkusb, Disks (gnome-disks), Win32 Disk Imager and usb-creator-gtk version 0.3.2.

---

### Post by mistcloud-misty on 2016-07-19
Okay I will have to get to that tomorrow night instead so I can make a suitable USB with the memtest options. 

It seems my wireless disconnect when physically moving seems to happen only after waking up from suspend at least once... I guess it could be the wireless adapter itself but the problem didn't occur until 16.04 and doesn't occur with every kernel.

---

