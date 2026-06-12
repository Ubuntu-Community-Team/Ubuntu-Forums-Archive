---
title: "Message &quot;No proprietary drivers are in use on this system&quot;"
date: 2011-11-15
forum: Hardware
---

### Post by r_avital on 2011-11-15
Hi all,

I'm posting this in Hardware because I believe the problem is hardware-related:

Ubuntu Lucid 64, uname -a returns:
2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 16:11:24 UTC 2011 x86_64 GNU/Linux

Motherboard: ASUS Sabertooth X58 LGA 1366 Intel X58 SATA 6Gb/s USB 3.0 ATX Intel 

Graphics card: NVIDIA - PNY VCGGT4301XPB GeForce GT 430 (Fermi) 1GB 128-bit DDR3 PCI Express 2.0 x16 HDCP Ready Low Profile Video Card

lspci output: ```
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:02.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 13)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 IDE interface: Device 1b4b:91a3 (rev 11)
02:00.0 USB Controller: NEC Corporation Device 0194 (rev 04)
[B]04:00.0 VGA compatible controller: nVidia Corporation Device 0de1 (rev a1)
04:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)[/B]
05:00.0 SATA controller: JMicron Technology Corp. Device 2362 (rev 10)
07:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
07:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
```As you can see from the two Bolded lines in the output, the graphics card is recognized as NVIDIA.

When I run System -> Administration -> Hardware drivers, I get the error message: 
No proprietary drivers are in use on this system

I've never seen this happen before.  I've installed Ubuntu Lucid on several --much older-- systems with built-in NVIDIA graphics, and the Hardware Drivers utility always offered an NVIDIA driver to install.

What I've tried:

In Synaptic, removed all NVIDIA-related items from the system (173-modaliases was installed by the Ubuntu install for some reason and a few others, removed them all).  Then, in Synaptic, installed nvidia-current and all suggested additional packages.

After restarting, Hardware Drivers did show the NVIDIA current as installed and recommended, but not in use.  Clicked it to be activated, rebooted again, and at this point, right after the opening purple Ubuntu screen, I get a black screen, steady cursor (not blinking), and some lines of text flashing for a fraction of a second every 5 or 6 seconds.  The system is frozen.

If I restart and go into Grub to start in safe mode or go to a console, I can tell that /etc/X11 has a new file xorg.conf that was not there before, so obviously Ubuntu is doing the right thing, because I checked and this file was not there before I went into the above procedure.  The result is the same whether I reboot, cold-boot, or just restart X.

Please help... This is a brand new motherboard and brand new NVIDIA card, and all I'm getting is 800x600 on the same monitor that I use at 1200x1600 rotated vertical on 3 other Ubuntu Lucid machines with the built-in NVIDIA which are much much older (on a KVM).

I could download the driver from the NVIDIA site and install it, but I'm afraid it will give me the same result.

Again, please, any ideas will be appreciated.

Thanks

---

### Post by cmileto on 2011-11-15
Do you have the linux-restricted-modules for your kernel installed?
sudo apt-get install linux-restricted-modules-`uname -r`

I always just use nvidia's propriotary installer.

perhaps this may help?  [http://askubuntu.com/questions/3024/good-nvidia-drivers-for-ubuntu/3027#3027](http://askubuntu.com/questions/3024/good-nvidia-drivers-for-ubuntu/3027#3027)

---

### Post by r_avital on 2011-11-15
Thanks, cmileto - I attempted the installation of the restricted modules as you suggested, got the following response: 

E: Couldn't find package linux-restricted-modules-2.6.32-35-generic

I googled around for it, but there doesn't seem to be one for the current build - if I'm wrong, someone please point me to it.

That got me thinking further, and found a thread [http://ubuntuforums.org/showthread.php?t=1599973](http://ubuntuforums.org/showthread.php?t=1599973) which talks about the ubuntu-restricted-extras.  I installed it, but Hardware Drivers still shows the same "no proprietary drivers" message.

As far as your other suggestion, I'd be happy to try it, but I'm reluctant because if my installation won't support it, then the installation of the proprietary NVIDIA driver gets compiled into the kernel and might mess it up, won't it?

---

### Post by r_avital on 2011-11-15
Update:

Well, cmileto, thanks so much.  I installed the proprietary driver from the Nvidia site, solved the problem.  Me so happy.

One last question to you:  Since you mentioned you always did this, when you get an updated kernel, do you have to run that installation again?

[Note that exiting to a console and stopping X did not work for me, the Nvidia install still reported X was running.  I had to boot into grub and drop to a console from there]

Let me know when you can, no rush.

Thanks again.  I'll mark this solved after I get your reply.

---

