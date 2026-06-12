---
title: "Slow USB transfer; ehci_hcd module not loaded"
date: 2008-11-02
forum: Hardware
---

### Post by qhex16 on 2008-11-02
It appears that Ubuntu 8.10 is not using USB 2.0. lsmod does not show any entry with "ehci" in it. lsusb says that I'm using a "1.1 root hub", and copying a file to a USB drive happens at 1,000 KB/s (about 7.8 Mbps, when USB 2.0 is 480 Mbps!).

How can I get Ubuntu to take advantage of USB 2.0?

This is a relatively new computer, with an ECS G31T-M motherboard. I've tried both enabling and disabling the "Legacy USB" setting in BIOS.

```
$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9500 GT (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

$ lsusb
Bus 002 Device 003: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:c317 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by scweston on 2008-11-03
Hey,

I've never 'bumped' before, here I go!

I believe I'm having exactly the same problem. I'm copying some files from an external USB drive and it is incredibly slow compared with hardy. I also believe it may be causing some of my other issues which I've posted separately about with my hauppauge nova-t 500 (although a PCI device it has an integrated PCI to USB adapter on which the tuners and remote devices are connected).

So I would also appreciate the help.

Stephen.

---

### Post by jpeery on 2008-11-03
Try forcing ehci

sudo modprobe -a ehci_hcd

If that doesn't work, post your lsusb and dmesg

---

### Post by scweston on 2008-11-03
Hi,

Forcing ehci_hcd didn't appear to have an effect.

Here's my lsusb output:

```
stephen@stephen-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04a9:1718 Canon, Inc. MP600 Storage
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 2040:9950 Hauppauge 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 001 Device 004: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 001 Device 003: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
stephen@stephen-desktop:~$
```

Here's the output from dmesg | grep usb:

```
stephen@stephen-desktop:~$ dmesg | grep usb
[    1.886325] usbcore: registered new interface driver usbfs
[    1.886356] usbcore: registered new interface driver hub
[    1.887917] usbcore: registered new device driver usb
[    1.951211] usb usb1: configuration #1 chosen from 1 choice
[    2.332332] usb 1-1: new low speed USB device using ohci_hcd and address 2
[    2.344346] usb usb2: configuration #1 chosen from 1 choice
[    3.008029] usb 2-8: new high speed USB device using ehci_hcd and address 4
[    3.151208] usb 2-8: configuration #1 chosen from 1 choice
[    3.461028] usb 1-1: new low speed USB device using ohci_hcd and address 3
[    3.676805] usb 1-1: configuration #1 chosen from 1 choice
[    3.993019] usb 1-2: new low speed USB device using ohci_hcd and address 4
[    4.214950] usb 1-2: configuration #1 chosen from 1 choice
[    4.217310] usbcore: registered new interface driver hiddev
[    4.222532] input: MLK Trust Keyboard 14909 as /devices/pci0000:00/0000:00:02.0/usb1/1-1/1-1:1.0/input/input1
[    4.249154] input,hidraw0: USB HID v1.00 Keyboard [MLK Trust Keyboard 14909] on usb-0000:00:02.0-1
[    4.259517] input: MLK Trust Keyboard 14909 as /devices/pci0000:00/0000:00:02.0/usb1/1-1/1-1:1.1/input/input2
[    4.293191] input,hiddev96,hidraw1: USB HID v1.00 Mouse [MLK Trust Keyboard 14909] on usb-0000:00:02.0-1
[    4.308913] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input3
[    4.329155] input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A] on usb-0000:00:02.0-2
[    4.329179] usbcore: registered new interface driver usbhid
[    4.329182] usbhid: v2.6:USB HID core driver
[    4.556813] usb usb3: configuration #1 chosen from 1 choice
[    4.839725] usb usb4: configuration #1 chosen from 1 choice
[    4.877029] usb 3-1: new high speed USB device using ehci_hcd and address 2
[    5.008996] usb 3-1: configuration #1 chosen from 1 choice
[    5.009423] usbcore: registered new interface driver libusual
[    5.016846] usbcore: registered new interface driver usb-storage
[    5.017037] usb-storage: device found at 4
[    5.017040] usb-storage: waiting for device to settle before scanning
[    5.045590] usb usb5: configuration #1 chosen from 1 choice
[   10.017611] usb-storage: device scan complete
[   16.547067] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x04A9 pid 0x1718
[   16.547105] usbcore: registered new interface driver usblp
[   17.794881] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   17.794886] firmware: requesting dvb-usb-dib0700-1.20.fw
[   18.879774] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   19.620046] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   19.620895] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   20.251287] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   20.822061] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:09.0/0000:01:02.2/usb3/3-1/input/input7
[   20.857825] dvb-usb: schedule remote query interval to 150 msecs.
[   20.857834] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   20.858123] usbcore: registered new interface driver dvb_usb_dib0700
[  119.592051] usb 2-3: new high speed USB device using ehci_hcd and address 5
[  119.704056] usb 2-3: device descriptor read/64, error -71
[  119.920416] usb 2-3: device descriptor read/64, error -71
[  120.136037] usb 2-3: new high speed USB device using ehci_hcd and address 6
[  120.248052] usb 2-3: device descriptor read/64, error -71
[  120.464058] usb 2-3: device descriptor read/64, error -71
[  120.680038] usb 2-3: new high speed USB device using ehci_hcd and address 7
[  121.088037] usb 2-3: device not accepting address 7, error -71
[  121.200059] usb 2-3: new high speed USB device using ehci_hcd and address 8
[  121.608049] usb 2-3: device not accepting address 8, error -71
[  122.064048] usb 1-3: new full speed USB device using ohci_hcd and address 5
[  122.265234] usb 1-3: not running at top speed; connect to a high speed hub
[  122.279038] usb 1-3: configuration #1 chosen from 1 choice
[  122.289423] usb-storage: device found at 5
[  122.289443] usb-storage: waiting for device to settle before scanning
[  127.289912] usb-storage: device scan complete
stephen@stephen-desktop:~$ 
```

I appreciate your help.
Stephen

---

### Post by jpeery on 2008-11-03
Hm, well, sadly that's what I *THOUGHT* would work, lemme do some digging, I had the same issue with my thumbdrive, and modprobe -r then -a seemed to fix it...
Jason

---

### Post by scweston on 2008-11-03
Hi Jason,

I rebooted and tried your suggestion again. This time however, after typing in the 'sudo modprobe -a echi_hcd' command. I disconnected the USB harddrive and reconnected it in to the same USB port. This time yay it worked!

Although, that doesn't really fix the problem completely as I would like to use the usb drive without having to first type in a command to terminal. Also, if this is the same problem as I'm getting with my hauppauge nova-t 500 card then I can't just disconnect it if its not working at the correct speed, type in the command and reconnect it.

So, Basically, how can I get things to work first time?

Stephen

---

### Post by jpeery on 2008-11-03
Good question, that's what I don't know that I'd like to.  I've just been running the command as needed, I would like to know myself, HOWEVER, having said that, I've not had that issue since I went to Intrepid (just yesterday), so it *SEEMS* to work fine for me without -r then -a ehci...
Are you still on 8.04?
Jason

---

### Post by scweston on 2008-11-03
LOL... I just upgraded from 8.04 to Intrepid and have just started having the problem.

Although there is a lot of things that are great about Intrepid, I had a lot more success getting things working properly in Hardy. Maybe I'll go back to hardy and wait for the next Ubuntu release, hopefully all will be fixed by then.

Although, I'm still open to suggestions to fix this from anyone! I really would prefer to stick with Intrepid if possible.

Stephen

---

### Post by Menthu_Rae on 2008-11-11
I'm also getting slow transfer rates under Ubuntu 8.10.

I have a 2.5" WD 160GB drive that is transferring ~6MB/sec.

When I put the drive on my Windows XP machine, it's about 32MB/sec (using HDTune) and when I put it on my **Ubuntu 8.04** machine it's also about 32MB/sec (using hdparm -Tt).

I checked the loaded usb modules between 8.04 and 8.10 (on the different machines) and they appear the same...

i.e. lsmod | grep usb

gives the same modules for both 8.04 and 8.10.

Doing lspci on 8.04 shows USB2 EHCI controllers.

On 8.10 it shows USB UHCI controllers...

Can anyone please help more? My 8.10 box is used for torrents, so it's very important I have fast transfer speed (so I can copy to my main PC).

I can confirm that copying from the internal HDD to my main PC works at about 30MB/sec - so it's not a samba issue.

---

### Post by Menthu_Rae on 2008-11-13
> **Menthu_Rae said:**
> Can anyone please help more? My 8.10 box is used for torrents, so it's very important I have fast transfer speed (so I can copy to my main PC).

OK, I've just gone and installed 8.04 on the PC which **was** using 8.10.

WD 2.5" 320GB USB HDD:

Ubuntu 8.10 - hdparm -Tt - ~5.5MB/sec
Ubuntu 8.04 - hdparm -Tt - ~35MB/sec

Hrmmm :mad:

I don't know how to solve it in 8.10 - but I can definitely say that using 8.04 - it's working fine/much faster!

---

### Post by beruic on 2008-12-29
Just installed Intrepid. Really slow USB transfer rates :( However:

```
$lsmod | grep ehci_hcd
ehci_hcd               43276  0 
usbcore               148848  7 usb_storage,libusual,uvcvideo,usbhid,uhci_hcd,ehci_hcd

$lsusb
Bus 007 Device 003: ID 05a9:7670 OmniVision Technologies, Inc. 
Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 008: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 005 Device 006: ID 046d:c01a Logitech, Inc. M-BQ85 Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Is there an open bug for this?
I'm no expert in this, but 'lsmod | grep usb2' returns nothing. Shouldn't there be something?

---

### Post by beruic on 2008-12-29
Found the bug: [https://bugs.launchpad.net/gvfs/+bug/197762](https://bugs.launchpad.net/gvfs/+bug/197762)

It's a kernel problem. Booted kernel 2.6.27-7-generic and got nice transfer rates :)

---

### Post by Menthu_Rae on 2009-12-22
OMG, **one year later** and this still isn't fixed.

I have tried:

**Ubuntu 8.04: **Works fine, 25-30MB/s transfer rates from SATA -> USB HDD
**Ubuntu 8.10: **Slow! 3-5MB/s transfer rates from SATA -> USB HDD
**Ubuntu 9.04: **Slow! 3-5MB/s transfer rates from SATA -> USB HDD
**Ubuntu 9.10: **Slow! 3-5MB/s transfer rates from SATA -> USB HDD
**Ubuntu 10.04 Alpha 1: **Slow! 3-5MB/s transfer rates from SATA -> USB HDD

I'm gathering all the info I can at the moment to submit a proper bug report. Rage!

---

### Post by jeffltw on 2010-07-31
Read the following. It can get a bit detailed but it does work. Make sure you read the two links at the end.

[http://ubuntuforums.org/showpost.php?p=8124833&postcount=294](http://ubuntuforums.org/showpost.php?p=8124833&postcount=294)

hope it helps

---

