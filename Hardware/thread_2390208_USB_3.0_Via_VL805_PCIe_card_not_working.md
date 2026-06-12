---
title: "USB 3.0 Via VL805 PCIe card not working"
date: 2018-04-26
forum: Hardware
---

### Post by zhongtiao1 on 2018-04-26
I got a USB 3.0 Card the other day and I found that it was only working when I booted into Windows (which I seldom do). However, I would really like for it to work on Ubuntu since I use it the majority of the time. My computer is a Dell Optiplex 980 full tower and I am on Ubuntu Kylin 16.04.

I followed the suggestion here: [https://bbs.archlinux.org/viewtopic.php?id=214293](https://bbs.archlinux.org/viewtopic.php?id=214293)

but adding the iommu soft to grub did not work. I disabled Intel VT, and it still didn't work.

Multiple people have said that they have gotten it to work on their computer, but it does not work on mine.

with lspci I get:
```
02:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)
```

and with lsusb I get:
```
Bus 003 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
```

My grub file looks like this:
```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=Ubuntu\ Kylin
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="iommu=soft"
GRUB_CMDLINE_LINUX="intel_iommu=off"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Does anyone have any other suggestions?

---

### Post by #&amp;thj^% on 2018-04-26
> **zhongtiao1 said:**
> I got a USB 3.0 Card the other day and I found that it was only working when I booted into Windows (which I seldom do). However, I would really like for it to work on Ubuntu since I use it the majority of the time. My computer is a Dell Optiplex 980 full tower and I am on Ubuntu Kylin 16.04.

I followed the suggestion here: [https://bbs.archlinux.org/viewtopic.php?id=214293](https://bbs.archlinux.org/viewtopic.php?id=214293)

but adding the iommu soft to grub did not work. I disabled Intel VT, and it still didn't work.

Multiple people have said that they have gotten it to work on their computer, but it does not work on mine.

with lspci I get:
```
02:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)
```

and with lsusb I get:
```
Bus 003 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
```

My grub file looks like this:
```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=Ubuntu\ Kylin
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="iommu=soft"
GRUB_CMDLINE_LINUX="intel_iommu=off"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Does anyone have any other suggestions?

I don't know why this is taking so long to implement (Since the year 2012) into the kernels, but see if this helps by adding  "pci=nomsi" to the boot parameters in grub.conf. And don't forget to update grub Also _don't forget to disable iommu in your bios._
So where your looks lie this "GRUB_CMDLINE_LINUX="intel_iommu=off" "
try changing "iommu=off" to "pci=nomsi"

---

### Post by zhongtiao1 on 2018-04-28
> **1fallen said:**
> I don't know why this is taking so long to implement (Since the year 2012) into the kernels, but see if this helps by adding  "pci=nomsi" to the boot parameters in grub.conf. And don't forget to update grub Also _don't forget to disable iommu in your bios._
So where your looks lie this "GRUB_CMDLINE_LINUX="intel_iommu=off" "
try changing "iommu=off" to "pci=nomsi"

I tried that and it didn't work :(

My BIOS sees the PCI Card as a USB card, but it does not detect any drive I plug in. I have disabled all Intel VT options in the BIOS.

---

### Post by matmercer on 2018-05-30
I managed to fix the issue in Arch Linux by updating the firmware (using a proprietary software in Windows) of the VL805.
My version of the firmware (013600 vs 013704) was older than the new one.

**Note that to update the firmware, you need to unninstall the windows driver in the device manager, I've had some issues updating it.**

This was the response of VIA tech support when I asked them for Linux issues:

[quote=VIA Support]
Hi,

VL805 is working well on Fedora 4.13.9-300. fc27.x86_64 .
And we also test on Fedora 4.13.16-100. fc25.x86_64 .
The function is ok, USB device can be recognized under VL805.
This issue should be possibly related to AMD driver behavior
 
Test condition in VLI:
CPU = Intel i3-8100
Motherboard : MSI Z370 Gaming M5

You can download the latest firmware update tool for VL805 and check the function.
User guide is stored in the folder.
This tool only support on Windows-based.

[https://www.dropbox.com/s/68srdt4gmvgsv6k/VL805%26VL806%20FW%20Update%20Tool.zip?dl=0](https://www.dropbox.com/s/68srdt4gmvgsv6k/VL805%26VL806%20FW%20Update%20Tool.zip?dl=0)
 
If there is any question, please contact me.

Thanks.

[/quote]

I Hope my message helps other people, since there aren't any other place I've found that shows the true sollution.

---

### Post by antonine on 2019-01-18
A warning and the solution! The above upgrade tool failed to identify the memory chip on my board but erased it anyway and then hung on writing rendering it useless.

After some research I was able to successfully upgrade after editing the SpiFlash.ini file with the parameters of the 25P10VP chip on my board.

I added the following:

21=25P10VP



[25P10VP]
FlashID = 202011
ReadID = 9F
WriteEnable = 06
WriteStatus = 01
ChipErase = C7
ReadData = 03
ReadStatus = 05
PageProgram = 02
ClockRate = 32
PageSize = 10


I can confirm you do appear to have to uninstall the Windows drivers to update and reboot after ISP update success before it works.

---

### Post by niziak2 on 2020-01-04
Thanks for SPI Flash config. It works also for my version of card. My  fimrware version was 00013400, so very old. 
I was able to flash it from  Windows XP running as VirtualBox guest (see [https://docs.oracle.com/cd/E97728_01/F12469/html/pcipassthrough.html](https://docs.oracle.com/cd/E97728_01/F12469/html/pcipassthrough.html)). 
Before starting machine you have  to attach PCI device 
```
VBoxManage modifyvm "VM name" --pciattach 04:00.0@01:05.0
```
Where 04:00 is bus number returned by lspci

To detach PCI device:
```

VBoxManage modifyvm "VM name" --pcidetach 04:00.0

```

---

### Post by kato223 on 2020-05-09
> **antonine said:**
> A warning and the solution! The above upgrade tool failed to identify the memory chip on my board but erased it anyway and then hung on writing rendering it useless.

After some research I was able to successfully upgrade after editing the SpiFlash.ini file with the parameters of the 25P10VP chip on my board.

I added the following:

21=25P10VP



[25P10VP]
FlashID = 202011
ReadID = 9F
WriteEnable = 06
WriteStatus = 01
ChipErase = C7
ReadData = 03
ReadStatus = 05
PageProgram = 02
ClockRate = 32
PageSize = 10


I can confirm you do appear to have to uninstall the Windows drivers to update and reboot after ISP update success before it works.

How did you find the chip on your board?  Mine is not identifying through the program itself so I am unable to flash it with the newer firmware.  It does however read the firmware fine on the board, but that is as far as I get.  Even if I try to update the FW, it just hangs.

---

### Post by QIII on 2020-05-09
RIP old thread.  My apologies for your having been disturbed from your slumber twice.

Closed.

---

