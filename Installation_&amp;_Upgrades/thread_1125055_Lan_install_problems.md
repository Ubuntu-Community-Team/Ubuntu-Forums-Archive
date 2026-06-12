---
title: "Lan install problems"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by Bapu on 2009-04-14
So I instaled ubuntu for the first time on my Gigabyte GA-P35-DS4 Rev 2.1 mobo with a Realtek 8111B onbaord NIC card.

Since I the NIC was not working I decided to go to realtek site and see if there was a Linux driver for it. There was.

[COLOR="red"]So I dowloaded it to Ubuntu and went about following their instructions.[/COLOR]

<Linux device driver for Realtek Ethernet controllers>

This is the Linux device driver released for RealTek RTL8168B/8111B, RTL8168C/8111C, RTL8168CP/8111CP, RTL8168D/8111D Gigabit Ethernet controllers with PCI-Express interface.

<Requirements>

- Kernel source tree (supported Linux kernel 2.6.x and 2.4.x)
- For linux kernel 2.4.x, this driver supports 2.4.20 and latter.
- Compiler/binutils for kernel compilation

<Quick install with proper kernel settings>
Check whether the built-in driver, r8169.ko (or r8169.o for kernel 2.4.x), is installed. 
# lsmod | grep r8169

If it is installed, please remove it.
# rmmod r8169
note: If the built-in driver cannot removed by rmmod, please edit /etc/modprobe.conf and comment 'alias eth0 r8169'. Then, remmove it again or reboot your computer.

Unpack the tarball :
# tar vjxf r8168-8.aaa.bb.tar.bz2

Change to the directory:
# cd r8168-8.aaa.bb

If you are running the target kernel, then you should be able to do :

# make all (as root or with sudo)
# depmod -a
# modprobe r8168

You can check whether the driver is loaded by using following commands.

# lsmod | grep r8168
# ifconfig -a

If there is a device name, ethX, shown on the monitor, the linux 
driver is loaded. Then, you can use the following command to activate 
the ethX.

# ifconfig ethX up


[COLOR="Red"]However at the make all commnad (which consists of "clean" & "modules" and "installed" you can see there was a failure at the "modules" step:[/COLOR]

edward@edward-server:~/Documents/r8168-8.011.00$ sudo make all
[sudo] password for edward: 
make -C src/ clean
make[1]: Entering directory `/home/edward/Documents/r8168-8.011.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
make[1]: Leaving directory `/home/edward/Documents/r8168-8.011.00/src'
make -C src/ modules
make[1]: Entering directory `/home/edward/Documents/r8168-8.011.00/src'
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'. Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/edward/Documents/r8168-8.011.00/src'
make: *** [modules] Error 2

[COLOR="red"]Here is the output from my lspci:[/COLOR]00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)


[COLOR="Red"]Here is the output from route:[/COLOR]Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface


[COLOR="red"]Here is the output of ifconfig -a:[/COLOR]lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:374 errors:0 dropped:0 overruns:0 frame:0
TX packets:374 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:25392 (25.3 KB) TX bytes:25392 (25.3 KB)

pan0 Link encap:Ethernet HWaddr ce:68:54:0b:64:6d 
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

[COLOR="Red"]
Note eth0 is not there because of course the modules and install portions of the make command failed.[/COLOR]

How can I get a driver up for this NIC?

TIA for any help.

---

