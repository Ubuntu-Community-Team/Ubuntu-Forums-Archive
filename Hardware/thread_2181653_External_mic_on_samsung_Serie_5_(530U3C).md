---
title: "External mic on samsung Serie 5 (530U3C)"
date: 2013-10-18
forum: Hardware
---

### Post by poubelle-r on 2013-10-18
Hello,

I'm trying to aquire some sound through the external microphone. 
The problem is that there is only one plug shared with the headphone.
I've tried the pavucontrol, alsamixer, hda-jack-restack, hdaanalyzer... But can't find a way to record from the external mic.
The full alsa info can be found here:
[http://www.alsa-project.org/db/?f=2f5d80ec0230541e96c65bf49008fa86895ffee3](http://www.alsa-project.org/db/?f=2f5d80ec0230541e96c65bf49008fa86895ffee3)


Does anyone knows if there is a bug or if there are some tweak to do? I just want to use the headphone plug as a microphone entry and keep the sound on the speakers

Thanks for any help

---

### Post by poubelle-r on 2013-10-18
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

---

### Post by poubelle-r on 2013-10-20
Hello,

I've found out the problem.
It is not related to ubuntu but to the internal connector of the notebook.
In  fact, the plug that can be used for headphone/mic seems to be a TRRS 4  type plug. It's a plug that has 4 parts (left, right, ground mic) that  is similar as some mobilephone.
I've just tried with an htc headset which has this kind of plug and it worked out of the box.
I think I will have to buy a converter with 3 jacks. 2 females (mic/headphone) and one male trrs 4 to go the laptop.

Hope this thread can save some time to someone...

---

