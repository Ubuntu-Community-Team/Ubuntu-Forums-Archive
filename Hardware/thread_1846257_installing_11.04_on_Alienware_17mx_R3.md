---
title: "installing 11.04 on Alienware 17mx R3"
date: 2011-09-18
forum: Hardware
---

### Post by pinan on 2011-09-18
I am trying to install Ubuntu on an Alienware 17mx R3 laptop.

Everything goes as expected, until the first reboot

My attempts have all failed with a grub debug error and the machine quoting a non existant UUID partition.

The machine has a fake raid controller are there any rules about how partitions should be assigned ?  I had attempt to use the disk tools to make several different sized partitions as an aid for backing the machine up.

I known it possible to do it, see [http://forum.notebookreview.com/alienware-m17x/568692-linux-support-2.html](http://forum.notebookreview.com/alienware-m17x/568692-linux-support-2.html), an entry at the bottom on the page by storm99999

Does anybody have any suggestions?

Since its the boot menu that has the problem it also takes out any attempt to boot windows.

lspci indicates 
------------------------


00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 1251 (rev a1)
01:00.1 Audio device: nVidia Corporation Device 0bee (rev a1)
07:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
0d:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
13:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
19:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

---

### Post by pinan on 2011-09-19
Just managed to resolve this problem.

My machine had a fake software raid on it, I had decided  to remove it and use both disks for extra space.

When I remove the Ubuntu install disk it would either boot to Windows7 if I set the machine up as a dule boot machine, or report an grub error if I totally removed Windows.

By looking at the Bios I discovered that the machine was set to boot from the 2nd hard drive.  Once I told it to boot from the first drive, it fired up in to gub/Ubuntu no problems. :P

SO be warned, check you disk boot order settings when installing, it took me a day to discover this little error

---

### Post by wulvyrn on 2011-09-21
did you get the audio to work? i'm having that issue with my 18x.

---

