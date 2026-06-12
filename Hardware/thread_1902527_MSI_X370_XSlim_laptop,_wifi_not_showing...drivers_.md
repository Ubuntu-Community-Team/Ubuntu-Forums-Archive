---
title: "MSI X370 XSlim laptop, wifi not showing...drivers are installed...??"
date: 2011-12-31
forum: Hardware
---

### Post by socioteq@gmail.com on 2011-12-31
Hello all.  This is my first post to the forums, although I've been using Ubuntu for 4 years now.  I usually find that I can find all of the answers that I need by searching for problems that have already been had; but this one is different.

I purchased this laptop the other day for its size and bang/buck and have everything working on it with the exception of WiFi... I've tried several different things including the so-called firmware install of the ipw2200 drivers.  These drivers are now located in /lib/firmware/ but nothing has changed.  Here is my ifconfig (which doesnt show me what I expected to see, which was the wireless adapter information).


eth0      Link encap:Ethernet  HWaddr 6c:62:6d:34:f3:17  
          inet addr:192.168.1.77  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6e62:6dff:fe34:f317/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14697 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14140798 (14.1 MB)  TX bytes:2087580 (2.0 MB)
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24160 (24.1 KB)  TX bytes:24160 (24.1 KB)

The wireless component of the system is an Intel WM3B2200BG (which is why I added the ipw2200.sourceforge.net driver to /lib/firmware/

I read in a previous post that I tried to follow that the adapter should just magically work at this point, but needless to say, that's not what happened.

Here is lsusb  (also not showing anything helpful)

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0461:4d42 Primax Electronics, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Also a grep of ipw shows:

kevin@kevin-laptop:~$ lsmod | grep ipw
libipw                 45137  0 
lib80211                6151  1 libipw
ipw                     7401  0 
usbserial              39973  1 ipw

Here is a dmesg

kevin@kevin-laptop:~$ dmesg | grep ipw
[ 2963.042315] usbcore: registered new interface driver ipwtty
[ 2963.042321] ipw: v0.3:IPWireless tty driver
[ 3060.869601] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[ 3060.869608] ipw2200: Copyright(c) 2003-2006 Intel Corporation


What am I doing wrong here? I just want my WiFi to work, but I haven't seen the sun for days.

If anyone could please help on this one it would be much appreciated.  I can give you any other info that might be beneficial with minimal explanation.  PLEASE PLEASE PLEASE HELP! Thanks
Kevin

---

### Post by socioteq@gmail.com on 2011-12-31
I hav efound very little information regarding this laptop in the ubuntu forums... does anyone have this lappy? here's a link to one and its specs.

[http://www.directron.com/x370206us.html]("http://www.directron.com/x370206us.html")

Features:
AMD Dual-Core E-450 APU Platform
Genuine Windows 7 Home Premium 64 bit
13" Widescreen Display with 16:9 LED Backlight Technology
AMD Radeon HD6320 Discrete-Class Graphic Card
4GB DDR3 System Memory
500GB Hard Drive Capacity
SRS Premium Sound Speakers
HDMI (High Definition Multimedia Interface) Output
Built-in 1.3 Mega Pixels webcam
802.11 b/g/n Wireless LAN
BACK TO TOP


Specifications:
Part Number: 
- 9S7-135612-206
Operating System: 
- Genuine Windows 7 Home Premium 64 bit
CPU: 
- AMD Dual-Core E450 APU Platform 
- 1.65 GHz
Memory: 
- 4GB DDR3 Memory
Chipset: 
- A50M FCH
Display: 
- 13" Widescreen Display with 16:9 LED Backlight Technology 
- Max Resolution: 1366 x 768
Webcam: 
- Yes
Graphics: 
- AMD Radeon HD6320
Hard Drive: 
- 500GB SATA 7200RPM
Optical Drive: 
- None
Onboard LAN: 
- Gigabit Ethernet
WLAN: 
- 802.11 b/g/n
Firewire: 
- No
USB: 
- 2
External Ports: 
- USB2.0 X 2 
- VGA (15-pin, D-Sub) X 1 
- HDMI X 1 
- Mic-in X 1 
- Headphone X 1
Card Reader: 
- 4-in-1 Card Reader (SD/SDHC/MMS/ MS)
Bluetooth: 
- No
Fingerprint Reader: 
- No
Power: 
- 8-Cell Lithium Polymer
Weight: 
- 3.85 lbs
Dimensions: 
- 12.77" (L) x 8.94" (W) x 0.9" (H)

---

### Post by socioteq@gmail.com on 2011-12-31
Oh and I forgot to mention that I am running Ubuntu Lucid 10.04
Kernel - 2.6.32-37 generic.

From what I've read about the Intel drivers, the firmware is distribution independent, so it's supposed to work on any linux.  Has anyone at all tried this?  I need to come up with a solution to this problem before the 11th of January before school starts.  I'll be using this system pretty intensely for my last semester in medical school.

I appreciate any inquiries! Thanks in advance

---

### Post by socioteq@gmail.com on 2012-01-01
::BUMP::
Is anyone out there?

---

### Post by marcio123 on 2012-02-07
I had the same problem. You need to activate "function keys" and after that with FN+ F8 turn on wifi . Wifi LED should be ON.

After restart it should work.


If You dont know how to activate FN 

In terminal
**sudo gedit /etc/default/grub**
in line GRUB_CMDLINE_LINUX_DEFAULT add **acpi_osi=Linux**
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_osi=Linux**"
 
SAVE and run:
 **sudo update-grub2**

---

