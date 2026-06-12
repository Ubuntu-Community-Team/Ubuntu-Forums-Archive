---
title: "Troubles with etc/network/interfaces"
date: 2005-11-19
forum: General Help
---

### Post by HugiAsgeirsson on 2005-11-19
Hi

I am attempting to install my Netgear MA111 card, by following these instructions: [https://wiki.ubuntu.com/MA111Howto](https://wiki.ubuntu.com/MA111Howto)

It turns out like this:

```
hugi@Klas-ubuntu:~$ lsmod | grep prism
prism2_usb             67204  0
p80211                 30992  1 prism2_usb
usbcore               104188  6 spca5xx,prism2_usb,usb_storage,ehci_hcd,uhci_hcd
hugi@Klas-ubuntu:~$ alias wlan0 prism2_usb
bash: alias: wlan0: not found
bash: alias: prism2_usb: not found
hugi@Klas-ubuntu:~$ sudo apt-get install linux-wlan-ng
Password:
Reading package lists... Done
Building dependency tree... Done
linux-wlan-ng is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hugi@Klas-ubuntu:~$ sudo gedit /etc/network/interfaces

```

Up to now everything seems fine, so I edit the etc/network/interfaces file to look like this (what I highlight is what I added):

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

[COLOR="Red"]auto wlan0 #comment if you don't want it boot at start
     wireless_mode managed
     wireless_essid your_essid
# Comment out the lines below if you don't have wireless encryption. Taken from /usr/share/doc/linux-wlan-ng/README.Debian
    # wireless_enc on
    # wlan_ng_key0 xx:xx:xx:xx:xx
    # wlan_ng_authtype opensystem[/COLOR]


```

Then I reboot and try to issue the "sudo ifup wlan0" command, but that only ends me with:

```
hugi@Klas-ubuntu:~$ sudo ifup wlan0
/etc/network/interfaces:15: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"

```

I gather there is something wrong on line 15 in the interfaces file, which would be "wireless_mode managed", however I can't see where this strays from the instructions.

Any ideas?

---

### Post by az on 2005-11-19
iface wlan0 inet dhcp


Try adding that to the stanza.


You should be able to configure it throught the networking tool, though.

If you cannot, there is a bug about that in bugzilla:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=15346](http://bugzilla.ubuntu.com/show_bug.cgi?id=15346)

---

### Post by HugiAsgeirsson on 2005-11-19
Hmmm, I don't think that worked. It just repeated "/etc/network/interfaces:15: misplaced option"

And the card doesn't show up in the networking tool.

---

### Post by Lambert on 2005-11-19
If it's not showing up in networking, try command iwconfig. If you don't see anything here either then there is a problem somewhere around the driver.

From terminal type 

sudo lshw -businfo

find your device and notice it's class; then

sudo lshw -C <class>

the section on the device notice a line [COLOR=DarkRed]configuration:

[COLOR=Black]notice driver=???? what does it say?

You can post the output of lshw here along with lspci for more help.
[/COLOR][/COLOR]

---

### Post by HugiAsgeirsson on 2005-11-19
I tried iwconfig, but that turned up nothing:

```
 hugi@Klas-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

wlan0     no wireless extensions.

```

Ok, so I ran lshw (highlighting my device):

```
hugi@Klas-ubuntu:~$ sudo lshw -businfo
Bus info                   Device    Class       Description
============================================================
                                     system      To Be Filled By O.E.M.
                                     bus         P4C800-E
                                     memory      BIOS
cpu@0                                processor   Intel(R) Pentium(R) 4 CPU 2.80GHz
                                     memory      L1 cache
                                     memory      L2 cache
                                     memory      L3 cache
                                     processor   Logical CPU
                                     processor   Logical CPU
                                     memory      System Memory
                                     memory      PartNum0
                                     memory      PartNum1
                                     memory      PartNum2
                                     memory      PartNum3
pci@00:00.0                          bridge      82875P/E7210 Memory Controller Hub
pci@00:01.0                          bridge      82875P Processor to AGP Controller
pci@01:00.0                          display     RV350 AR [Radeon 9600]
pci@01:00.1                          display     RV350 AR [Radeon 9600] (Secondary)
pci@00:03.0                          bridge      82875P/E7210 Processor to PCI to CSA Bridge
pci@02:01.0                eth0      network     82547EI Gigabit Ethernet Controller (LOM)
pci@00:1d.0                          bus         82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
usb@1                      usb1      bus         Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
pci@00:1d.1                          bus         82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
usb@2                      usb2      bus         Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
usb@2:2                              generic     Generic USB device
pci@00:1d.2                          bus         82801EB/ER (ICH5/ICH5R) USB UHCI #3
usb@3                      usb3      bus         Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI #3
usb@3:2                              generic     WebCam NX Pro
pci@00:1d.3                          bus         82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
usb@4                      usb4      bus         Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
pci@00:1d.7                          bus         82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
usb@5                      usb5      bus         Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
usb@5:1                    scsi3     storage     LaCie Hard Drive USB
scsi@3.0:0.0               /dev/sda  disk        6Y160P0
pci@00:1e.0                          bridge      82801 PCI Bridge
pci@03:03.0                          bus         IEEE 1394 Host Controller
pci@03:04.0                          storage     PDC20378 (FastTrak 378/SATA 378)
pci@03:0b.0                          multimedia  SB Audigy
pci@03:0c.0                eth1      network     RTL-8139/8139C/8139C+
pci@00:1f.0                          bridge      82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
pci@00:1f.1                          storage     82801EB/ER (ICH5/ICH5R) IDE Controller
ide@0                      ide0      bus         IDE Channel 0
ide@0.0                    /dev/hda  disk        ExcelStor Technology J840
ide@1                      ide1      bus         IDE Channel 1
ide@1.0                    /dev/hdc  disk        SAMSUNG CDRW/DVD SM-352F
pci@00:1f.3                          bus         82801EB/ER (ICH5/ICH5R) SMBus Controller
pci@00:1f.5                          multimedia  82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
firewire@0010b9f701225613  scsi4     storage
scsi@4.0:1.0               /dev/sdb  disk        OneTouch
scsi@0                     scsi0     storage
scsi@1                     scsi1     storage
scsi@2                     scsi2     storage
                           wlan0     network     Ethernet interface
hugi@Klas-ubuntu:~$ sudo lshw -C generic
  [COLOR="Red"]*-usb
       description: Generic USB device
       vendor: NetGear, Inc.
       physical id: 2
       bus info: usb@2:2
       version: 1.32
       capabilities: usb-1.10
       configuration: driver=prism2_usb maxpower=500mA speed=12.0MB/s[/COLOR]
  *-usb
       description: Generic USB device
       product: WebCam NX Pro
       vendor: Creative Technology, Ltd
       physical id: 2
       bus info: usb@3:2
       version: 1.00
       capabilities: usb-1.10
       configuration: driver=spca5xx maxpower=160mA speed=12.0MB/s

```

Then I ran lspci for additional stats:

```
 hugi@Klas-ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82875P Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82875P Processor to AGP Controller (rev 02)0000:00:03.0 PCI bridge: Intel Corp. 82875P Processor to PCI to CSA Bridge (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
0000:02:01.0 Ethernet controller: Intel Corp. 82547EI Gigabit Ethernet Controller (LOM)
0000:03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:03:04.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
0000:03:0b.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
0000:03:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```


Thats the output I got. Any ideas?

---

### Post by az on 2005-11-19
See the bug report.  I am in the same boat.
[http://bugzilla.ubuntu.com/show_bug.cgi?id=15346](http://bugzilla.ubuntu.com/show_bug.cgi?id=15346)

---

### Post by HugiAsgeirsson on 2005-11-19
Ah, that sucks. I guess I'll just have to wait until someone solves it :/.

---

### Post by az on 2005-11-19
Copy this script and save it as /etc/hotplug/usb/prism2_usb:



wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable

wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable

wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true

wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true

wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0

wlanctl-ng wlan0 dot11req_mibset
mibattribute=dot11WEPDefaultKey0="(mysecretWEPkey)"

wlanctl-ng wlan0 lnxreq_autojoin ssid="(myssid)" authtype="sharedkey"

sleep 2

dhclient wlan0





And you are good to go.  It is mentioned in the bug report.  It is not a conventional way to do things, but it works.

---

### Post by archibald on 2005-12-16
if you read that wiki carefully, you'd see that he doesnt tell you to type in "alias wlan0 prism2_usb" into the terminal...
just read carefully. also try using places->administration->networking instead of editing "etc/networking/interfaces" file!
I myself am having trouble with this on dapper...but you appear to be on breezy, so all should work fine for you??

---

