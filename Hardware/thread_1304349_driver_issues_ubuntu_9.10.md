---
title: "driver issues ubuntu 9.10"
date: 2009-10-29
forum: Hardware
---

### Post by ultiphoenix on 2009-10-29
Hey guys, i hope someone has a solution the the issues i've been having. I currently have the RC of ubuntu 9.10 (x64 arc) installed on my Acer Travelmate 7730 notebook.

The issue that im having is with the latest kernel (2.6.31-14-generic). It doesn't load any of my network drivers. The drivers in question is tg3 and iwlagn. here is the dmesg extract where it tries to start the devices:

```
    4.810602] Freeing unused kernel memory: 660k freed
[    4.810790] Write protecting the kernel read-only data: 7580k
[    4.817128] usb 8-2: configuration #1 chosen from 1 choice
[    4.934498] tg3.c:v3.99 (April 20, 2009)
[    4.934667] tg3 0000:09:00.0: enabling device (0000 -> 0002)
[    4.934676] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.934687] tg3 0000:09:00.0: setting latency timer to 64
[    4.960059] tg3 0000:09:00.0: PME# disabled
[    5.142123] tg3: eth%d: Cannot get nvarm lock, tg3_nvram_init failed.
[    5.202637] acpi device:03: registered as cooling_device2
[    5.203085] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
[    5.203120] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    5.244362] tg3: (0000:09:00.0) phy probe failed, err -19
[    5.567160] tg3: Problem fetching invariants of chip, aborting.
[    5.567330] tg3 0000:09:00.0: PCI INT A disabled
```
I cant find the wireless in the dmesg anymore, think its totally kicked the bucket, but it use to say something like "MAC in deep sleep", i've tried adding 'noacpi' flag on boot, doesn't help.

Do you guys have any suggestions? im currently using a usb wireless module.

This is so frustrating!!!

 ](*,)

---

### Post by hoofdbaas on 2009-10-31
Concur, have the same problem here with an Acer 7730. Read somewhere that with an external usb receiver it should work, but not here. Will keep trying for some time, but I guess it's back to 8.10 again, very frustrating indeed.
Pieter

---

### Post by ultiphoenix on 2009-11-09
i've tried again after final release came out, x86 and x64 arc. Both giving me the same issue, im so dissapointed in 9.10 because of these driver regression bugs.

I've even gone as far as building my own kernel with the latest source from kernel.org. No luck though, seems i still have the same issue.

Back on jaunty, jaunty would be fine if i could use gnome 2.28. i love the new alsa sound manager and bluetooth module :cry:. Awesome for playing music via bluetooth stereo to my home theatre.

Anyway, if anybody has success with this, please let me know, looks like i might have to wait for lucid before i'll be able to upgrade, sad sad times...

---

### Post by linuxmasters on 2009-11-09
Hi Guys,
I have the Aspireone-AOD250 with below mentioned specs,**Preloaded**

Processor 1.6 GHz Intel Atom N270
Memory 1GB DDR2 RAM 533 MHz
Hard drive 160GB, 5400rpm
Chipset Mobile Intel 945GM Express
Graphics Intel GMA 950 (integrated)
Operating System Windows XP Home SP3
Dimensions (WD) 10.17 x 7.24 inches
Height 1 inch
Screen size (diagonal) 10.1 inches
System weight / Weight with AC adapter 2.36/3 pounds
Category Netbook
Connectivity – Lan/Wifi/Bluetooth

Tried to load the new Netbook Remix 9.10 and the ubuntu 9.10. Everything seems to load and work fine except for one thing that is a major flaw as far as a normal user is concerned. **The moment  the laptop is unplugged from the mains power it goes into sleep mode and the WIFI network is also automatically disconnected**.Not sure but I assume the flaw is in the  gnome power management module. I have tried to Load Xubuntu 9.10 on the netbook and that to surprise seems to work just fine without any problems @ all. All the hardware works fine including soundcard out /wifi/wired lan / power management /camera. etc.



As of now i prefer to stick to version 9.04 for my netbook. as gnome is more comfortable to work with.

anyone else facing the same issues with aspire-one please update.

---

### Post by ultiphoenix on 2009-11-10
i've been having issues with my power management as well. when i start up my machine with the power plugged in, it doesn't detect my battery, if i start it up with the power plugged out and plug it in again after the machine has started up, its fine.

Have you tried to start your netbook up without the power plugged in? you should try that, its not a perfect solution but its better than nothing.

Also, have you tried to disable acpi? i know some people have had success with that in the past around power management.

---

### Post by linux4africa on 2009-11-16
Same issue on Acer 7730.

On 8.10 eth0 and wlan0 are perfect, but no network interface is configured on 9.10. If I plug in an old 3Com PCMCIA card I can get a network connection.

I tried upgrading from 8.10 and a clean install of 9.10, but the problem is the same.

---

### Post by linuxmasters on 2009-11-25
> **ultiphoenix said:**
> i've been having issues with my power management as well. when i start up my machine with the power plugged in, it doesn't detect my battery, if i start it up with the power plugged out and plug it in again after the machine has started up, its fine.

Have you tried to start your netbook up without the power plugged in? you should try that, its not a perfect solution but its better than nothing.

Also, have you tried to disable acpi? i know some people have had success with that in the past around power management.


well, here the issue only is if its connected to the mains and i am connected to the wifi network it goes into sleep mode and disconnects moment the mains are plugged out.. Battery and all are detected at boot time as you have mentioned you are having issues. just that if i am charging and working at the same time  and if lights go off it instantly goes to sleep.whereas 9.04 is working just PERFECT..no Issues. i have tweaked it to run as much fast as i can on the net-book.


yes tried the acpic settings as well. no Good.
Even tried the ubuntu-moblin-remix as well.

---

### Post by linuxmasters on 2009-11-25
> **linux4africa said:**
> Same issue on Acer 7730.

On 8.10 eth0 and wlan0 are perfect, but no network interface is configured on 9.10. If I plug in an old 3Com PCMCIA card I can get a network connection.

I tried upgrading from 8.10 and a clean install of 9.10, but the problem is the same.

9.10 has too many problems.lots of broken packages.Wifi for notebooks / Video for  Nvidia. and other SD-MMC Cards issues.Use the older version , they are always more stable. Try some other distro, which one makes everything work.
Some place or other we have to compromise..:(

---

### Post by linux4africa on 2009-11-27
With acpi=off I get get the network running...so I will wait another week or two for a patch.

I always avoid installing new distros on anything important, so I can wait a bit longer...but frustrating!

---

### Post by linux4africa on 2009-12-12
It now works after I upgraded the kernel from 2.6.31-16 to 2.6.31-17.


Thanks for the fix.

---

### Post by bender1234 on 2009-12-24
> **linux4africa said:**
> It now works after I upgraded the kernel from 2.6.31-16 to 2.6.31-17.


Thanks for the fix.


Can anyone else confirm this? I'm running the .15 kernel with the fix on an 6930G with intel 5100, a bit nervous of doing any updates that will break my wired and wireless networking.

and merry xmas btw! :)

---

### Post by bender1234 on 2009-12-25
bump! :)

---

### Post by ultiphoenix on 2010-01-03
hey guys, im so glad to confirm that this is now working with the new kernel. Did a clean install of karmic today, used a old usb wireless dongle jus to get conntected. enabled prereleased updates, reloaded repos and bam there it was. the new kernel. installed and it works perfectly!!!!!

thanx for everyone that helped with finding this fix.

---

