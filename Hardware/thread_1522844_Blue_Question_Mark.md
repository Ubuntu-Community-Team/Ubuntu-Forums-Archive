---
title: "Blue Question Mark"
date: 2010-07-02
forum: Hardware
---

### Post by WarriorAsh on 2010-07-02
Hi, I have been using windows forever and I've just installed Ubuntu 10.04. I am a new user so please reply as newbie friendly as possible :-(
I was having a real hard time finding help and then I finally decided to make a post...

**Question:** I have installed Gnome Device Manager (I think, not sure if I installed it correctly.. Everything is so confusing) In the device manager there are soo many Blue question marks. Can anyone help me solve it? @_@
I've taken some screenshot. 
[http://cid-cb6f26bfd84c7806.photos.live.com/self.aspx/New%20album/Screenshot.png]("http://cid-cb6f26bfd84c7806.photos.live.com/self.aspx/New%20album/Screenshot.png")
[http://cid-cb6f26bfd84c7806.photos.live.com/self.aspx/New%20album/Screenshot-1.png](http://cid-cb6f26bfd84c7806.photos.live.com/self.aspx/New%20album/Screenshot-1.png)
[http://cid-cb6f26bfd84c7806.photos.live.com/self.aspx/New%20album/Screenshot-2.png](http://cid-cb6f26bfd84c7806.photos.live.com/self.aspx/New%20album/Screenshot-2.png)
[http://cid-cb6f26bfd84c7806.photos.live.com/self.aspx/New%20album/Screenshot-3.png](http://cid-cb6f26bfd84c7806.photos.live.com/self.aspx/New%20album/Screenshot-3.png)

And apart from that i have no clue how to get my inbuild webcam to work :(

Can anyone help me with the question marks please? I feel soo lost.. and everything looks so weird :frown:

Thanks a lot.
Ash.

---

### Post by davidmohammed on 2010-07-02
sorry no idea about the question marks - never used that myself.

anyway - welcome.

choose from the menu Accessories - Terminal

type the following

lspci

copy and paste the text displayed in a reply here.

then type

lsusb

copy and paste the text displayed in a reply here.


The information supplied will indicate what devices (usb and pci) that you have.  Make sure your usb devices are switched on before running this.

---

### Post by WarriorAsh on 2010-07-02
**Copy - Paste **

avinash@Lazy-Laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

avinash@Lazy-Laptop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 15d9:0a4d Dexon 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 090c:37a2 Feiya Technology Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**mmm.. :/ The only usb devices im using is my mouse @_@**

---

### Post by davidmohammed on 2010-07-02
Dont know is the answer - your webcam doesnt appear to be connected.  Its not recognised as a pci device.

The two usb devices look like a modem of some sort and a flash drive.  Am I correct?

What is you PC manufacturer and exact model?

---

### Post by WarriorAsh on 2010-07-02
Hmm.. @_@ I dont know what do you mean  by usb devices... The only thing that i have connected by usb is my mouse... other than that I do have a flash card slot.. mic  webcam HDMI port, ethernet thingy.. 3x usb slots.. :(

My laptop is Compaq Presario CQ61-324SA 
Nd i knew that something wont work thats why i wrote its name down b4 i installed ubuntu on top of win 7 D:

my webcam is HP Webcam 101 @_@
hope it helps..

I would be more happy if i could fix all my unknown devices and Unknown buttons? O_O

Thanks. Please do reply if any more info is needed :(

---

### Post by davidmohammed on 2010-07-03
another quick test to see if your webcam is recognised

please copy and paste the following code

dmesg | grep -i webcam

note the numbers on the left hand side - e.g.

[   11.789933] Linux video capture interface: v2.00
[   11.889793] cfg80211: Calling CRDA to update world regulatory domain
[   11.960481] uvcvideo: Found UVC 1.00 device HP Webcam-101 (0408:03f4)
[   11.962096] input: HP Webcam-101 as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input8
[   11.964108] usbcore: registered new interface driver uvcvideo
[   11.964112] USB Video Class driver (v0.1.0)

now type dmesg

match the left hand numbers to the output.  see if you can see something similar to the above.  If you can - good news - your webcam is indeed recognised.


Next step is to find a program that will activate and display your webcam.

try starting software center and searching for webcam

install "Cheese"
Run this - it should see your webcam.

---

