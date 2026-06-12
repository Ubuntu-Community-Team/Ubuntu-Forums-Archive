---
title: "SD Card reader not working on Acer Aspire One"
date: 2010-06-10
forum: Hardware
---

### Post by mordalo on 2010-06-10
Greetings;

I purchased a new Acer Aspire One (NAV50) a month or so ago.  It shipped with Win7, but I wiped it and installed Lucid on it after, oh, five minutes.

The SD card reader worked fine in Win7 but has not worked with Ubuntu.  I've tried three installs, both with a card in the slot and without. No matter what I do, no SD card will appear.

Here's the results of lsusb:

> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0cf2:6250 ENE Technology, Inc. 
Bus 001 Device 003: ID 04f2:b19d Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

...and here's lspci:

> 00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

I'm not sure what else to do.  I've done the Google thing and tried the recommendations they've offered, to no avail.  Anyone...anyone...got anything?

---

### Post by redcharlie on 2010-06-12
Same problem, although it's on a ZaReason Teo, not an AA1.

```
dmesg | tail
``` gives

```
[  262.540160] usb 1-3: new high speed USB device using ehci_hcd and address 3
[  262.673845] usb 1-3: configuration #1 chosen from 1 choice

```

usb-storage module does not support it. See:
[https://lists.one-eyed-alien.net/pipermail/usb-storage/2010-April/005210.html](https://lists.one-eyed-alien.net/pipermail/usb-storage/2010-April/005210.html)

---

### Post by dino99 on 2010-06-12
into a terminal: pccardctl status

[http://www.linuxquestions.org/questions/ubuntu-63/how-to-mount-sd-card-on-ubuntu-536646/#post2681052](http://www.linuxquestions.org/questions/ubuntu-63/how-to-mount-sd-card-on-ubuntu-536646/#post2681052)

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

---

### Post by mordalo on 2010-06-13
> **dino99 said:**
> into a terminal: pccardctl status

[http://www.linuxquestions.org/questions/ubuntu-63/how-to-mount-sd-card-on-ubuntu-536646/#post2681052](http://www.linuxquestions.org/questions/ubuntu-63/how-to-mount-sd-card-on-ubuntu-536646/#post2681052)

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

pccardctl status reports back...nothing.  Sigh...

---

### Post by the-penguin on 2010-07-14
has anyone found out anything new regarding this subject? I have an AAOne here as well and the SD card reader isn't working as well. 

thatnks in advance

the-penguin

---

### Post by Quarn on 2010-07-28
I just installed it for someone on a ACER ASPIRE and got the same problem.. 
after praising UBUNTU so much now I look like a moron :D

I work so well on ma EeePC from ASUS..:popcorn:

---

### Post by jegerjensen on 2010-08-11
Same computer, same problem.  Here is some information from lsusb:

```

[~]$ sudo lsusb -d 0cf2:6250 -v

Bus 001 Device 005: ID 0cf2:6250 ENE Technology, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0cf2 ENE Technology, Inc.
  idProduct          0x6250 
  bcdDevice            1.00
  iManufacturer           1 ENE Flash  
  iProduct                2 UB6250       
  iSerial                 4 606569746801
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              498mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      6 
      bInterfaceProtocol     80 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

---

### Post by croques on 2010-08-11
I'm just passing through but have an Acer Aspire AOA 150 that works with the SD card on Ubuntu 10.4 (and 9.4 for that matter)

I seem to remember the trick is to put the sd card in the slot and then power up the machine. One side is better than the other if I remember correctly. I use the RHS slot. Google will have loads of stuff about the issue, I'm sure.

On a side note I use a 16gb micro sd card in a phone. I also have a USB carrier for it and is most effective. But it also came with an SD sized holder - so in future I will buy micro SD's.

---

### Post by mordalo on 2010-08-11
> **croques said:**
> I seem to remember the trick is to put the sd card in the slot and then power up the machine. One side is better than the other if I remember correctly. I use the RHS slot. Google will have loads of stuff about the issue, I'm sure.

I saw that as well, as well as an article that says to have a SD card in the slot when you install Ubuntu.

Neither trick works, alas.  This model is different than yours, with only one SD slot (on the right).

I read somewhere else (forgive me for not bookmarking or sharing the link) that there's possibly a driver issue at work here, or something in the Kernel that's causing it to not function.  They've indicated that with this model netbook, the SD card slot doesn't work period.  Also, Bluetooth doesn't function (it says there's Bluetooth in this laptop, but the FN+F3 key does nothing and no module shows up on a scan).

Hopefully, with 10.10, this problem will be resolved, but I'm not holding my breath...

---

### Post by jontyrp on 2010-08-14
> **mordalo said:**
> I saw that as well, as well as an article that says to have a SD card in the slot when you install Ubuntu.
 
Neither trick works, alas. This model is different than yours, with only one SD slot (on the right).
 
I read somewhere else (forgive me for not bookmarking or sharing the link) that there's possibly a driver issue at work here, or something in the Kernel that's causing it to not function. They've indicated that with this model netbook, the SD card slot doesn't work period. Also, Bluetooth doesn't function (it says there's Bluetooth in this laptop, but the FN+F3 key does nothing and no module shows up on a scan).
 
Hopefully, with 10.10, this problem will be resolved, but I'm not holding my breath...
 
Hi,
I've also got an Acer AspireONE 532h netbook. I've had both 9.10 & 10.04 running on it and had no luck with the Media Card Reader. I believe it's an issue of there not being appropriate drivers available, for Linux, for the ENE Technologies UB6250 USB Mass Storage Controller. Certainly the only drivers I can find are for Windows, as from this site;
[http://www.station-drivers.com/page/ene-tech.htm](http://www.station-drivers.com/page/ene-tech.htm)
 
Also it would be wrong to think that the Media Card Reader is natively supported in Windows, it's not. You have to install the appropriate drivers from the Acer Support Website, before it works. I know, as I've just installed Windows 7 Pro x86, and it was only after installing the ENE Driver Package from Acer that I was able to access cards in the media slot. I would therefore suspect that until someone writes a specific Linux driver for the ENE UB6250 USB Mass Storage Controller, the media card slot will never work in Ubuntu, or any other distro. I don't have the skills to do that myself, and it doesn't seem likely, to me, that either Acer, or ENE are going to do it either, so anyone game..........?
 
On anther note, I was able to use Bluetooth in Ubuntu without any problems on my system. Are you sure you have a Bluetooth equiped model? It's a Broadcom 2046 Bluetooth 2.1+EDR chip in my AspireONE, and this worked fine in both 9.10 & 10.04, as well as now in Windows 7.
 
(If you are wondering why I'm now running Windows 7, it was because of an issue with the Atheros WiFi adaptor. I could never get a reliable/stable connection with it in Ubuntu, so in the end I've had to give up and go over to Windows instead, where the WiFi works flawlessly.)
 
Jonathan

---

### Post by mordalo on 2010-08-17
> **jontyrp said:**
> On anther note, I was able to use Bluetooth in Ubuntu without any problems on my system. Are you sure you have a Bluetooth equiped model? It's a Broadcom 2046 Bluetooth 2.1+EDR chip in my AspireONE, and this worked fine in both 9.10 & 10.04, as well as now in Windows 7.

I did a little research on this particular model, and it doesn't have a Bluetooth module installed (even if the F3 key has the Bluetooth icon under it).  It appears that you can order a BT module for this model.

Oh, and I wouldn't even begin to know how to write a driver module.  Anyone else up for a challenge?

---

### Post by the-penguin on 2010-08-26
I too heard, or read, on the net that the problem originally lies with the BIOS of the computer and that the problem can be fixed by updating the BIOS, but I'm always a bit paranoid when it comes to messing around in the BIOS or something. [-o<

jason

---

### Post by the-penguin on 2010-09-03
what does your computer say when you try the command ```
tail -f /var/log/messages 
```

jason

---

### Post by sid1950 on 2010-09-10
This works for OpenSUSE 11.2 on an Acer One Aspire AOA110:
[http://old-en.opensuse.org/OpenSUSE_on_the_Aspire_One#Card_readers](http://old-en.opensuse.org/OpenSUSE_on_the_Aspire_One#Card_readers)

Any idea where the equivalent to /etc/sysconfig would be on Ubuntu 10.04? I am using the Netbook Remix and it is a great deal faster than Suse, and the interface is very good. The card reader works if you boot with a card in the slot, but having had the above work in Suse I need to sort it for Ubuntu. Everything else works fine.

**UPDATE**
After searching this forum for "acer card reader", I found this:
[http://ubuntuforums.org/showthread.php?t=974525](http://ubuntuforums.org/showthread.php?t=974525)

And tried a few variations. In the end I just added the line: pciehp to the /etc/modules file like this:
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
pciehp
Now the left card reader works everytime. I can't get the right reader to work yet.

I also looked at the instructions here:
[https://help.ubuntu.com/community/AspireOne/110L#Card Readers](https://help.ubuntu.com/community/AspireOne/110L#Card Readers)  but they seem to be a bit out of date.

Since I mainly use this netbook for the web, e-mail, and to look at photos from my digital camera, I am perfectly happy with the functionality now have.

---

### Post by mordalo on 2010-09-10
> **the-penguin said:**
> what does your computer say when you try the command ```
tail -f /var/log/messages 
```

jason

Sorry, Jason.  I've been offline for awhile.

```

Sep 10 15:39:48 onestar-acer kernel: [   18.697177] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 10 15:39:48 onestar-acer kernel: [   18.762417] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 10 15:39:51 onestar-acer kernel: [   22.114845] ppdev: user-space parallel port driver
Sep 10 15:40:21 onestar-acer nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Sep 10 15:40:21 onestar-acer nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Sep 10 15:40:33 onestar-acer kernel: [   63.334413] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Sep 10 15:43:32 onestar-acer kernel: [  265.040211] __ratelimit: 3 callbacks suppressed
Sep 10 15:43:32 onestar-acer kernel: [  265.040224] gnome-power-man[1316]: segfault at 1 ip 0041f13b sp bfee2700 error 4 in libgtk-x11-2.0.so.0.2000.1[322000+3cd000]
Sep 10 15:51:20 onestar-acer kernel: [  732.972134] usb 1-5: new high speed USB device using ehci_hcd and address 5
Sep 10 15:51:20 onestar-acer kernel: [  733.107139] usb 1-5: configuration #1 chosen from 1 choice

```

The command prompt locks at this point and doesn't drop me back to a prompt.  I have to CTRL-C to continue.  Not sure if that's normal...

P.S.  The info above is with a card in the slot.

---

### Post by mordalo on 2010-09-10
> **sid1950 said:**
> This works for OpenSUSE 11.2 on an Acer One Aspire AOA110:
[http://old-en.opensuse.org/OpenSUSE_on_the_Aspire_One#Card_readers](http://old-en.opensuse.org/OpenSUSE_on_the_Aspire_One#Card_readers)

Any idea where the equivalent to /etc/sysconfig would be on Ubuntu 10.04? I am using the Netbook Remix and it is a great deal faster than Suse, and the interface is very good. The card reader works if you boot with a card in the slot, but having had the above work in Suse I need to sort it for Ubuntu. Everything else works fine.

**UPDATE**
After searching this forum for "acer card reader", I found this:
[http://ubuntuforums.org/showthread.php?t=974525](http://ubuntuforums.org/showthread.php?t=974525)

And tried a few variations. In the end I just added the line: pciehp to the /etc/modules file like this:

Now the left card reader works everytime. I can't get the right reader to work yet.

I also looked at the instructions here:
[https://help.ubuntu.com/community/AspireOne/110L#Card Readers](https://help.ubuntu.com/community/AspireOne/110L#Card Readers)  but they seem to be a bit out of date.

Since I mainly use this netbook for the web, e-mail, and to look at photos from my digital camera, I am perfectly happy with the functionality now have.

Sid, I saw these as well, but it doesn't work for my particular netbook. There's only one card reader in the 250h, and I installed Ubuntu both with and without a card in the slot.

I did notice that, when a card is inserted in the slot, the drive indicator light does come on, which pretty much confirms it's a driver issue for this particular model.

---

### Post by the-penguin on 2010-09-13
@ Moraldo 

the command i gave you will monitor some log files, so when it freezes it really just continues to monitor the log files.. if you run the command and then remove, or insert the SD card the terminal output will change..

---

### Post by mordalo on 2010-09-15
> **the-penguin said:**
> @ Moraldo 

the command i gave you will monitor some log files, so when it freezes it really just continues to monitor the log files.. if you run the command and then remove, or insert the SD card the terminal output will change..

Ah.  Pardon my ignorance.  :D

The last two lines:

[CODE]
Sep 10 15:51:20 onestar-acer kernel: [  732.972134] usb 1-5: new high speed USB device using ehci_hcd and address 5
Sep 10 15:51:20 onestar-acer kernel: [  733.107139] usb 1-5: configuration #1 chosen from 1 choice
[\CODE]

They appear when the SD card is inserted.  Also, as I might've mentioned, the light on the netbook appears indicating there's a card in the slot.

---

### Post by g01d10x on 2010-10-06
> **the-penguin said:**
> what does your computer say when you try the command ```
tail -f /var/log/messages 
```

jason

Hi Jason :)

I just tried the command, and plugged in a card ..
[1527.800097] usb 1-5: new high speed USB devide using ehci_hcd and address 3
[1527.934473] usb 1-5: configuration #1 chosen from 1 choice

after that I did a lsusb and compared ..

new line that changed from before the card was inserted is :
Bus 001 Device 003: ID 0cf2:6250 ENE Technology, Inc.

So would I be correct then in guessing that Ubuntu can see that something is happening on the Card Reader but doesn't have the driver to do anything about it ?!?!

Cheers from Vancouver :)

---

### Post by mordalo on 2010-10-06
> **g01d10x said:**
> So would I be correct then in guessing that Ubuntu can see that something is happening on the Card Reader but doesn't have the driver to do anything about it ?!?!

Cool.  So who knows how to make a driver?  I'm a hardware geek, not a programmer...

Seriously.  Anyone out there wanna try their hand at compiling a driver?

---

### Post by jlh68 on 2010-10-11
My rlight side SD card reader does not work either.  I am using Ubuntu 10.04LTS.  I did have it work with 9.04, but that was using GRUB and not GRUB2 like version 10.04LTS uses.  I used the patch/fix to the GRUB conf file, but GRUB2 does not have the same file.

So how to get the right side SC card reader to9 work (agan)?

---

### Post by saiprem on 2010-10-12
I had the same problem with the same card reader on my MSI A6200 laptop.  After hours of trying to find a Linux driver I finally bought a cheap Linux USB card reader.

prem

---

### Post by avacado on 2010-10-14
If you are reading thism chances are you have the same card reader.
try open a terminal and type  lsusb and hit enter if you have device Oc2f:6250 then you have the same driver as me.
other distributions have the same problem - no driver.

subscribe to my bug 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852)
this adds weight to the issue

It may take some time for s volunteer developer to write a driver.
In the mean time I suggest you buy a card reader or use your camera as an external drive with the card.

update the linux compatibility netbook page to add your model and problem

---

### Post by scorp123 on 2010-10-24
PFMJI, but I'd like to add that I too have this problem. The netbook in question is a Packard-Bell Dot SE. The "Packard-Bell" brand is now owned by Acer (found this via Google) and very often Packard-Bell netbooks are practically identical to an Acer Aspire Dxxx model. Just the brand sticker on the case is different. So this Packard-Bell Dot SE netbook also has this card reader device:

Bus 001 Device 004: ID 0cf2:6250 ENE Technology, Inc.

So I can't get this to work with Ubuntu 10.04 LTS. Does anyone know if it works with Maverick (Ubuntu 10.10) or are there any chances that it might be working with Ubuntu 11.04?

---

### Post by fmmarzoa on 2011-01-16
Hello guys,

I've also a Packard Bell Dot SE netbook and my card reader does not work neither, even I do not know what device is neither from bot lspci and lsusb.

Here are the outputs for both commands:

fran@marx:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0402:9665 ALi Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


fran@marx:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Intel Corporation WiFi Link 1000 Series



Which of those devices do you figure out that may be the card reader?

Regards,

---

### Post by fmmarzoa on 2011-01-16
Hello again,

Fortunatly I still have a partition with the original Windows XP that comes with the Netbook, and trying the card reader with that XP says that's also an ENE card reader...

No solution yet, though.

Regards,

---

### Post by misanthropist on 2011-02-11
> **scorp123 said:**
>  are there any chances that it might be working with Ubuntu 11.04?

[Yes. Bug #530277]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277")

---

### Post by ibrrfarr on 2011-02-11
Acer Aspire One D255 the only SD card reader is on the right hand side.  I cannot access the SD card either.  See [http://ubuntuforums.org/showthread.php?t=1666533](http://ubuntuforums.org/showthread.php?t=1666533) where I first brought it up for my issue as well.

In all candor, what needs to be done?  I mean if I have 'X' dollars can I simply hire someone to code this up, so-to-speak, and then as I would 'own' the code contribute it here?  I am serious on this question as the card reader is a NECESSITY for my line of work as I take thousands of photos in any given week.

Thanks to all!

---

### Post by misanthropist on 2011-02-12
Hi Ibrrfarr,

The first step to getting a problem fixed is to [file a bug report]("https://help.ubuntu.com/community/ReportingBugs") on launchpad. This bug has already been filed (see my previous post for a link to the bug report) and a fix has been committed for version 11.4 which is scheduled for release in April. 
Once the next version is released you should be able to download an unofficial kernel backport if you don't want to update to 11.4.

If you need it now and are happy hacking your system there is also an explanation on the bug report about how to build the necessary module yourself. Somebody might even be kind enough to build one for your particular release.

---

### Post by ibrrfarr on 2011-02-12
> **misanthropist said:**
> Hi Ibrrfarr,

The first step to getting a problem fixed is to [file a bug report]("https://help.ubuntu.com/community/ReportingBugs") on launchpad. This bug has already been filed (see my previous post for a link to the bug report) and a fix has been committed for version 11.4 which is scheduled for release in April. 
Once the next version is released you should be able to download an unofficial kernel backport if you don't want to update to 11.4.

If you need it now and are happy hacking your system there is also an explanation on the bug report about how to build the necessary module yourself. Somebody might even be kind enough to build one for your particular release.

I made an account but really don't know what bug# or really what/how to track or report.  Perhaps you could give me the # you are talking about or do I need to file a new one?

Would like to see the hack you speak of.  Maybe I can do it; however, I would really appreciate it if someone could walk me through the process.  I have skype so if it's easier that way, by all means PM me!  :)

Found the Bug#.

---

### Post by ibrrfarr on 2011-02-13
So, "installed 2.6.37-rc7" seems to fix the sd card reader?  Can someone send me to a layman's explanation page on how to install this kernel I guess it is?

---

### Post by williamts99 on 2011-02-13
> **ibrrfarr said:**
> So, "installed 2.6.37-rc7" seems to fix the sd card reader?  Can someone send me to a layman's explanation page on how to install this kernel I guess it is?

If you have been thinking of upgrading to the next release of Ubuntu when released, it might be worth it for you to wait.

It's still an ALPHA, so I wouldn't install it, but you can boot it as a LiveCD or USB and test it out before you make any permanent changes.
[http://www.ubuntu.com/testing/natty/alpha2](http://www.ubuntu.com/testing/natty/alpha2)

---

### Post by misanthropist on 2011-02-14
> **ibrrfarr said:**
> So, "installed 2.6.37-rc7" seems to fix the sd card reader?  Can someone send me to a layman's explanation page on how to install this kernel I guess it is?

2.6.37-rc7 == kernel version 2.6.37 release candidate 7 

I would echo williamts99 comment that you should probably wait for a production ready version of the kernel unless you intend to contribute to the testing process. The kernel covers a myriad of things and a  non-production version may break things which are currently working for you.

If time is important the safer route would be to compile the module as described near the end of the bug report. This should have a limited impact if anything goes wrong whereas a kernel update may cause unanticipated problems.

If I get a chance (perhaps unlikely) I will see if I can compile this module and send you a copy.

---

### Post by ibrrfarr on 2011-02-15
[LEFT]OK.  I believe I will wait for the update.  Thanx for all the input!
[/LEFT]

---

### Post by williamts99 on 2011-02-15
Here is the release schedule, due for final release in Apr.

[https://wiki.ubuntu.com/NattyReleaseSchedule](https://wiki.ubuntu.com/NattyReleaseSchedule)

---

### Post by BigRedButton on 2011-02-17
There is a driver available for the ENE multi card reader present in the Aspire One series and a few others.
You need dkms and the headers for your kernel in order for the build to work.

1. Download the source code from [http://ftp.twaren.net/Linux/Linpus/Acer_Linpus_Moblin_Lite/srpms/linpus-customize/kernel/driver-src/cardreader/ENE/R100_02_ene_card_reader.zip](http://ftp.twaren.net/Linux/Linpus/Acer_Linpus_Moblin_Lite/srpms/linpus-customize/kernel/driver-src/cardreader/ENE/R100_02_ene_card_reader.zip)

2. Unzip it to /usr/src/keucr-0.0.1/. You might have to rename the folder

3. In the source folder, create dkms.conf:
```
PACKAGE_NAME="keucr"
PACKAGE_VERSION="0.0.1"
CLEAN="rm -f *.*o"
 BUILT_MODULE_NAME[0]="keucr"
MAKE[0]="make -C $kernel_source_dir M=$dkms_tree/$PACKAGE_NAME/$PACKAGE_VERSION/build"
DEST_MODULE_LOCATION[0]="/extra"
 AUTOINSTALL="yes"
```
4. Add the sources to dkms:
```
sudo dkms add -m keucr -v 0.0.1
```
5. Build the module:
```
sudo dkms build -m keucr -v 0.0.1
```
6. Build the package:
```
sudo dkms mkdeb -m keucr -v 0.0.1
```
The .deb package will be located in /var/lib/dkms/keucr/0.0.1/deb/keucr-dkms_0.0.1_all.deb
Installed and working on Aspire One d250

Thanks to vladimir on Launchpad for the driver: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277?comments=all)

---

### Post by mordalo on 2011-02-24
Well, I followed the instructions, and although I didn't have dpkg-dev installed initially, I installed it and ran through everything until I got to this point:

> **BigRedButton said:**
> 
6. Build the package:
```
sudo dkms mkdeb -m keucr -v 0.0.1
```

It was at this point, I got this:

```
sudo dkms mkdeb -m keucr -v 0.0.1
Using /etc/dkms/template-dkms-mkdeb
copying template...
modifying debian/changelog...
modifying debian/compat...
modifying debian/control...
modifying debian/copyright...
modifying debian/dirs...
modifying debian/postinst...
modifying debian/prerm...
modifying debian/README.Debian...
modifying debian/rules...
copying legacy postinstall template...
Copying source tree...
Gathering binaries...Marking modules for 2.6.35-27-generic (i686) for archiving...

Creating special tarball structure to accomodate only binaries.


Tarball location: /var/lib/dkms/keucr/0.0.1/tarball/keucr-0.0.1.dkms.tar.gz

DKMS: mktarball Completed.

Copying DKMS tarball into DKMS tree...
Building binary package...dpkg-buildpackage: warning: using a gain-root-command while being root
 dpkg-source --before-build keucr-dkms-0.0.1
 fakeroot debian/rules clean
make: dh_testdir: Command not found
make: *** [clean] Error 127
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
(bad exit status: 2)
```

I'm not a programmer, nor a coder.  I have no idea what happened.  Any ideas/suggestions/help!

---

### Post by mordalo on 2011-02-24
Well, error or not...IT WORKED!

I ran apt-get update and upgrade, rebooted, and it worked!
Finally, after nearly having this netbook for a year, I can use the SD card reader.

Thank you, Vladimir, wherever you are!

:KS

---

### Post by pracrichard on 2011-03-03
I am having the same trouble with this card reader. The good news is that I have been told there will be a fix in 11.04. See my thread - here [URL="http://ubuntuforums.org/showthread.php?t=1683842&highlight=UB6250+SD"]http://ubuntuforums.org/showthread.php?t=1683842&highlight=UB6250+SD 
[/URL]

---

### Post by eldonkr on 2011-03-12
I just bought an Acer Aspire One D225 and my reader doesn't work either. Does compiling that doohickey work as a fix? I've built from source a while ago with mixed results; but it's been long enough that I don't remember how it all works.

---

### Post by desaivarun_104lts on 2011-03-12
> **BigRedButton said:**
> There is a driver available for the ENE multi card reader present in the Aspire One series and a few others.
You need dkms and the headers for your kernel in order for the build to work.

1. Download the source code from [http://ftp.twaren.net/Linux/Linpus/Acer_Linpus_Moblin_Lite/srpms/linpus-customize/kernel/driver-src/cardreader/ENE/R100_02_ene_card_reader.zip](http://ftp.twaren.net/Linux/Linpus/Acer_Linpus_Moblin_Lite/srpms/linpus-customize/kernel/driver-src/cardreader/ENE/R100_02_ene_card_reader.zip)

2. Unzip it to /usr/src/keucr-0.0.1/. You might have to rename the folder

3. In the source folder, create dkms.conf:
```
PACKAGE_NAME="keucr"
PACKAGE_VERSION="0.0.1"
CLEAN="rm -f *.*o"
 BUILT_MODULE_NAME[0]="keucr"
MAKE[0]="make -C $kernel_source_dir M=$dkms_tree/$PACKAGE_NAME/$PACKAGE_VERSION/build"
DEST_MODULE_LOCATION[0]="/extra"
 AUTOINSTALL="yes"
```
4. Add the sources to dkms:
```
sudo dkms add -m keucr -v 0.0.1
```
5. Build the module:
```
sudo dkms build -m keucr -v 0.0.1
```
6. Build the package:
```
sudo dkms mkdeb -m keucr -v 0.0.1
```
The .deb package will be located in /var/lib/dkms/keucr/0.0.1/deb/keucr-dkms_0.0.1_all.deb
Installed and working on Aspire One d250

Thanks to vladimir on Launchpad for the driver: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277?comments=all)
can you explain me how to do the thrid step..
i cant creat a dkms.conf..
how to do that

---

### Post by eldonkr on 2011-03-13
So, after it turns into a .deb package do I run the .deb?

---

### Post by rvndrk3233 on 2011-03-17
can someone sticky page 4 with the sources plEASE?

Its hard to find working code like this that builds ok for DEBIAN as well...and google redid thier index, so this needs to be one of the FIRST links that those with keucr/AKA ENE card readers on *NIX can find ...I owe you one..

you have to dig out the deb file it makes and "dpkg -i" the file(as root or sudo root)

SAVE IT FOR LATER, the board wont let me post what I have for Debian 6(standard stock kernel).

---

### Post by eldonkr on 2011-03-17
I tried fixing my card reader tonight. I was reading through the bug report and found this comment:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277/comments/135](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277/comments/135)
I downloaded and ran the .deb attached to it and put an SD card in and it recognized it and opened up the folder. When I tried to eject the drive with the disk mounter panel applet and it would eject and reappear instantly; but it wouldn't mount it again. I mounted it again and this time I right clicked on the desktop icon for the drive an clicked 'Safely Remove' and got the following error message:
```
Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5)
SYNCHRONIZE CACHE: FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: FAILED: No such file or directory
```
What do I do now?

---

### Post by eldonkr on 2011-03-17
/poke

Anyone have any ideas?

---

### Post by bdaman80 on 2011-03-18
I just downloaded and installed the .deb file from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277/comments/135](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277/comments/135) and would like to report it works fine on my AAO D260-2916!! I get the same error message as you when i go to remove, but it still removes for me and remounts when I re-insert.  This is on 10.10 Desktop 64 bit

---

### Post by eldonkr on 2011-03-18
Yeah, everything is working now. The error message is of no consequence as far as I can tell, it's just annoying. I'd like to figure out what is causing it so that I won't get an error message every time I try to eject an SD card.

---

### Post by eldonkr on 2011-03-23
So.... anyone know what I should do about that error message?

---

### Post by eldonkr on 2011-04-06
Still hoping for an answer....

---

### Post by ibrrfarr on 2011-04-11
I installed 11.04 and all works like a charm now!

---

### Post by eldonkr on 2011-04-13
> **ibrrfarr said:**
> I installed 11.04 and all works like a charm now!

Well, I knew that the card reader would work in 11.04. But I usually like to wait a while before I upgrade to a new version just to make sure everything is working smoothly. For example, I was using Karmic until last month when I bought this netbook.

Is everything working great in 11.04? I've heard some horror stories from friends who had weird things happened when they upgraded soon after a new release.

---

### Post by ibrrfarr on 2011-04-16
Other than the normal shake down stuff I've had no problems.

---

### Post by RedOctober17 on 2011-04-30
I've just updated to 11.04 on an AAO D255, and no luck with the card reader. The little disk light comes on, blinks for a moment, and stays on, but nothing else happens.

The disk utility recognises the card, but when I try to mount, I get the following error.

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed

So...it's already mounted? I can't find it in the file system, though.

---

### Post by CoryDean on 2011-05-04
Hello board I to have an ACER ASPIRE on d250 netbook same problems sd card reader and usb not reading external mem. properly disk utilities see them but cant mount please help......:(

---

### Post by eldonkr on 2011-05-04
Sort of off topic. The website that has my AOD225 in stock says that the netbook can be upgraded to 2gb of RAM. I was wondering if that is the hardware limit for this netbook or if that is the max that Windows will recognize on this netbook and if Ubuntu doesn't have the same restriction.


What's the point of putting a 64-bit proccy in this thing if it won't recognize more than 2gb RAM?

---

### Post by frncz on 2011-05-09
I would also like to know whether one can put more than 2Gb in AAO D255. There is only one memory slot. Can one buy  memory sticks with more than 2Gb in the same form factor?

---

### Post by jlh68 on 2011-05-09
The motherboard will only support 2-GB, you can put more RAM in, but only 2-GB will be seen by the computer.  (the OS (32-bit) would recognise 3.3-GB if the M/B will allow) 

On my older Acer Aspire ONE 8.9-in only recognises 1.5-GB.  I tried to go higher, but was limited to 1.5-GB by the M/B.

A side note I still cannot get the second SD slot to work.  I only get the SD slot that was made for additional memory (Left side) to work.  The right side does not work.  It would be nice it it did.

---

### Post by eldonkr on 2011-05-09
What is the point of having an x -64 processor if the hardware limit is 2gb?

---

### Post by fINTiP on 2011-05-15
I'm also curious about the ram limitation question in relation to the dual core processor. I spent hours trying to read up on this, and the answers all over the web were just convoluted, disagreeing, and reaked of ignorance. Can someone give a clear proof that the 2gig limit is truly the motherboard, and explain the ups and downs of a 64bit distro with less than 4gigs of ram clearly?

Otherwise, I came to this thread because, of course, I also don't see the SD card on my AOD255-1625 (N550 processor). I'm running 64bit 10.04, fresh install. About to try the option mentioned on page 4.

---

### Post by eldonkr on 2011-05-16
> **fINTiP said:**
> I'm also curious about the ram limitation question in relation to the dual core processor. I spent hours trying to read up on this, and the answers all over the web were just convoluted, disagreeing, and reaked of ignorance. Can someone give a clear proof that the 2gig limit is truly the motherboard, and explain the ups and downs of a 64bit distro with less than 4gigs of ram clearly?

Otherwise, I came to this thread because, of course, I also don't see the SD card on my AOD255-1625 (N550 processor). I'm running 64bit 10.04, fresh install. About to try the option mentioned on page 4.

Dude, just install Natty. It's stable and awesome and I've heard that the SD card reader works on 11.04.

---

### Post by ssticht on 2011-05-18
Hi,

I have an AAO150 running 11.04 and both card readers
work fine, but only if I boot with a card in them.
That is a bit annoying.

Anyone an idea? Should I open another bug report or can I update
an existing?

Thanks,
Stefan

---

### Post by ssticht on 2011-05-20
Hi again,

as said earlier, both card slots on my Acer Aspire One ZG5 aka 150 with Ubuntu 11.04 are working fine with SDHC cards (have no other type)
if the card is inserted while boot. Meanwhile I found out that

sudo echo 1 > /sys/bus/pci/rescan

forces a rescan of the PCI bus what also finds the inserted card
and makes the card slot available.

From what I have read that should be the task of the pciehp module,
but that one has not been installed with my 11.04 installation.

Hope that helps,
Stefan

---

### Post by molo3 on 2011-07-11
Hi, i tried BigRedbutton's method but building the module I obtain this:
[HTML]ales@roby-netbook:~$ sudo dkms build -m keucr -v 0.0.1

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.32-32-generic -C /lib/modules/2.6.32-32-generic/build M=/var/lib/dkms/keucr/0.0.1/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.32-32-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/keucr/0.0.1/build/ for more information.
0
0
ERROR: binary package for keucr: 0.0.1 not found
[/HTML]This is the make.log file:

[HTML]DKMS make.log for keucr-0.0.1 for kernel 2.6.32-32-generic (i686)
lun 11 lug 2011, 17.05.26, CEST
make: ingresso nella directory «/usr/src/linux-headers-2.6.32-32-generic»
scripts/Makefile.build:44: /var/lib/dkms/keucr/0.0.1/build/Makefile: Nessun file o directory
make[1]: *** Nessuna regola per creare l'obiettivo «/var/lib/dkms/keucr/0.0.1/build/Makefile».  Arresto.
make: *** [_module_/var/lib/dkms/keucr/0.0.1/build] Errore 2
make: uscita dalla directory «/usr/src/linux-headers-2.6.32-32-generic»[/HTML]
What's the problem?
Thanks

---

### Post by pearsoa on 2011-12-20
Is this thread still valid, I have an acer aspire one and have used Ubuntu and mint linux on it, the right hand sd reader works after using the fix described in the 1st post here-- [http://forums.techarena.in/tips-tweaks/1349695.htm](http://forums.techarena.in/tips-tweaks/1349695.htm)

---

### Post by jlh68 on 2011-12-20
I read the fix in **pearsoa** post.  It is talking about GRUB and no mention of GRUB2. Will this fix work with 11.04 or 11.10?  Both of them use GRUB2 instead of GRUB.  I had the right SD port working with GRUB and 8.10.  It did not work with 10.4 or 11.10, I skipped using 10.10 and 11.04 on my netbook.

I now have 11.10 installed which uses GRUB2.  I will see if I can get it to work using the fix.  I would like to know if anyone has had success with the fix in 11.10.

---

### Post by xyzzyman on 2011-12-21
> **jlh68 said:**
> I read the fix in **pearsoa** post.  It is talking about GRUB and no mention of GRUB2. Will this fix work with 11.04 or 11.10?  Both of them use GRUB2 instead of GRUB.  I had the right SD port working with GRUB and 8.10.  It did not work with 10.4 or 11.10, I skipped using 10.10 and 11.04 on my netbook.

I now have 11.10 installed which uses GRUB2.  I will see if I can get it to work using the fix.  I would like to know if anyone has had success with the fix in 11.10.

You would still pass the kernel options along the same way through the /etc/default/grub file. The question is whether the drivers in question in 11.10 support those options you're adding. If they don't the system will boot no problems just no fix will take place.

---

### Post by jlh68 on 2011-12-22
I have change grub IAW the procedure in [http://forums.techarena.in/tips-tweaks/1349695.htm](http://forums.techarena.in/tips-tweaks/1349695.htm).

Still right side did not work.  The post talked about a SSD, where I have a 120 GB HDD.  I don't know if that would make a difference in the coding of the grub file.

Any more suggestions.

---

### Post by jlh68 on 2011-12-30
Well, the change to the GRUB file broke the OS.  Had to boot into the recovery mode and reverse the change.  That restored the OS so it would boot again.

So I am still looking for a way to get the right side SD card reader working.

---

### Post by petrzovy on 2012-04-13
I have AAO ZG5 +Lin Mint 11. Before I had many distros and always the  same problem. Mass store card reader never worked(only the left one). In  Synaptic I have instaled [IMG]http://ubuntuforums.org/data:image/png;base64,PGh0bWwgeG1sbnM6dG9tYm95PSJodHRwOi8vYmVhdG5pa3NvZnR3YXJlLmNvbS90b21ib3kiIHhtbG5zOmxpbms9Imh0dHA6Ly9iZWF0bmlrc29mdHdhcmUuY29tL3RvbWJveS9saW5rIiB4bWxuczpzaXplPSJodHRwOi8vYmVhdG5pa3NvZnR3YXJlLmNvbS90b21ib3kvc2l6ZSI+PGJvZHk+bGlicGNzY2xpdGUxPC9ib2R5PjwvaHRtbD4=[/IMG]libpcsclite1 and now it works fine. 

If you have not libpcsclite1 in repo, try google, or add more sources. 
Or try type to Synaptic "card reader" or anything similar. When I click on libpcsclite1 it give me dicription 

"The purpose of PC/SC Lite is to provide a Windows(R) SCard interface
in a very small form factor for communicating to smartcards and
readers.

The PC/SC Lite library is used to connect to the PC/SC daemon from
a client application and provide access to the desired reader."

(sorry for my English - it is not my mother tong ):P )

---

### Post by user-friendly on 2012-05-30
I have this problem of the RH card reader fixed. Now I can boot my Acer Aspire one with no SD cards in both left and right reader, insert a card in left or right and it is instantly mounted. Both 4GB and 8Gb SD cards work. :KS

Add these pciehp options to /etc/default/grub

```
GRUB_CMDLINE_LINUX_DEFAULT="pciehp.pciehp_force=1 pciehp.pciehp_poll=1 elevator=noop quiet splash"
```Now create a file /etc/modprobe.d/aspireone.conf with this content

```
####################################################################
# Module options for the Acer AspireOne
#
# Enable USB card reader
options pciehp pciehp_force=1
install sdhci for i in 2381 2382 2383 2384; do /usr/bin/setpci -d 197b:$i AE=47; done; /sbin/modprobe --ignore-install sdhci
```Now add the following line to the end of you existing /etc/modules file

```
pciehp
```You do need to be ROOT to edit and create these files, I use gedit. Reboot your computer and watch the magic. :popcorn:
This is using Easy Peasy which is built on Ubuntu 10.04 (Lucid) and uses Grub and not Grub2.

---

### Post by druucifer on 2012-12-15
I have an Acer NAV50 netbook running 32 bit 12.10, and I am still experiencing this problem.  Windows can recognize the card reader, but nothing in Ubuntu.  I have never been able to get it to recognize an SD card in Ubuntu.

---

### Post by gatesdrovme2it on 2013-01-25
i have an acer v3-471 and the sd card slot doesn't work with 12.10.  i guess this problem is just going to go on forever?

---

