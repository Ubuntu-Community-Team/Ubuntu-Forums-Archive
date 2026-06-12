---
title: "no nvidia hybrid graphic support in ubuntu"
date: 2011-10-21
forum: Hardware
---

### Post by jcxaver on 2011-10-21
sony vaio z31, graphics GMA X4500MHD/GeForce 9300GS

switching works not, hdmi works not.

[http://global-social.net/tiki-view_blog.php?blogId=3#intel_xorg.conf](http://global-social.net/tiki-view_blog.php?blogId=3#intel_xorg.conf) .. is quite old, helps not. Nvidia driver is installed but Nvidia X server message: You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. But it is good joke (in standard ubuntu instalation),  doing this tend to rescue and recovery xorg.conf , black screen.

Is it impossible to solve it in ubuntu, o.k. this problem have I three years  since 8.04 version. It costs me a lot of days time - ubuntu :(. This hw has no problems in MS windows. Should I try another linux distro? Thank you for help.

```
jc@u-vaio:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9300M GS] (rev a1)
06:00.0 Network controller: Intel Corporation WiFi Link 5100
0b:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
0b:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
0b:04.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
0b:04.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)

```

---

### Post by jcxaver on 2011-10-27
with 64bit oneiric ocelot I was not successfull with anything of this:

[LIST][*]Asking here in ubuntuforums.org five days ago. **No reply. No help.**[*]Submiting bug in ubuntu launchpad [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/879894]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/879894")[*]Trying acpi_call, byo-switchero like there:  [http://linux-hybrid-graphics.blogspot.com/2010/10/vga-switcheroo-and-acpicall-status-so.html]("http://linux-hybrid-graphics.blogspot.com/2010/10/vga-switcheroo-and-acpicall-status-so.html")[*]Trying this:[http://global-social.net/tiki-view_blog.php?blogId=3#intel_xorg.conf]("http://global-social.net/tiki-view_blog.php?blogId=3#intel_xorg.conf")[*]Trying switchero support in current kernel of oneiric ocellot.  [https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")[*]Uninstalling ubuntu and trying Open Suse with simillar results. I must say that oder kernels gave me hope to try switchero once again I found . I can try   ```
grep -i switcheroo /boot/config-2.6.*
```  there. **In Oneiric Ocelot are boot/config* folders missing.** And I dont know about any redemption.
[/LIST]


Main reason that both graphic are working te same time:
```
jc@u-vaio:~$ lspci -vnnn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: nVidia Corporation G98 [GeForce 9300M GS] [10de:06e5] (rev a1) (prog-if 00 [VGA controller])
jc@u-vaio:~$ 

```
Laptop is very heat. 

[B]I cannot find switchero support for Oneiric Ocelot like this:
[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")
This help become unusable with new Ubuntu 11.10[/B]

---

