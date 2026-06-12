---
title: "Black screen for one second every time i start a video in ubuntu 12.04"
date: 2012-05-08
forum: Hardware
---

### Post by Bucky83 on 2012-05-08
I have a very, very annoying problem and couldn't figure out what is going on yet.

I get a black screen (that last for 1 second roughly) every time I open a video (vlc, mplayer), every time I open a web page featuring a video, every time I open pages like GMAIL or others and every time I open programs like Tecplot (dataset analysis tool).

I have no idea what might be the problem, I've tried to disable the screen saver, change the resolution or to enable different verison of the Nvidia drivers. Nothing helped.

Based on what I have found on the internet, it almost seems that nobody else has had this kind of problems.
Does anyone have any suggestions?

Best Regards

---

### Post by Bucky83 on 2012-05-13
Anyone?

---

### Post by Kieran. on 2012-05-31
I also have this problem. In my case it is my second monitor that turns black for 1 second and then back again, the first remains unaffected. The cause however is exactly the same as you; mplayer, flash content etc.

---

### Post by Bucky83 on 2012-06-11
Ok, so, apparently this is very very very limited to the only two of us.

---

### Post by fransfrans on 2012-06-25
same problem here, my graphics card is:
VGA compatible controller: NVIDIA Corporation G86 [Quadro NVS 290] (rev a1)
using nvidia proprietary driver.
It's indeed only the second monitor that does the blinking

---

### Post by slotown on 2012-07-04
wow finally I find people with the same issue as me. I have the same exact issue. It may be me but it seems the issue ramps up once firefox is started and continues to happen minimizing and maximizing firefox but happens with other programs also. It is just easier to reproduce with firefox and sometimes when computer boots, it does not happen for a while but once it does, it is just continuous and annoying. After screen blanks and comes back I see the monitor connection picture in the upper left of the monitor for a few seconds which tells me it could be some sync issue. 

Display identity
description: VGA compatible controller
 product: G86 [Quadro NVS 290]
 vendor: NVIDIA Corporation
 physical id: 0
 bus info: pci@0000:01:00.0

on this particular combination of hardware, dell tower, dell monitor, this is the first time I have seen the issue and have ran every version of ubuntu starting from 9.x on this hardware where 12.04 is first time the issue occurred. 

One more thing to note, when system boots, the ubuntu splash screen is of low resolution like 640x480 where on other version of ubuntu the splash was of much higher res. Also note that when I go to alternate console e.g. ctrl-alt-f3, the font is large and console resolution low. One more thing to note is, I maintain usb live pens and keep my 12.04 up to date and this issue does not occur when booting to live usb pen in 12.04 as far as the splash screen and console fonts. I thought I had a bad install and blew everything away and wiped out the disk and started over and same exact issue came back.

---

### Post by Bucky83 on 2012-07-04
Yeah, everytime I open GMAIL or resize the firefox browser window when gmail (or others) are open it blacks out for one second.
```

isola@leader:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82X38/X48 Express DRAM Controller
00:01.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge
00:06.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Secondary PCI Express Bridge
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [Quadro NVS 290] (rev a1)
03:00.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
04:01.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
04:05.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
04:07.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
04:09.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
06:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9120 SATA 6Gb/s Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)

```


And I have tried many different NVIDIA settings but nothing seemed to wrok



```

^C
isola@leader:~$ sudo lshw 
[sudo] password for isola: 
leader                    
    description: Tower Computer
    product: Precision WorkStation T3400 ()
    vendor: Winbond Electronics
    serial: 8NMW64J
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: administrator_password=enabled boot=normal chassis=tower power-on_password=enabled uuid=44454C4C-4E00-104D-8057-B8C04F36344A
  *-core
       description: Motherboard
       product: 0TP412
       vendor: Winbond Electronics
       physical id: 0
       serial: ..CN708218BID1LN.

................

     *-pci
          description: Host bridge
          product: 82X38/X48 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=x38_edac
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: 82X38/X48 Express Host-Primary PCI Express Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:fa000000-fdefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G86 [Quadro NVS 290]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fc000000-fcffffff memory:d0000000-dfffffff 

```

---

### Post by Bucky83 on 2012-07-04
I think I might have solved it...

I un-ticked the "Allow Flipping" box under OpenGL settings of the NVIDIA x Server Settings.

Does it work to you as well?

---

### Post by slotown on 2012-07-04
Thanks for the tip. Funny, when I clicked 'Allow Flipping' screen blanked again but so far it has not happened again staying unchecked. Sounds like you have similar hardware as me. For anyone else reading this thread, I have a Dell 2208WFP monitor and computer is a Dell tower 
description: Tower Computer
product: Precision WorkStation T3400 ()

If issue happens again I will update the thread but so far things look stable. Another way I was able to reproduce this issue was click a new tab in firefox but so far this is not happening anymore. All good.

---

### Post by slotown on 2012-07-09
I've been out of town and meant to update this thread last week before I left but I am still seeing the issues. Definitely not as often after turning off flipping. I believe there may be some newer drivers out there provided by other repositories. Here is my current version info 
Operating System: Linux-x86_64
NVIDIA Driver Version: 295.49
Server Version Number: 11.0
Server Vendor Version: 1.11.3 (11103000)
NV-CONTROL Version: 1.27

I think I saw a .53 version out there and it may be newer now but since these are forums, I am guessing that this is more for user interaction and I am thinking a bug will have to be logged somewhere such as launchpad.

---

### Post by Kieran. on 2012-08-27
I have now found a solution that works on my machine. When I first installed the nVidia drivers I had two proprietory driver options in the additional drivers panel

(version current) [Recommended]
(post-release-updates) (version current-updates)

Both of these produced the blank second screen issue so I stuck with the recommended option. When I checked the additional driver list today however, two more proprietory drivers have been made available, as follows

(version 173)
(post-release-updates) (version 173-updates)

I installed and activated the second of these and rebooted. Problem is all solved now.

---

### Post by slotown on 2012-08-27
My problem completely went away a couple weeks back. From my memory, the update that fixed it was the following

Start-Date: 2012-08-13  08:03:53
Commandline: apt-get upgrade
Upgrade: base-files:amd64 (6.5ubuntu6, 6.5ubuntu6.2), xserver-xorg-core:amd64 (1.11.4-0ubuntu10.6, 1.11.4-0ubuntu10.7), xserver-common:amd64 (1.11.4-0ubuntu10.6, 1.11.4-0ubuntu10.7), sessioninstaller:amd64 (0.20+bzr128-0ubuntu1, 0.20+bzr128-0ubuntu1.1)
End-Date: 2012-08-13  08:04:42

After this update on 8/13, I never saw the blanking issue again. A few days later I did get a nvidia update

Start-Date: 2012-08-16  07:06:00
Commandline: apt-get upgrade
nvidia-current:amd64 (302.17-0ubuntu1~precise~xup2, 304.37-0ubuntu1~precise~xup1)

and this was newer than the one I was using from a different source so I ended up disabling and removing mine which was I believe 2.95xxx from my memory.

Things have been looking good so far.

---

