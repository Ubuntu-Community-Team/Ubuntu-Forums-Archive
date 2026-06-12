---
title: "Micro Solutions Backpack USB External CDRW module/driver build?"
date: 2011-10-19
forum: Hardware
---

### Post by northd_tech on 2011-10-19
I have a very old external Micro Solutions CDRW drive that has 3 interfaces (USB 2.0, "PC card"/PCMCIA, and Parallel port) and these are selectable by changing the cable interface to the computer.  The manufacturer has since gone out of business, so there will be NO support forthcoming on that front.  This was probably one of the first USB 2.0 interfaces that I ever saw (I needed to special order and install a SIIG USB host adapter card in order to access the USB 2.0 speeds waaay back when under Win98SE).  Of course, my 64bit Windows Vista has no drivers since Vista came out years after the manufacturer went out of business, and Vista won't seem to recognize the external CD spinner using the Win9X/ME/NT4 drivers.  Strangely enough, the driver install program files worked fine under 64bit Vista (I was expecting the ubiquitous 64bit "different version of windows" error message that I have grown so accustomed to- which is generally when I immediately boot over to Ubuntu).  I have tried 5 or 6 of the Win9x drivers with no love so far under Vista Home 64bit.

I need to access some of my old archived data that was recorded on what now appear to be somewhat "dodgy" CD-R media that WILL NOT read in any of my newer CDRW/DVD-RW drives (and I've tried 2 external DVD-RW drives in addition to my HP laptop's internal Optiarc DVD-RW drive).  I can get these to at least partially read in a relative's Sony 52x CD-RW drive, but I only have Guest access to that machine under WinXP and I really don't want to go through the hassle of trying to transfer Gigabytes of .ISO files over the wireless network to my laptop, and all the permissions hassles, etc.  These data CD-R media are still in "like new" unscratched condition (being stored on a sealed spindle for about 10+ years)- they just won't seem to read in the newer DVD-RW drives for whatever reason(s).

I cannot use the Backpack drive's Parallel port interface as my HP laptop HAS NO Parallel Port (just 4 USB and 1 firewire port).  "PC card"/PCMCIA might work under Ubuntu, but the transfer rate is much slower than USB 2.0 and I would need to go for a long drive to find the PCMCIA adapter in my storage location...   Long story short:  I need to get this old, obsolete [as in read the manufacturer went out of biz] CDRW drive running on a USB 2.0 cable under some flavor of Linux.

My [USB 2.0] external CDRW drive is a "series 6" "Triple Play" Backpack model #195200.

I did locate some older information from around 2005 or so where apparently a Micro Solutions engineer, Ken Hahn, and  some other people were able to get the Backpack USB drives running under Arch Linux, Frugalware and possibly some other distros:

BACKPACK USB (and USB2.0) now working in Linux
[http://lwn.net/Articles/7653/](http://lwn.net/Articles/7653/)

Subject: Re: New Packages - fxload and bpck-usb-firmware - msg#00068
[http://osdir.com/ml/linux.frugalware.devel/2006-02/msg00068.html](http://osdir.com/ml/linux.frugalware.devel/2006-02/msg00068.html)

Making a Driver Package for USB CD-Writer Drives
[https://bbs.archlinux.org/viewtopic.php?id=18156](https://bbs.archlinux.org/viewtopic.php?id=18156)
-----------------------------------------------
I was able to locate some Frugalware and Knoppix Linux sourcecode files and scripts that are also pretty old:

[http://www6.frugalware.org/mirrors/linux/frugalware/frugalware-testing/source/lib-extra/bpck-usb-firmware/](http://www6.frugalware.org/mirrors/linux/frugalware/frugalware-testing/source/lib-extra/bpck-usb-firmware/)

ftp.cc.uoc.gr/mirrors/linux/frugalware/frugalware-testing/source/lib-extra/bpck-usb-firmware/

[http://knoppix.mirrors.tds.net/pub/linux/frugalware/frugalware-current/source/lib-extra/bpck-usb-firmware/](http://knoppix.mirrors.tds.net/pub/linux/frugalware/frugalware-current/source/lib-extra/bpck-usb-firmware/)

[http://ftp.freepark.org/pub/linux/distributions/frugalware/frugalware-stable/source/lib-extra/bpck-usb-firmware/](http://ftp.freepark.org/pub/linux/distributions/frugalware/frugalware-stable/source/lib-extra/bpck-usb-firmware/)
---------------------------
My research also led me to the [Hardware] Detection Ubuntu wiki, where I was reading about** /proc/sys/kernel/hotplug**,** /sbin/hotplug**,** /etc/hotplug/usb/** vs. [COLOR=Blue]**udevd**[/COLOR] and other mouldy, arcane whisperings:

[https://wiki.ubuntu.com/Hardware/Detection](https://wiki.ubuntu.com/Hardware/Detection)

HOWTO: Creative's Jukebox with Gnomad
[http://ubuntuforums.org/showthread.php?t=33040](http://ubuntuforums.org/showthread.php?t=33040)

OK- let's quote little from the Detection wiki here (I could certainly use the review- or 2 or 3 on this stuff):

> The kernel provides uevents by two means, by running the user-space program specified in /proc/sys/kernel/hotplug (usually /sbin/hotplug) and passing environment variables to describe the device and point to the information in the /sys filesystem; or over a netlink socket with packets containing the same information.

As the "hotplug" system relies on user-space forks, it is potentially racey as the handling of one event could be superseded by the handling of another, resulting in out-of-order events. For this reason the kernel supplies a sequence number for each event and any user-space system relying on this should take care to re-order events. The udevd daemon contains this logic.

udevd also listens on the netlink socket and receives uevents from there, eliminating duplicates and processing them the same was as if they came in through the "hotplug" system. As this socket is a FIFO, there is no requirement to re-order events as they will not arrive out of order.

For breezy we used a mixture of both methods because the input subsystem was not yet generating netlink events, in 2.6.15 this will have been fully converted to the new driver core and produces both kinds of events. Therefore** for dapper we intend to drop the "hotplug" interface and only listen for events on the netlink socket. This is far more reliable and less error-prone due to the guaranteed ordering and no need to eliminate duplicates**.Whew.  I gather from that that I want to avoid the old obsolete "hotplug" method and use the "far more reliable" netlink method.  Unfortunately, their old install script (oh yes- did I mention that we need to upload some Micro Solutions Backpack firmware into the external CDRW drive to get it recognized in Linux ) keeps wanting me to poke around in **/etc/hotplug** and to **mkdir /etc/hotplug/usb**, etc.

I was hoping to just do a little 'tailoring' of the install script to be Unbuntu-relevant/-functional when I noticed all this firmware business.  Now it's looking like a moderate to major overhaul of the script, and I am QUITE 'rusty' on the hardware driver front- and that was under Red Hat and Mandrake, NOT Ubuntu...

Any helpful tips would be appreciated (and links to the Backpack firmware and install script(s) should be at the Frugalware links above).

ndt

Edit:  Also, I already used Synaptic to install the "fxload" package that was previously missing.

---

### Post by northd_tech on 2011-10-19
> **northd_tech said:**
> 
I cannot use** the Backpack drive's Parallel port** interface as **my HP laptop HAS NO Parallel Port** (just 4 USB and 1 firewire port).  "PC card"/PCMCIA might work under Ubuntu, but the transfer rate is much slower than USB 2.0 and I would need to go for a long drive to find the PCMCIA adapter in my storage location...   Long story short:  I need to get this old, obsolete [as in read the manufacturer went out of biz] CDRW drive running on a USB 2.0 cable under some flavor of Linux.

My [USB 2.0] external CDRW drive is a "series 6" "Triple Play" Backpack model #195200.
Apparently, the** Parallel Port** Backpack support is a 'standard' built-in component of Linux kernels since 2.2.x:

> ** Obtaining PARIDE**

     The **PARIDE** drivers **are now included as standard components of the Linux kernel distribution.  At this writing, the    current stable kernel is Linux version 2.2.1** and is widely    available from many FTP sites on the internet.
     The most recent version of the previous stable kernel, Linux    version 2.0.36 also contained the PARIDE drivers (with a few    missing features).
     Recent distributions from [Slackware]("http://www.slackware.org/") and [SuSE]("http://www.suse.de/") contain installation support for    PARIDE CD-ROMs.  [Red Hat]("http://www.redhat.com/") does    not officially support PARIDE devices for installation purposes,    but the installed system does contain all the necessary support.
[http://cyberelk.net/tim/parport/paride.html](http://cyberelk.net/tim/parport/paride.html)

See also:

CONFIG_PARIDE_BPCK6: MicroSolutions backpack (Series 6) protocol
[http://cateee.net/lkddb/web-lkddb/PARIDE_BPCK6.html](http://cateee.net/lkddb/web-lkddb/PARIDE_BPCK6.html)

While this is interesting information, my Laptop still mainly just has the USB 2.0 interface available to the Backpack CDRW burner and NO Parallel port... :(

Also, I'm currently running Ubuntu Lucid Lynx 10.04.3 LTS with:

> Linux  2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC 2011 x86_64 GNU/Linux
With the external drive unplugged I get this from **lsusb**:

> Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a110 Suyin Corp. HP Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
but with the Backpack external CDRW "hotplugged"** lsusb** tells me:
> Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a110 Suyin Corp. HP Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR=Blue]**Bus 001 Device 002: ID 0ac9:0010 Micro Solutions, Inc. BACKPACK**[/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Thusly, I conclude that my Backpack USB cables, drive, and external power supply are all still functioning- I just need to find a way to get my Ubuntu 2.6.32-34-generic x86_64 kernel to recognize (and mount) the interface/CDRW drive so I can read my old data and convert them to .ISO's for burning on better/newer DVD disks.

---

### Post by northd_tech on 2011-10-19
> **northd_tech said:**
> 
but with the Backpack external CDRW "hotplugged"** lsusb** tells me:
> [COLOR=Blue]**Bus 001 Device 002: ID 0ac9:0010 Micro Solutions, Inc. BACKPACK**[/COLOR]

The verbose** lsusb -v** tells me this about that [obsolete] Micro Solutions Backpack CDRW external USB drive:

> Bus 001 Device 002: ID 0ac9:0010 Micro Solutions, Inc. BACKPACK
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x0ac9 Micro Solutions, Inc.
  idProduct          0x0010 BACKPACK
  bcdDevice            0.85
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          171
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      [B](Bus Powered)
    MaxPower              100mA[/B]
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
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
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
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
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  **(Bus Powered)**My SWAG here is that the** USB interface is bus-powered** (and needs some Backpack firmware injected by Ubuntu) whereas the CDRW [COLOR=Green]**drive**[/COLOR] itself uses the MicroSolutions dual 5VDC & 12VDC external power 'brick.'

---

### Post by northd_tech on 2011-10-19
> **northd_tech said:**
>   I gather from that that I want to avoid the old obsolete "hotplug" method and use the "far more reliable" netlink method.  Unfortunately, their old install script (oh yes- did I mention that we need to upload some Micro Solutions Backpack firmware into the external CDRW drive to get it recognized in Linux ) keeps wanting me to poke around in **/etc/hotplug** and to **mkdir /etc/hotplug/usb**, etc.

I was hoping to just do a little 'tailoring' of the install script to be Unbuntu-relevant/-functional when I noticed all this firmware business.  Now it's looking like a moderate to major overhaul of the script, and I am QUITE 'rusty' on the hardware driver front- and that was under Red Hat and Mandrake, NOT Ubuntu...

I just found this old 'zombie' of a thread in a web search (not in an ubuntuforums search) that looks to be worth a shot- I will post updates (or massive failures) here as I discover them- since I can't post or tag that old 2006 thread with anything relevant to my Backpack USB troubles here:

**Please help, MicroSolutions Back Pack CD-RW issue, USB style**
[http://ubuntuforums.org/showthread.php?t=218475](http://ubuntuforums.org/showthread.php?t=218475)

I'm looking at posts #7 and #8 on that thread, and I will be taking extensive notes on my inputs/outputs/results.

Edit:  More possibly helpful, likely obsolete notes:

**External USB BACKPACK CD-ReWriter problem...  **
[http://www.linuxquestions.org/questions/linux-hardware-18/external-usb-backpack-cd-rewriter-problem-212360/](http://www.linuxquestions.org/questions/linux-hardware-18/external-usb-backpack-cd-rewriter-problem-212360/)

**Linux and USB 2.0** (refers to now-defunct Micro Solutions website for .RPM files...)
[http://www.linux-usb.org/usb2.html](http://www.linux-usb.org/usb2.html)

---

### Post by northd_tech on 2011-10-20
I wasn't certain which of the Backpack firmwares was correct for my old external CDRW, so I was forced to 'trial&error' and ended up trying all 5 firmwares with no luck (but the firmware appears to load in RAM, not EEPROM, so hopefully nothing got messed up in the USB interface by my 'erroring').

The one firmware did throw an error message, so I'm reasonably certain that the "BPINTCD.HEx" firmware file is incorrect for my Backpack Series 6 External CDRW drive:
> ~/Desktop/bpck-usb-firmware-1.1/firmware$ **sudo fxload -vv -D /dev/bus/usb/001/008 -I BPINTCD.HEX**
microcontroller type: fx
single stage:  load on-chip memory
open RAM hexfile image BPINTCD.HEX
stop CPU
write on-chip, addr 0x0000 len    3 (0x0003)
write on-chip, addr 0x125e len    6 (0x0006)
write on-chip, addr 0x0043 len    3 (0x0003)
write on-chip, addr 0x1000 len    4 (0x0004)
write on-chip, addr 0x100c len   12 (0x000c)
write on-chip, addr 0x0e00 len  208 (0x00d0)
can't write 7 bytes external memory at 0x1cd0
unable to download BPINTCD.HEXI did find this very helpful tidbit of information while researching- post #1 and I"m posting the [previously missing] bpckusb script here for convenience, since it is apparently EXTREMELY difficult to locate now with Micro Solutions now being disintegrated:

```
#!/bin/sh

# [shell script "bpckusb"]
# [from post #1: http://www.linuxquestions.org/questions/linux-hardware-18/external-usb-backpack-cd-rewriter-problem-212360/#post1082927 ]
# [ **External USB BACKPACK CD-ReWriter problem... (Solved!)]**
# [ http://www.linuxquestions.org/questions/linux-hardware-18/external-usb-backpack-cd-rewriter-problem-212360/#post1082927]
# [ FYI- Micro Solutions went out of business years ago as of Oct. 18, 2011]
# Load bulk/interrupt transfer test firmware into
# various EZ-USB USB devices that will run it

#TEMPLATE PROGRAM TAKEN FROM [http://linux-hotplug.sourceforge.net/perf](http://linux-hotplug.sourceforge.net/perf) 4/2/2002
#Adapted for BACKPACK USB drives 

FIRMWARE=
FLAGS=

# pre-renumeration device IDs
case $PRODUCT in

# BACKPACK USB2 INTERNAL ADAPTER

#----------------------SCANNNERS SCANNERS-------------------------------
#external usb1 scanner
ac9/0/0)
    FIRMWARE=usb/bpckusb.fw/BP1SCAN.HEX
    ;;

#external usb2 scanner
ac9/1/*)
    FIRMWARE=usb/bpckusb.fw/BP2SCAN.HEX
    FLAGS="-2"
    ;;

#----------------------USB1 EXTERNAL-------------------------------
#external usb1 cd-romish series 5
ac9/1000/*)
    FIRMWARE=usb/bpckusb.fw/BP1CD5.HEX
    ;;
#external usb1 cd-romish series 6
ac9/1001/*)
    FIRMWARE=usb/bpckusb.fw/BP1CD6.HEX
    ;;
#external usb1 hard drive series 5
ac9/1002/*)
    FIRMWARE=usb/bpckusb.fw/BP1HD5.HEX
    ;;
#external usb1 hard drive series 6
ac9/1003/*)
    FIRMWARE=usb/bpckusb.fw/BP1HD6.HEX
    ;;

#----------------------USB2 EXTERNAL-------------------------------
#external usb2 cd-romish series 5
ac9/1004/*)
    FIRMWARE=usb/bpckusb.fw/BP2CD5.HEX
    FLAGS="-2"
    ;;
#external usb2 cd-romish series 6
ac9/1005/*)
    FIRMWARE=usb/bpckusb.fw/BP2CD6.HEX
    FLAGS="-2"
    ;;
#external usb2 hard drive series 5
ac9/1006/*)
    FIRMWARE=usb/bpckusb.fw/BP2HD5.HEX
    FLAGS="-2"
    ;;
#external usb2 hard drive series 6
ac9/1007/*)
    FIRMWARE=usb/bpckusb.fw/BP2HD6.HEX
    FLAGS="-2"
    ;;

#----------------------USB2 INTERNAL-------------------------------
#internal usb2 cd-romish drive
ac9/10/*)
    FIRMWARE=usb/bpckusb.fw/BPINTCD.HEX
    FLAGS="-2"
    ;;

#internal usb2 cd-romish drive
ac9/11/*)
    FIRMWARE=usb/bpckusb.fw/BPINTHD.HEX
    FLAGS="-2"
    ;;
esac


# quit unless we were called to download some firmware 
if [ "$FIRMWARE" = "" ]; then
    # OR:  restructure to do other things for
    # specific post-renumeration devices
    exit 0
fi

# missing firmware?
if [ ! -r $FIRMWARE ]; then
    if [ -x /usr/bin/logger ]; then
    /usr/bin/logger -t $0 "missing $FIRMWARE for $PRODUCT ??"
    fi
    exit 1
fi

if [ ! -x /sbin/fxload ]; then
    if [ -x /usr/bin/logger ]; then
        /usr/bin/logger -t $0 "cannot load firmware, missing fxload"
        fi
        exit 1
fi 

if [ -x /usr/bin/logger ]; then
    /usr/bin/logger -t $0 "load $FIRMWARE for $PRODUCT to $DEVICE"
fi

**    /sbin/fxload $FLAGS -I $FIRMWARE **
```**External USB BACKPACK CD-ReWriter problem... (Solved!)**
[http://www.linuxquestions.org/questions/linux-hardware-18/external-usb-backpack-cd-rewriter-problem-212360/#post1082927](http://www.linuxquestions.org/questions/linux-hardware-18/external-usb-backpack-cd-rewriter-problem-212360/#post1082927)

Post #1
[http://www.linuxquestions.org/questions/linux-hardware-18/external-usb-backpack-cd-rewriter-problem-212360/#post1082927](http://www.linuxquestions.org/questions/linux-hardware-18/external-usb-backpack-cd-rewriter-problem-212360/#post1082927)

---

### Post by northd_tech on 2011-10-20
> **northd_tech said:**
> 
I did find this very helpful tidbit of information while researching- post #1 and I"m posting the [previously missing] bpckusb script here for convenience, since it is apparently EXTREMELY difficult to locate now with Micro Solutions now being disintegrated:


Also, before I forget to post it (again)- I have found that a simple **lsusb** command will tell you the USB [COLOR=Blue]**Bus**[/COLOR] & [COLOR=Red]**Dev**[/COLOR]ice information much easier than all the "Device Manager" business (that seems to now be obsolete information from my experience under Ubuntu Lucid Lynx 10.04.3 LTS) from post #7 on this thread:

[http://ubuntuforums.org/showpost.php?p=2114499&postcount=7](http://ubuntuforums.org/showpost.php?p=2114499&postcount=7)

I have found that if you lose/cycle the CDRW power or disconnect the USB cable and plug it into a different (or even the same) USB port, it keeps incrementing the [COLOR=Red]**Dev**[/COLOR]ice number (on my laptop it's apparently always on [COLOR=Blue]**Bus 001**[/COLOR] for a USB 2.0 device), so my firmware 'target' is currently:

..................[                   /Bus./Dev ]
/dev/bus/usb/[COLOR=Blue]**001**[/COLOR]/[COLOR=Red]**009**[/COLOR]

for:
> [COLOR=Blue]Bus 001[/COLOR] [COLOR=Red]Device 009[/COLOR]: ID 0ac9:0010 Micro Solutions, Inc. BACKPACK
In the case of my external USB 2.0 Series 6 CDRW #195200, I believe this is the relevant part of the Linuxquestions.org script that I just posted above:

```
#----------------------[COLOR=Green]**USB1 EXTERNAL**[/COLOR]-------------------------------
#external usb1 cd-romish series 5
ac9/1000/*)
    FIRMWARE=usb/bpckusb.fw/BP1CD5.HEX
    ;;
[COLOR=Green][B]#external usb1 cd-romish series 6
ac9/1001/*)
    FIRMWARE=usb/bpckusb.fw/BP1CD6.HEX[/B][/COLOR]
    ;;
#external usb1 hard drive series 5
ac9/1002/*)
    FIRMWARE=usb/bpckusb.fw/BP1HD5.HEX
    ;;
[COLOR=Green][COLOR=Black]#external usb1 hard drive series 6
ac9/1003/*)
    FIRMWARE=usb/bpckusb.fw/BP1HD6.HEX[/COLOR][B]
    ;;[/B][/COLOR]

#----------------------**USB2 EXTERNAL**-------------------------------
#external usb2 cd-romish series 5
ac9/1004/*)
    FIRMWARE=usb/bpckusb.fw/BP2CD5.HEX
    FLAGS="-2"
    ;;
[B]#external usb2 cd-romish series 6
ac9/1005/*)
    FIRMWARE=usb/bpckusb.fw/BP2CD6.HEX
    FLAGS="-2"
    ;;[/B]
#external usb2 hard drive series 5
ac9/1006/*)
    FIRMWARE=usb/bpckusb.fw/BP2HD5.HEX
    FLAGS="-2"
    ;;
#external usb2 hard drive series 6
ac9/1007/*)
    FIRMWARE=usb/bpckusb.fw/BP2HD6.HEX
    FLAGS="-2"
    ;;

```I'm fairly certain that I tried the "BP2CD6.HEX" firmware file first off, but perhaps the script with its "FLAGS" will somehow make the CDRW spin to life.

Still digging...

---

### Post by northd_tech on 2011-10-20
Attempting wonton180's load script from post #8 on the old thread:

```
---- load_backpack.sh -----

#!/bin/bash
#
# searches for Backpack CDRW drive on USB device tree.
#
# if found, loads the firmware update to the device so Linux
# may detect and recognize the drive

grep -B 2 "Vendor=0ac9 ProdID=0001" /dev/bus/usb/devices | head -1 | awk '{ \

fieldcount = split($0, fullstr);
busstr = fullstr[2];
fieldcount = split(busstr, busnum, "=");
devnum = fullstr[8];

targetdev = "/dev/bus/usb/0" busnum[2] "/00" devnum;
execstr = "sudo fxload -t fx2 -D " targetdev " -I /etc/backpack_usb/BP2CD6.HEX"
print "Loading USB Backpack firmware to " targetdev;
system(execstr);

}'
```

[http://ubuntuforums.org/showpost.php?p=2286286&postcount=8](http://ubuntuforums.org/showpost.php?p=2286286&postcount=8)

I got this error message:

> **sh ./load_backpackUSB.sh**
grep: /dev/bus/usb/devices: No such file or directory


It looks to me like the USB Bus/Device reference scheme has probably changed since that script was written back in March 2007... :(

Currently, my Backpack USB CDRW drive is at: /dev/bus/usb/001/009 and I'm trying to decipher what it is that script is trying to do, but I can already see that mine is an "fx" device type, not a "fx2" as shown in that old script.

For reference:
> usage: fxload [-vV] [-t type] [-D devpath]
        [-I firmware_hexfile] [-s loader] [-c config_byte]
        [-L link] [-m mode]
... [-D devpath] overrides DEVNAME= and DEVICE= in env
... device types:  one of an21, fx, fx2
... at least one of -I, -L, -m is required


---

### Post by northd_tech on 2011-10-20
> **northd_tech said:**
> 
I did find this very helpful tidbit of information while researching- post #1 and I"m posting the [previously missing] bpckusb script here for convenience, since it is apparently EXTREMELY difficult to locate now with Micro Solutions now being disintegrated:
...
Post #1
[http://www.linuxquestions.org/questions/linux-hardware-18/external-usb-backpack-cd-rewriter-problem-212360/#post1082927](http://www.linuxquestions.org/questions/linux-hardware-18/external-usb-backpack-cd-rewriter-problem-212360/#post1082927)
I did actually locate that "bpckusb" script in the "bpck-usb-firmware-1.1" archive- I was looking for a ".sh" extension (either from habit or code discipline reasons, but I missed that one before).

That script did..........

absolutely nothing.

NOTHING- no errors, no newly found CD drive(s), no spinning up of the drive motor- NOTHING.

I'm reasonably certain that my cable is fine and I'm communicating on the USB bus, since **lsusb** still tells me:

> Bus 001 Device 009: ID 0ac9:0010 Micro Solutions, Inc. BACKPACK


Arrgh.  Time for a system restart and a cup of coffee.

---

### Post by northd_tech on 2011-10-20
OK- I powered everything down for a while and downed a cup o' Joe.  From a fresh restart, I believe that this is the correct and proper command for my Series [COLOR=Red]**6**[/COLOR] Backpack CDRW on a USB[COLOR=Blue]**2.0**[/COLOR] interface (firmware file BP[COLOR=Blue]**2**[/COLOR]CD[COLOR=Red]**6**[/COLOR].HEX when the Backpack is at Bus 001 Dev 003 ):

**fxload -vv -D /dev/bus/usb/001/003 -I BP2CD6.HEX**

gave me this (apparently moderately "successful?") output:

> microcontroller type: fx
single stage:  load on-chip memory
open RAM hexfile image BP2CD6.HEX
stop CPU
write on-chip, addr 0x0000 len    3 (0x0003)
write on-chip, addr 0x000b len    3 (0x0003)
write on-chip, addr 0x0040 len    5 (0x0005)
write on-chip, addr 0x0033 len    3 (0x0003)
write on-chip, addr 0x0100 len 1013 (0x03f5)
write on-chip, addr 0x04f5 len 1013 (0x03f5)
write on-chip, addr 0x08ea len  413 (0x019d)
write on-chip, addr 0x0aa6 len  152 (0x0098 )
write on-chip, addr 0x0bc0 len 1021 (0x03fd)
write on-chip, addr 0x0fbd len 1013 (0x03f5)
EOF on hexfile
write on-chip, addr 0x13b2 len   16 (0x0010)
... WROTE: 4655 bytes, 11 segments, avg 423
reset CPUStill no spinning, and no new CD devices discovered (even after ejecting/inserting the CD tray with a data CD in it).  I even tried 'hotplugging' the Backpack CDRW back into the same USB port (which incremented it to Bus 001 Dev 004) and re-upping the Firmware, this time with a type "fx" specified explicitly:

~/Desktop/bpck-usb-firmware-1.1/firmware$ **fxload -vv [COLOR=Red]-t fx[/COLOR] -D /dev/bus/usb/001/004 -I BP2CD6.HEX**

> microcontroller type: fx
single stage:  load on-chip memory
open RAM hexfile image BP2CD6.HEX
stop CPU
write on-chip, addr 0x0000 len    3 (0x0003)
write on-chip, addr 0x000b len    3 (0x0003)
write on-chip, addr 0x0040 len    5 (0x0005)
write on-chip, addr 0x0033 len    3 (0x0003)
write on-chip, addr 0x0100 len 1013 (0x03f5)
write on-chip, addr 0x04f5 len 1013 (0x03f5)
write on-chip, addr 0x08ea len  413 (0x019d)
write on-chip, addr 0x0aa6 len  152 (0x0098)
write on-chip, addr 0x0bc0 len 1021 (0x03fd)
write on-chip, addr 0x0fbd len 1013 (0x03f5)
EOF on hexfile
write on-chip, addr 0x13b2 len   16 (0x0010)
... WROTE: 4655 bytes, 11 segments, avg 423
reset CPU
**lsusb**
> Bus 001 **Device 004**: ID 0ac9:0010 Micro Solutions, Inc. BACKPACK
[B]ls /dev/bus/usb/001/
[/B]
> 001  002  004 (Bus 001 Dev 001 is the "Linux Foundation 2.0 root hub", Bus 001 **[COLOR=DarkGreen]Dev 002 is my 1TB external hard disk[/COLOR]** that I've got plugged in after the fresh restart in order to retrieve some files, and Bus 001 Dev 004 should still be our Backpack CDRW).

**lsusb**
> Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a110 Suyin Corp. HP Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device [COLOR=Red]**004**[/COLOR]: ID 0ac9:0010 [COLOR=Red]**Micro Solutions, Inc. BACKPACK**[/COLOR]
Bus 001 Device [COLOR=DarkGreen]**002**[/COLOR]: ID 18a5:0216  
Bus 001 Device **001**: ID 1d6b:0002 Linux Foundation 2.0 root **hub**
Still no luck, and still no spinning CD-R media (but the drive LED is glowing orange at me- it is green when the disk is first inserted, but I cannot remember if this indicates an error condition or not.  I seem to recall it flashing red while burning CD-R's but I've owned almost a dozen recordable drives and used many more than that, so I can't say for certain).

So to recap:
1.  120 Volts of 60 Hertz AC power to Backpack CDRW drive- check.
2.  USB cable communication to Backpack CDRW drive- check (according to lsusb).
3.  Readable data disc in Backpack CDRW drive- very likely (it automounted in my laptop's internal Optiarc DVD-RW drive and I tested the integrity of a .ZIP file on the CD with no errors noted).
4.  Firmware loaded in Backpack CDRW drive- it would appear so if the "reset CPU" message and lack of error messages from the **fxload** command(s) means anything.

NOTE:  I had absolutely NO luck with any of the old scripts that I tried (either the unmodified ones or my attempts at bringing them more along much more modern Ubuntu 10.04.3 LTS 'lines').

ANY input from our Hardware and/or PERL scripting gurus here would be helpful- I'm ready to try the old "factory" Micro Solutions Win98 drivers under a VirtualBox "Windows 98SE" virtual machine to try to generate my .ISO files from my old data CD's now.   That will probably be a goose chase as well.

I did figure out that wonton180's script would probably work better (**on my** HP laptop running Ubuntu 10.04.3 LTS, that is) with this input string though:

**lsusb | grep BACKPACK**
> Bus 001 Device 004: ID 0ac9:0010 Micro Solutions, Inc. BACKPACK


---

### Post by northd_tech on 2011-10-20
Perhaps my one last try (today at least)- I forgot to try **sudo** above.  After unplugging the external Backpack CDRW AC power supply for at least a dozen seconds to clear the RAM (which incremented the Device to Bus 001 Dev 005 according to **lsusb**):

~/Desktop/bpck-usb-firmware-1.1/firmware$ **sudo fxload -vv -t fx -D /dev/bus/usb/001/005 -I BP2CD6.HEX**

> microcontroller type: fx
single stage:  load on-chip memory
open RAM hexfile image BP2CD6.HEX
stop CPU
write on-chip, addr 0x0000 len    3 (0x0003)
write on-chip, addr 0x000b len    3 (0x0003)
write on-chip, addr 0x0040 len    5 (0x0005)
write on-chip, addr 0x0033 len    3 (0x0003)
write on-chip, addr 0x0100 len 1013 (0x03f5)
write on-chip, addr 0x04f5 len 1013 (0x03f5)
write on-chip, addr 0x08ea len  413 (0x019d)
write on-chip, addr 0x0aa6 len  152 (0x0098 )
write on-chip, addr 0x0bc0 len 1021 (0x03fd)
write on-chip, addr 0x0fbd len 1013 (0x03f5)
EOF on hexfile
write on-chip, addr 0x13b2 len   16 (0x0010)
... WROTE: 4655 bytes, 11 segments, avg 423
reset CPU
In the words/shrieks of Steven Tyler:  "Same ol' story, Same ol' song&dance, My friend." :(

Edit:  Also the only device seen under Settings > Devices in k3b is my internal DVD-RW drive, so the Backpack is still 'invisible' to anything but **lsusb**...

Edit2:  Nero Linux 4 did throw the following error message at me (and I was able to make it go away by changing the permissions for those 2 items using **gksu nautilus**):

> Please check that you have the correct permissions on the corresponding device files.
Nero Linux cannot get acces to the following devices:
/dev/sg0 (SCSI Generic Device)
/dev/sg2 (SCSI Generic Device)Although the Backpack external USB CDRW should show up as a SCSI device after uploading the firmware according to my research, I only see my internal Optiarc DVD-RW and the Image Recorder in Nero- no Backpack anything at all (and I seem to recall it showing up as the actual physical drive inside the external case not as "Backpack" when everything ran properly under Win98SE waaaay back when).

also, these are my recent USB messages:

> **dmesg | grep usb**
[    0.370000] usbcore: registered new interface driver usbfs
[    0.370000] usbcore: registered new interface driver hub
[    0.370000] usbcore: registered new device driver usb
[    0.620181] usb usb1: configuration #1 chosen from 1 choice
[    0.640174] usb usb2: configuration #1 chosen from 1 choice
[    0.702109] usb usb3: configuration #1 chosen from 1 choice
[    0.762106] usb usb4: configuration #1 chosen from 1 choice
[    1.083361] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    1.241998] usb 2-2: configuration #1 chosen from 1 choice
[    7.540035] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    7.713784] usb 1-2: configuration #1 chosen from 1 choice
[   13.890037] usb 1-1: new high speed USB device using ehci_hcd and address 3
[   14.040912] usb 1-1: configuration #1 chosen from 1 choice
[   50.623742] input: HP Webcam as /devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input7
[   50.623808] usbcore: registered new interface driver uvcvideo
[   50.950205] usbcore: registered new interface driver usb-storage
[   50.950604] usb-storage: device found at 2
[   50.950607] usb-storage: waiting for device to settle before scanning
[   55.954398] usb-storage: device scan complete
[  726.334047] usb 1-1: USB disconnect, address 3
[  730.602550] usb 1-1: new high speed USB device using ehci_hcd and address 4
[  730.754225] usb 1-1: configuration #1 chosen from 1 choice
[ 5497.262111] usb 1-1: USB disconnect, address 4
[ 5499.930058] usb 1-1: new high speed USB device using ehci_hcd and [COLOR=DarkRed]**address 5**[/COLOR]
[ 5500.071227] usb 1-1: configuration #1 chosen from 1 choice
I believe the "usb-storage" lines are due to me plugging in my external 1TB hard disk this time to retrieve some files....

And the Backpack drive is still dangling out there on the USB bus as:
> **lsusb**
Bus 001 [COLOR=DarkRed]**Device 005**[/COLOR]: ID 0ac9:0010 Micro Solutions, Inc. BACKPACK


Edit3: here are the SCSI messages:
> **dmesg | grep scsi**
[    1.079767] scsi0 : ahci
[    1.081548] scsi1 : ahci
[    1.083838] scsi2 : ahci
[    1.084057] scsi3 : ahci
[    1.621621] scsi4 : pata_amd
[    1.621693] scsi5 : pata_amd
[    1.658921] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-6 01.0 PQ: 0 ANSI: 5
[    1.672877] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.883574] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7561A  GH09 PQ: 0 ANSI: 5
[    1.913271] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.953209] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.953335] sr 4:0:0:0: Attached scsi generic sg1 type 5
[   50.943158] scsi6 : SCSI emulation for USB Mass Storage devices
[   55.964797] scsi 6:0:0:0: Direct-Access     SAMSUNG  HD103SI               PQ: 0 ANSI: 2
[   55.965280] sd 6:0:0:0: Attached scsi generic sg2 type 0

I believe that the Samsung HD103SI at scsi6 is my Laptop's internal hard disk, the Western Digital WD2500BEVS-6 at scsi0 is my external 1TB hard disk, and the Optiarc DVD RW AD-7561A at scsi4 is my Laptop's internal DVD-RW drive (but I might have the hard disks reversed here).

???

---

### Post by northd_tech on 2011-10-25
I'm still hacking away at this Backpack USB thing.  While cleaning off my external hard disk, I ran across the older Backpack [COLOR=Green]**parallel port**[/COLOR] DOS driver directory.  While it is [COLOR=Green]**for parallel port and NOT USB**[/COLOR], there might be something informative in the documentation regarding the Backpack firmware loading, so I will quote some of that documentation here for the historical record (and since Micro Solutions is out of business and information will be VERY hard to find for their products now).

> ------------LOADCD.BAT
:
: This batch file can be used to load the BACKPACK drivers after a
: system has booted up. The DEVICE.COM program on this disk is
: used to load the BACKPACK device driver.
:
device=bpcddrv.sys
if exist bpcddrv$ mscdex /d:bpcddrv$
> ------------IOSFIX.TXT

   USING the IOS.VXD replacement driver in Win95B (OSR2) and Win98
     
After loading Backpack Diskette Drive (or 16-bit Backpack Hard Drive)
software under Windows 95 or 98 all files after BACKPACK.SYS are
"Missing or Corrupt" during reboot.

    Error While Initializing IOS: Windows Protection Fault
                                 

The above "Missing or Corrupt" errors may occur with early versions of
Backpack Diskette Drive's 16-bit device driver (BACKPACK.SYS) or
Backpack Hard Drive's 16-bit driver (BPHDDRV.SYS) in the CONFIG.SYS
of certain computers running the second release of Windows 95
(Win95B - OSR2 - Ver 4.00.1111 or Ver 4.00.1212) or either version
of Windows 98.  Only certain computers' BIOS revisions seem to exhibit
this failure.

This problem can be temporarily worked-around by turning off the
Backpack power and rebooting the computer.  After the computer has
successfully rebooted, the Backpack Drive will not be available.

Next, update the Backpack Diskette Drive software to the 16-bit driver
version contained within the file BPFDv213.EXE on the Micro
Solutions Web site.  The updated BACKPACK.SYS file should be extracted
into the root directory, or whichever directory the BACKPACK.SYS device
driver is being loaded from.

Or, for Backpack Hard Drive, upgrade to the 32-bit driver which replaces
the original 16-bit Backpack Hard Drive driver.  Important Note:  32-bit
support is available for all Backpack Hard Drives with capacities of 850MB
or greater.  Most Backpack Hard Drives with capacities lower than 850MB
are not supported by the 32-bit driver.  16-bit driver software must be
used instead.

* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * 

You will also need to update the IOS.VXD file located in

\Windows\System\VMM32 if the message:
  
  "Error While Initializing IOS: Windows Protection Fault" 

or a similar message is displayed during reboot.  
  
       
 FOLLOW THESE INSTALLATION INSTRUCTIONS CAREFULLY TO UPDATE IOS.VXD
                                                                   
  1) Copy this patch file:  IOSFIX.EXE into the folder:
     C:\Windows\System\VMM32 
  2) From an MS-DOS prompt, change to the \Windows\System\VMM32 folder
     (by typing:  CD\WINDOWS\SYSTEM\VMM32 <enter>)
  3) Run the program: IOSFIX <enter> to update IOS.VXD 

Then, turn the Backpack back on and restart the computer.  The Backpack
should then be available and the computer should work properly.> -------------README.TXT

  BACKPACK CD-ROM Registration:

 Please be sure to send in your registration card, or register your 
 prdocut online at our Web site:  [www.micro-solutions.com]("http://www.micro-solutions.com")  to ensure 
 your eligibility for software updates, enhancements, and important
 product information.

  BACKPACK CD-ROM COMPATIBILITY

 This 16-bit DOS driver software package provides support for reading
 CD-ROM discs under MS-DOS or Windows 3.1x.  It does not provide any
 "writing" support or PD Cartridge support.

 This software is compatible with the following Backpack CD-ROM
 drive models:
 
 163550  Backpack 2x CD-ROM
 163700  Backpack 2x CD-ROM w/Sound
 164550  Backpack 4x CD-ROM
 164700  Backpack 4x CD-ROM w/Sound
 165550  Backpack 6x CD-ROM
 165700  Backpack 6x CD-ROM w/Sound
 166550  Backpack 8x CD-ROM
 166700  Backpack 8x CD-ROM w/Sound
 167550  Backpack 32x CD-ROM
 167700  Backpack 32x CD-ROM w/Sound
 
 180100  Backpack bantam
 180200  Backpack bantam w/Sound
 181100  Backpack bantam 24x
 181200  Backpack bantam 24x w/Sound
 181150  Backpack bantam 24x (No PC Card support in DOS)

 190100  Backpack cd-rewriter 2x2x6
 190120  Backpack cd-rewriter 4x2x6 (both controllers supported)
 190126  Backpack cd-rewriter 4x2x6
 190127  Backpack cd-rewriter 4x2x8
 190130  Backpack cd-rewriter 4x4x20
 191100  Backpack cd-rewriter 4x4x20 (No PC Card support in DOS)

 170550  Backpack pd/cd (PD Cartridge in DOS requires BPPDDRV.SYS)
 170700  Backpack pd/cd w/Sound (PD Cartridge/DOS requires BPPDDRV.SYS)


  USING THE LOADCD.BAT UTILITY FOR BACKPACK CD-ROM

 The Backpack CD-ROM's 16-bit device driver (BPCDDRV.SYS) can be
 temporarily loaded from a diskette (A: or B: prompt) by running
 LOADCD.BAT.  This provides a way to temporarily use the Backpack
 CD-ROM on a computer without running the complete SETUP program.
 Therefore, no modifications are made to CONFIG.SYS, AUTOEXEC.BAT,
 and no additional files/directories are added to the computer's
 C: drive.  LOADCD.BAT can be run from a diskette, a C: prompt, or
 from a network drive, provided that the required files are in
 the SAME DIRECTORY as the LOADCD.BAT utility.

 Running LOADCD.BAT is simple.  From the Backpack Master Diskette (Disk1)
 type:     A:> LOADCD  <enter>

 Files Required to run LOADCD.BAT:
 BPCDDRV.SYS:    Backpack CD-ROM's 16-bit device driver
 MSCDEX.EXE      Microsoft CD-Extension, which provides the drive
                 letter for CD-ROM drives
 DEVICE.COM      A Micro Solutions utility program which can load
                 Backpack 16-bit drivers
 LOADCD.BAT      The utility that incorporates the three files above

 Important Notes:
 If another 16-bit CD-ROM is already installed, which used MSCDEX.EXE
 already, then the LOADCD program cannot properly load, since MSCDEX.EXE
 can be run only once.
 
 If you already have a hard disk compression program, such as Microsoft's
 DoubleSpace, DriveSpace, or Stac Electronic's Stacker program loaded,
 Micro Solutions' DEVICE.COM program will not be able to load other
 Backpacks, such as Backpack Hard Drive, Backpack Diskette Drive, or
 Backpack PD (pd/cd) Drive.
 
 LOADCD.BAT must be run under DOS, and not from an "MS-DOS Prompt" under
 Windows 3.x or Windows 95/98/NT.  If you do run LOADCD.BAT from
 Windows 3.1's "MS-DOS Prompt" the Backpack CD-ROM support will be lost
 as soon as you use the EXIT command to re-enter Windows 3.1.   This
 happens because Windows 3.1 only adds CD-ROM drive support when the
 Windows 3.1 shell first loads. Windows 3.1 does not have the capability
 of adding a 16-bit CD-ROM drive after Windows has already been started.

 Using Backpack CD-ROM Parameters within LOADCD.BAT
 The normal contents of the LOADCD.BAT file is as follows:
    device=bpcddrv.sys
    if exist bpcddrv$ mscdex /d:bpcddrv$

 Use a text editor, such as DOS EDIT or Windows NOTEPAD you can modify
 LOADCD.BAT and add Backpack options such as NOEPP, UNIDIR, T1=
 or T8= (timings) or MODE=0 as follows:
        device=bpcddrv.sys  NOEPP UNIDIR T1=15
    if exist bpcddrv$ mscdex /d:bpcddrv$

 (or)   device=bpcddrv.sys  MODE=0
    if exist bpcddrv$ mscdex /d:bpcddrv$


  BACKPACK CD-ROM User's Guide (CDGUIDE):

 If you are unfamiliar with the operation of a CD-ROM drive or
 experience difficulties using the Backpack CD-ROM drive, 
 please read the Backpack CD-ROM User's Guide (CDGUIDE).

 Included with the Backpack CD-ROM drive is a diskette labeled 
 "CDGUIDE".  This diskette contains two files, CDGUIDE.DOC and 
 CDGUIDE.TXT.  Both files contain complete Backpack usage 
 instructions, troubleshooting suggestions, and technical 
 support information.
 
 CDGUIDE.DOC is written as a Microsoft Word document. To 
 view/print CDGUIDE.DOC in Microsoft Word insert the CDGUIDE
 diskette, open Word, and choose File - Open - A: (or B: ) - 
 choose the language that you prefer, and double-click on the
 CDGUIDE.DOC file.   
 
 Using Microsoft Word to view and print CDGUIDE.DOC is the 
 preferred method of accessing the Backpack user's guide.  
 If you do not have Microsoft Word you can download a free copy 
 of Microsoft Word Viewer from Microsoft's site on the World 
 Wide Web. Word Viewer allows documents created with Microsoft 
 Word to be viewed and printed.  You can find Microsoft Word 
 Viewer at:      [http://www.microsoft.com](http://www.microsoft.com) 
 
 CDGUIDE.TXT is written in regular text format and can be viewed 
 and printed from most word processing programs, Windows Write, 
 Windows Notepad, or DOS Edit. 

Contacting Micro Solutions:

 Most questions about Backpack and its operation are answered 
 in the user's guide. To solve most problems:  

 * Check the solutions and procedures in the User's Guide.

 * Review the Online Help file located in the Backpack program 
   group.

 * Visit Micro Solutions on-line at our WebSite at:

        [http://www.micro-solutions.com](http://www.micro-solutions.com).

 * Contact Micro Solutions' Automated Fax Response at 
   815.754.4600. Automated Fax Response is available 24-hours 
   daily. A complete catalog of faxes and information is 
   available. If you are calling from outside the United 
   States prefix the digits 011 when you are asked to enter
   your country code and FAX number. 

 If your problem remains unsolved, contact Micro Solutions' 
 Technical Support Department at 815.754.4500. Technical 
 Support is available during normal business hours, Monday 
 through Friday, Central Time. Before calling, be sure to have 
 the following information ready:

 * The version numbers of your backpack software and your 
   operating system (DOS, Windows 3.x, Windows 95/98 or NT).

 * The name and model of the computer, and the eight-digit 
   serial number found on the bottom of your backpack drive.

 * The exact wording of any error message(s) from the Backpack 
   driver, DOS, Windows or any other application producing 
   the error message.

 * The exact model of printer installed and the revision of 
   printer driver software, if available.

 If possible, be at your computer when calling.

 Micro Solutions Technical Support
 132 W. Lincoln Hwy.
 DeKalb, IL 60115 USA
 815.754.4600 Automated Fax Response
 815.756.4986 FAX
 815.754.4500
 [www.micro-solutions.com]("http://www.micro-solutions.com")

---

### Post by northd_tech on 2011-10-25
I also located some of the old scripts from the old Win95C OEM and Win98SE Backpack driver software.

> 
-----------txtsetup.oem
#  Version 4
#  For distribution with SETUP
#  Micro Solutions,Inc.
#  For use with series 5 & 6 driver bp32drv4.sys. Must be edited to use with
#  other drivers.

[Disks]

# This section lists all disks in the disk set.
#
# <description> is a descriptive name for a disk, used when
#   prompting for the disk
# <tagfile> is a file whose presence allows setup to recognize
#   that the disk is inserted.
# <directory> is where the files are located on the disk.


d1 = "BACKPACK Driver", \DISK1.ID, \


[Defaults]

# This section lists the default selection for each 'required'
# hardware component.  If a line is not present for a component,
# the default defaults to the first item in the [<component_name>]
# section (see below).
#
# <component_name> is one of computer, display, keyboard, mouse, scsi
# <id> is a unique <within the component> string to be associated
#   with an option.

scsi = BP32DRV1


[scsi]

# This section lists the options available for a particular component.
#
# <id> is the unique string for the option
# <description> is a text string, presented to the user in a menu
# <key_name> gives the name of the key to be created for the component in
#   HKEY_LOCAL_MACHINE\ControlSet001\Services

BP32DRV1 = "BACKPACK Series 5 & 6 Driver"

[Files.scsi.BP32DRV1]

# This section lists the files that should be copied if the user
# selects a particular component option.
#
# <file_type> is one of driver, port, class, dll, hal, inf, or detect.
#   See below.
# <source_disk> identifies where the file is to be copied from, and must
#   match en entry in the [Disks] section.
# <filename> is the name of the file. This will be appended to the
#   directory specified for the disk in the [Disks] section to form the
#   full path of the file on the disk.

driver = d1, BP32DRV4.SYS,BP32DRV
inf    = d1, oemsetup.inf

#         *****  PLEASE NOTE THIS  ******
# The control panel program BPMPDCP.CPL needs to be copied into
# Win../system32 directory


[Config.BP32DRV]

# This section specifies values to be set in the registry for
# particular component options.  Required values in the services\xxx
# key are created automatically -- use this section to specify additional
# keys to be created in services\xxx and values in services\xxx and
# services\xxx\yyy.
#
# <key_name> is relative to the services node for this device.
#   If it is empty, then it refers to the services node.
#   If specified, the key is created first.
# <value_name> specifies the value to be set within the key
# <value_type> is a string like REG_DWORD.  See below.
# <value> specifies the actual value; its format depends on <value_type>

value = Parameters,default,REG_DWORD,0

#         *****  PLEASE NOTE THIS  ******
#   An additional sub key has to be added by using regedit32
#   Txtsetup can't create this sub key.
#   For NT installation this is NOT needed, but is used if the
#   parameters are to be changed in control panel later.

#   BP32DRV
#    Parameters
#     Device0                         (Sub key under Parameters)
#     DriverParameter REG_SZ "OS=1"   (value in Device0)
#  value = Device0,DriverParameter,REG_SZ,"OS=1;noepp=1;unidir=1"
> -------oemsetup.inf
[version]
signature="$Windows NT$"
Class=SCSIAdapter
ClassGUID={4D36E97B-E325-11CE-BFC1-08002BE10318}
Provider=%MSI%

[DestinationDirs]
DefaultDestDir = 12 ; DIRID_DRIVERS

[Manufacturer]
%MSI%=BP32DRV4

[BP32DRV4]
%Backpack.DeviceDesc%  = BP_Inst,BPCD

[BP_Inst]
CopyFiles = @bp32drv4.sys


[BP_Inst.Services]
AddService = BP32DRV4, 0x00000002, BP_Service_Inst, Miniport_EventLog_Inst

[BP_Service_Inst]
ServiceType    = 1
StartType      = 0
ErrorControl   = 1
Tag            = 0x00111100
ServiceBinary  = %12%\bp32drv4.sys
LoadOrderGroup = SCSI Miniport


[Miniport_EventLog_Inst]
AddReg = Miniport_EventLog_AddReg

[Miniport_EventLog_AddReg]
HKR,,EventMessageFile,0x00020000,"%%SystemRoot%%\System32\IoLogMsg.dll"
HKR,,TypesSupported,0x00010001,7

[Strings]
MSI = "Micro Solutions"
Backpack.DeviceDesc  = "BACKPACK Series 5 & 6 Driver for NT4"> --------------bpusbdrv.inf
[Version]
Signature=$CHICAGO$
Class=BACKPACK
ClassGuid={B85B7C50-6A01-11d2-B841-00C04FAD5171}
Provider=%String0%
LayoutFile=LAYOUT.INF

[ClassInstall32]
Addreg=BackpackClassReg

[BackpackClassReg]
HKR,,,,"BACKPACK"
HKR,,Icon,,0
HKR,,SilentInstall,,1

[ControlFlags]
ExcludeFromSelect = *

[Manufacturer]
%String1%=MSI_USB

[MSI_USB]
%String2%=usbcable_install, USB\VID_0AC9&PID_0000
%String3%=usbcable_install, USB\VID_0AC9&PID_0001
%String4%=usbcable_install, USB\VID_0AC9&PID_0010
%String4%=usb_install, USB\VID_0AC9&PID_1234

[DefaultInstall]
CopyFiles=usbcable.copy, usb_inf_copy

[DefaultInstall.NT]
CopyFiles = usbcable.copy

[DefaultInstall.NT.Services]
Addservice = bpusbdrv, 0x00000002, bpusbdrv.AddService
AddService = bpusbflt,, bpusbflt_Service_Inst
Addservice = usbstor, 0x00000002, usbstor.addservice

; ------ WIN98
[usbcable_install]
AddReg=usbcable.addreg

[usb_install]

; ------ WIN2000
[usbcable_install.NT]

[usbcable_install.NT.Services]
Addservice = bpusbdrv, 0x00000002, bpusbdrv.AddService

[bpusbdrv.AddService]
DisplayName    = %String2%
ServiceType    = 1                  ; SERVICE_KERNEL_DRIVER
StartType      = 3                  ; SERVICE_DEMAND_START
ErrorControl   = 1                  ; SERVICE_ERROR_NORMAL
ServiceBinary  = %12%\bpusbdrv.sys


[usb_install.NT]
AddReg=usbstor.addreg
CopyFiles=usbstor_copy


[usbstor_copy]
usbstor.sys

[usb_install.NT.HW]
AddReg=bpusbflt.addreg

[bpusbflt.addreg]
HKR,,LowerFilters,0x00010000,bpusbflt

[usbstor.addreg]
HKR,,DriverFlags,0x00010001,0x00000001


[usb_install.NT.Services]
AddService = bpusbflt,, bpusbflt_Service_Inst
Addservice = usbstor, 0x00000002, usbstor.addservice

[usbstor.addservice]
DisplayName    = %USBSTOR_desc%
ServiceType    = 1
StartType      = 3
ErrorControl   = 1
ServiceBinary  = %12%\USBSTOR.SYS

[bpusbflt_Service_Inst]
DisplayName    = %bpusbflt_2000%
ServiceType    = 1               ; SERVICE_KERNEL_DRIVER
StartType      = 3               ; SERVICE_DEMAND_START
ErrorControl   = 0               ; SERVICE_ERROR_IGNORE
ServiceBinary  = %12%\bpusbflt.sys
LoadOrderGroup = PNP Filter

; ------
[usbcable.copy]
bpusbdrv.sys
bpusbflt.sys

[usb_inf_copy]
bpusbdrv.inf

[usbcable.addreg]
HKR,,DevLoader,,*ntkern
HKR,,NTMPDriver,,bpusbdrv.sys

[SourceDisksNames]
1="BACKPACK Installation Disk",,

[DestinationDirs]
usbcable.copy = 10, System32\Drivers
usb_inf_copy = 17
usbstor_copy = 10, System32\Drivers

[SourceDisksFiles]
bpusbdrv.sys = 1
bpusbdrv.inf = 1
bpusbflt.sys = 1

[Strings]
String0="Micro Solutions, Inc."
String1="Micro Solutions, Inc."
String2="BACKPACK USB 1 Cable"
String3="BACKPACK USB 2 Cable"
String4="BACKPACK USB"
bpusbflt_2000 = "BACKPACK USB Filter"
USBSTOR_desc = "USB Mass Storage Driver"The Backpack "finder" is the driver/software that scans the Backpack interface(s) and determines which driver(s) to load, from what I recall years ago.  Here is the install script for that Backpack "finder" under Win9X/NT:

> ----------------bpfinder.inf
;
; Micro Solutions BACKPACK
;
[Version]
Signature=$CHICAGO$
Class=BACKPACK
ClassGuid={B85B7C50-6A01-11d2-B841-00C04FAD5171}
Provider=%MSI%
DriverVer=02/08/2001,3.05.0000

[ControlFlags]
ExcludeFromSelect=BACKPACK\PORT,BPDRIVE

[Manufacturer]
%MSI%=BACKPACK

[BACKPACK]
%BP_Finder%=BPFinder,root\BACKPACK
%BP_Driver_95%=BPDriver,BACKPACK\PORT
%BP_Driver_2000%=BPDriver,BPDRIVE


[DefaultInstall]
CopyFiles=finder_copy, dev_copy, inf_copy
AddReg=BPClass_reg, BP_class_95, BP_enum_95
UpdateInis=VBPD_ini

[DefaultInstall.NT]
CopyFiles = finder_copy_nt, dev_copy_nt, cpl_copy_nt, 8000t_inf_copy
Addreg = BP_class, BP_enum

[DefaultInstall.NT.Services]
AddService = bpfinder,%SPSVCINST_ASSOCSERVICE%, bpfinder_Service_Inst
AddService = bpflt,, bpflt_Service_Inst
AddService = bppnpdrv,%SPSVCINST_ASSOCSERVICE%, bppnpdrv_Service_Inst

[BP_enum]
HKLM,"SYSTEM\CurrentControlSet\Enum\Root\BACKPACK\0000","Capabilities",0x00010001,0
HKLM,"SYSTEM\CurrentControlSet\Enum\Root\BACKPACK\0000","Class",0x00000000,"BACKPACK"
HKLM,"SYSTEM\CurrentControlSet\Enum\Root\BACKPACK\0000","ClassGUID",0x00000000,"{B85B7C50-6A01-11d2-B841-00C04FAD5171}"
HKLM,"SYSTEM\CurrentControlSet\Enum\Root\BACKPACK\0000","ConfigFlags",0x00010001,4
HKLM,"SYSTEM\CurrentControlSet\Enum\Root\BACKPACK\0000","DeviceDesc",0x00000000,%BP_Finder%
HKLM,"SYSTEM\CurrentControlSet\Enum\Root\BACKPACK\0000","Driver",0x00000000,"{B85B7C50-6A01-11d2-B841-00C04FAD5171}\bpfinder"
HKLM,"SYSTEM\CurrentControlSet\Enum\Root\BACKPACK\0000","HardwareID",0x00010008,"root\backpack"
HKLM,"SYSTEM\CurrentControlSet\Enum\Root\BACKPACK\0000","Mfg",0x00000000,"Micro Solutions, Inc."
HKLM,"SYSTEM\CurrentControlSet\Enum\Root\BACKPACK\0000","Service",0x00000000,"bpfinder"

[BP_class]
HKLM,"SYSTEM\CurrentControlSet\Control\Class\{B85B7C50-6A01-11d2-B841-00C04FAD5171}","",0x00000000,"BACKPACK"
HKLM,"SYSTEM\CurrentControlSet\Control\Class\{B85B7C50-6A01-11d2-B841-00C04FAD5171}","Class",0x00000000,"BACKPACK"
HKLM,"SYSTEM\CurrentControlSet\Control\Class\{B85B7C50-6A01-11d2-B841-00C04FAD5171}","Icon",0x00000000,"0"
HKLM,"SYSTEM\CurrentControlSet\Control\Class\{B85B7C50-6A01-11d2-B841-00C04FAD5171}","SilentInstall",0x00000000,"1"
HKLM,"SYSTEM\CurrentControlSet\Control\Class\{B85B7C50-6A01-11d2-B841-00C04FAD5171}","EnumPropPages32",0x00000000,"bpcpl.cpl,PropPages"
;
HKLM,"SYSTEM\CurrentControlSet\Control\Class\{B85B7C50-6A01-11d2-B841-00C04FAD5171}\bpfinder","DriverDesc",0x00000000,%BP_Finder%
HKLM,"SYSTEM\CurrentControlSet\Control\Class\{B85B7C50-6A01-11d2-B841-00C04FAD5171}\bpfinder","DriverVersion",0x00000000,"1.0"
HKLM,"SYSTEM\CurrentControlSet\Control\Class\{B85B7C50-6A01-11d2-B841-00C04FAD5171}\bpfinder","DriverDate",0x00000000,"02/08/2001"
HKLM,"SYSTEM\CurrentControlSet\Control\Class\{B85B7C50-6A01-11d2-B841-00C04FAD5171}\bpfinder","MatchingDeviceID",0x00000000,"root\BACKPACK"
HKLM,"SYSTEM\CurrentControlSet\Control\Class\{B85B7C50-6A01-11d2-B841-00C04FAD5171}\bpfinder","ProviderName",0x00000000,%MSI%

[BP_class_95]
HKLM,"SYSTEM\CurrentControlSet\Services\Class\{B85B7C50-6A01-11d2-B841-00C04FAD5171}","Class",0x00000000,%ClassName%
HKLM,"SYSTEM\CurrentControlSet\Services\Class\{B85B7C50-6A01-11d2-B841-00C04FAD5171}","Link",0x00000000,%ClassName%
;
HKLM,"SYSTEM\CurrentControlSet\Services\Class\BACKPACK\bpfinder","DriverDesc",0x00000000,%BP_Finder%
HKLM,"SYSTEM\CurrentControlSet\Services\Class\BACKPACK\bpfinder","DriverDate",0x00000000,"02/08/2001"
HKLM,"SYSTEM\CurrentControlSet\Services\Class\BACKPACK\bpfinder","DevLoader",0x00000000,"bpfinder.vxd"
HKLM,"SYSTEM\CurrentControlSet\Services\Class\BACKPACK\bpfinder","EnumPropPages",0x00000000,"bpfinder.dll,EnumPropPages"
HKLM,"SYSTEM\CurrentControlSet\Services\Class\BACKPACK\bpfinder","MatchingDeviceId",0x00000000,"root\BACKPACK"
HKLM,"SYSTEM\CurrentControlSet\Services\Class\BACKPACK\bpfinder","ProviderName",0x00000000,%MSI%

[BP_enum_95]
HKLM,"Enum\Root\BACKPACK\0000","Capabilities",0x00000001,0x14,0,0,0
HKLM,"Enum\Root\BACKPACK\0000","Class",0x00000000,"BACKPACK"
HKLM,"Enum\Root\BACKPACK\0000","ClassGUID",0x00000000,"{B85B7C50-6A01-11d2-B841-00C04FAD5171}"
HKLM,"Enum\Root\BACKPACK\0000","ConfigFlags",0x00000001,0,0,0,0
HKLM,"Enum\Root\BACKPACK\0000","DeviceDesc",0x00000000,%BP_Finder%
HKLM,"Enum\Root\BACKPACK\0000","Driver",0x00000000,"BACKPACK\bpfinder"
HKLM,"Enum\Root\BACKPACK\0000","HardwareID",0x00010008,"root\backpack"
HKLM,"Enum\Root\BACKPACK\0000","Mfg",0x00000000,"Micro Solutions, Inc."


; ================= Class section =====================

[ClassInstall32]
Addreg=BackpackClassReg
CopyFiles=cpl_copy_nt

[BackpackClassReg]
HKR,,,,%ClassName%
HKR,,Icon,,0
HKR,,SilentInstall,,1
HKR,,EnumPropPages32,,"bpcpl.cpl,PropPages"

[cpl_copy_nt]
bpcpl.cpl

;
; ================= WIN 95/98 =================
;
[BPFinder]
CopyFiles=finder_copy,dev_copy
AddReg=finder_reg,BPClass_reg
UpdateInis=VBPD_ini
Restart

[BPDriver]
AddReg=dev_reg

[finder_copy]
bpfinder.vxd
bpfinder.dll
bpcpl.cpl
vbpd.vxd

[finder_reg]
HKR,,DevLoader,0,bpfinder.vxd
HKR,,EnumPropPages,0,"bpfinder.dll,EnumPropPages"

[BPClass_reg]
HKLM,"System\CurrentControlSet\Services\Class\BACKPACK",,,%ClassName%
HKLM,"System\CurrentControlSet\Services\Class\BACKPACK",SilentInstall,,1
HKLM,"System\CurrentControlSet\Services\Class\BACKPACK",Icon,,"0"
HKLM,"System\CurrentControlSet\Services\Class\BACKPACK",EnumPropPages,,"bpfinder.dll,EnumClassPages"
HKLM,"System\CurrentControlSet\Services\VxD\VBPD","Start",1,0
HKLM,"System\CurrentControlSet\Services\VxD\VBPD","StaticVxD",0,"VBPD.VXD"

[VBPD_ini]
%10%\system.ini,386Enh,"device=vbacpac.vxd","",0

[dev_copy]
bppnpdrv.mpd

[inf_copy]
bpfinder.inf

[dev_reg]
HKR,,DevLoader,0,*IOS
HKR,,DontLoadIfConflict,0,Y
HKR,,Polling,0,1
HKR,,PortDriver,0,bppnpdrv.mpd
HKR,,PollingSupportNeeded,1,01

;
; ================= WIN 2000 =================
;
; Install FINDER Section
;
[BPFinder.NT]
CopyFiles=finder_copy_nt, dev_copy_nt, 8000t_inf_copy

[finder_copy_nt]
bpfinder.sys
bpflt.sys

[8000t_inf_copy]
bp8000t.inf

;
; Service installation
;
[BPFinder.NT.Services]
AddService = bpfinder,%SPSVCINST_ASSOCSERVICE%, bpfinder_Service_Inst
AddService = bpflt,, bpflt_Service_Inst

;
; bpfinder driver install sections
;
[bpfinder_Service_Inst]
DisplayName    = %BP_Finder%
ServiceType    = 1               ; SERVICE_KERNEL_DRIVER
StartType      = 1               ; SERVICE_SYSTEM_START
ErrorControl   = 1               ; SERVICE_ERROR_NORMAL
ServiceBinary  = %12%\bpfinder.sys
LoadOrderGroup = Extended Base

;
; Install BPPNPDRV Section
;
[BPDriver.NT]

[dev_copy_nt]
bppnpdrv.sys

;-------------- bppnpdrv Service installation
[BPDriver.NT.Services]
AddService = bppnpdrv,%SPSVCINST_ASSOCSERVICE%, bppnpdrv_Service_Inst

; -------------- bppnpdrv driver install sections
[bppnpdrv_Service_Inst]
DisplayName    = %BP_Driver_2000%
ServiceType    = 1               ; SERVICE_KERNEL_DRIVER
StartType      = 3               ; SERVICE_DEMAND_START
ErrorControl   = 0               ; SERVICE_ERROR_IGNORE
ServiceBinary  = %12%\bppnpdrv.sys
LoadOrderGroup = SCSI Miniport

Addreg = bppnpdrv_addreg

[bppnpdrv_addreg]
HKR, "Parameters\PnpInterface", "1", 0x00010001, 0x00000001

;-------------- bpflt Service installation
[bpflt_Service_Inst]
DisplayName    = %bpflt_2000%
ServiceType    = 1               ; SERVICE_KERNEL_DRIVER
StartType      = 3               ; SERVICE_DEMAND_START
ErrorControl   = 0               ; SERVICE_ERROR_IGNORE
ServiceBinary  = %12%\bpflt.sys
LoadOrderGroup = PNP Filter

AddReg = BPFLT_AddReg

[BPFLT_AddReg]
HKLM,"SYSTEM\CurrentControlSet\Control\Class\{4d36e965-e325-11ce-bfc1-08002be10318}","LowerFilters",0x00010008,"bpflt"

;----------------------------------------------------------------------

[SourceDisksNames]
1=%DiskId1%,,,

[SourceDisksFiles]
bpfinder.vxd = 1
bpfinder.dll = 1
vbpd.vxd = 1
bppnpdrv.mpd = 1
bpfinder.inf = 1
bpfinder.sys = 1
bppnpdrv.sys = 1
bpflt.sys = 1
bpcpl.cpl = 1

[DestinationDirs]
DefaultDestDir = 11
dev_copy = 12
inf_copy = 17
8000t_inf_copy = 17
finder_copy_nt = 12
dev_copy_nt = 12
cpl_copy_nt = 11

;----------------------------------------------------------------------

[Strings]
MSI = "Micro Solutions, Inc."
ClassName = "BACKPACK"
BP_Finder = "BACKPACK Finder"
BP_Driver_95 = "BACKPACK Driver"
BP_Driver_2000 = "BACKPACK Driver"
bpflt_2000 = "BACKPACK Filter"
DiskId1 = "BACKPACK Installation Disk"
SPSVCINST_ASSOCSERVICE= 0x00000002I also located this "bpdetusb.inf" script which I suspect has to do with USB DETection- but don't quote me on that and I really don't remember this bpdetusb.inf file at all.

> ---------------bpdetusb.inf
[Version]
Signature = $CHICAGO$
Class = BACKPACK
ClassGuid = {B85B7C50-6A01-11d2-B841-00C04FAD5171}
Provider = %MSI%

[Manufacturer]
%MSI% = MSI_DETECT_USB

[MSI_DETECT_USB]
%usbcable1% = usbcable_inst, USB\VID_0AC9&PID_0000
%usbcable2% = usbcable_inst, USB\VID_0AC9&PID_0001
%bpusb%     = usbcable_inst, USB\VID_0AC9&PID_0010

[ClassInstall32]
Addreg = BackpackClassReg

[BackpackClassReg]
HKR,,,,"BACKPACK"
HKR,,Icon,,0
HKR,,SilentInstall,,1

;
; WIN 95/98
;
[usbcable_inst]
include = bpusbdrv.inf
needs = usbcable_install
CopyFiles = usbcable.copy, usb_inf_copy

;-----
; WIN 2000
;
[usbcable_inst.NT]
include = bpusbdrv.inf
needs = usbcable_install.NT
CopyFiles = usbcable.copy

[usbcable_inst.NT.Services]
include = bpusbdrv.inf
needs = usbcable_install.NT.Services

[Strings]
MSI = "Micro Solutions, Inc."
usbcable1 = "BACKPACK  USB 1 Cable"
usbcable2 = "BACKPACK  USB 2 Cable"
bpusb = "BACKPACK  USB"


---

### Post by northd_tech on 2011-10-26
Although it did not look exceedingly helpful, I did find this archived Ubuntuforums thread from about Nov. 2005 that might possibly have some relevant information:

**Re: MicroSolutions BackPack CD-R/W in Breezy**
[http://ubuntuforums.org/showthread.php?t=77900](http://ubuntuforums.org/showthread.php?t=77900)

> I have recently installed Breezy on a previously RH8 PC that was working fine with my MicroSolutions Parallel Port BackPack CD-R/W (Series 6). After repeated attempts at trying to make it work on FC3, I gave up and decided to try Breezy. This is my first experience of Ubuntu and I am impressed. For those of you who want to connect this archaic external CD-R/W drive here is how to do it. My script, which I stumbled upon after many RH8 tweaking days & nights are shown below. It also works on Breezy! All comment lines are included as possible fixes for your particular situation. Make sure your BackPack is connected to the parallel port before booting and your BIOS setting for the parallel port is: PCSPP,TRISTATE,EPP

You can check the Parallel port setting by:
cat /proc/sys/dev/parport/parport0/modes

# Start here...

# modprobe parport # Already maybe loaded
# modprobe parport_pc # Already maybe loaded

modprobe paride

#
# The following 2 steps are not necessary on Breezy...
# mkdir /lib/modules/$(LINUX_VERSION)/misc
# cp /lib/modules/$(LINUX_VERSION)/kernel/drivers/block/paride/bpck6.o /lib/modules/2.4.20-20.8/misc/backpack.o

echo "Inserting the necessary modules..."
modprobe bpck6
modprobe pg # For CD-R/W
modprobe cdrom
modprobe pcd # For CD-R

dmesg | grep paride
# Look for: "paride: bpck6 registered as protocol 0"

# modprobe pcd drive0=0x378,1 drive1=0x3bc,1 # Example syntax
# To support such a wide range of devices PARIDE, the parallel port IDE subsystem, is actually structured in three parts.
# There is a base paride module which provides a registry and some common methods for accessing the parallel ports.
# The second component is a set of high-level drivers for each of the different type of supported device:
# pd IDE disk
# pcd ATAPI CD-ROM
# pf ATAPI disk
# pt ATAPI tape
# pg ATAPI generic devices

# The pg driver exists mainly to support parallel port ATAPI CD-R and CD-RW devices.

#
# Run the commands below from a script
# ================================================== ==================
echo "Running the commands of Check4CDDrives..."
test `whoami` = 'root' || echo "You must be root to execute the commands."
cdrecord -scanbus > /dev/null
if ! (pidof kerneld || test -f "/proc/sys/kernel/modprobe"); then
echo "Neither kerneld nor kmod are running to automatically load modules".
fi
report_no_autoload() {
echo "Ensure the module $1 is loaded automatically next time."
}
if test ! -f "/proc/scsi/scsi"; then
report_no_autoload scsi_mod && modprobe scsi_mod
fi
if ! grep "^........ sg_" /proc/ksyms > /dev/null; then
report_no_autoload sg && modprobe sg
fi
if ! grep "^........ sr_" /proc/ksyms > /dev/null; then
report_no_autoload sr_mod && modprobe sr_mod
fi
if ! grep "^........ loop_" /proc/ksyms > /dev/null; then
report_no_autoload loop && insmod loop
fi
if ! grep iso9660 /proc/filesystems > /dev/null; then
report_no_autoload iso9660 && modprobe iso9660
fi
echo "The following is only needed for IDE/ATAPI CD-writers."
if ! grep ide-scsi /proc/ide/drivers > /dev/null; then
report_no_autoload ide-scsi && modprobe ide-scsi
fi
# ================================================== ==============

# Now check if it is recognized:
cdrecord -scanbus

# Mount to an appropriate location after placing a CD in the drive
mkdir /mnt/backpack
mount -t iso9660 /dev/pcd0 /mnt/backpack
ls -al /mnt/backpack # Works !

Edit:  also see this archived thread from Feb 2005 for Backpack DVD-RW

**can't get Microsolutions Backpack dvd+rw to work in Warty**
[http://ubuntuforums.org/showthread.php?t=15663](http://ubuntuforums.org/showthread.php?t=15663)

---

### Post by northd_tech on 2011-10-26
Going back to RTFM:

[http://manpages.ubuntu.com/manpages/lucid/man8/fxload.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/fxload.8.html)

> ...
**DESCRIPTION**

       **fxload** is a program which downloads firmware to USB  devices  based  on        AnchorChips   EZ-USB,   Cypress   EZ-USB  FX,  or  Cypress  EZ-USB  FX2        microcontrollers.  These have 8-bit 8051 cores with special  extensions        for  USB  I/O.   The  FX2  supports  high  speed USB 2.0 transfers (480        Mbit/sec) as well as full speed USB 1.1 transfers (12 Mbit/sec),  while        the   earlier   parts   supports  only  full  speed  transfers.   These        controllers have several package  options,  and  can  be  set  up  with        external memory (on-chip memory is usually about 8K), EEPROMs, and ROMs        when device costs allow.         This uses "usbfs" (older name:   "usbdevfs")  to  access  devices,  and        issues  vendor  specific control requests to download and reset the EZ-        USB  devices.    Normally,   firmware   will   then   "renumerate"   by        disconnecting  from USB and then reconnecting as a new device.  It then        appears with new device descriptors and functionality, as  provided  by        the firmware which has been downloaded.         To  support  some  non-firmware  applications,  this  can  also  set up        symbolic links for those usbfs names.  It can also change their  access        modes.  Both of these can help simplify software applications that need        to talk to USB devices using user mode drivers, don&#8217;t want to run  with        privileges  or  to  examine  all of the existing USB devices, and which        don&#8217;t need more kernel drivers.         See the _Linux-Hotplug_ web site for information about how to use  **fxload**        to download device firmware when hotplugging USB devices, using driver-        specific scripts stored in the _/etc/hotplug/usb_ directory. 
...
**[B]NOTES**[/B]

       This  program  implements  one  extension  to  the  standard "hex file"        format.  Lines beginning with a "#" character are ignored, and  may  be        used  to  hold copyright statements and other information.  Other tools        may not handle hexfiles using this extension.         

At this writing,[COLOR=Red]** "usbfs" is a kernel configuration option.  That  means        that  device drivers relying on user mode firmware downloading may need        to depend on that  kernel  configuration  option.   A  less  preferable        alternative  involves  compiling  the  firmware  into  the  kernel  and        managing downloads and renumeration there.  This is less preferable  in        part  because  much  device  firmware is provided with GPL-incompatible        licensing, and in part because storing such  firmware  firmware  wastes        kernel memory. **[/COLOR]

For   EZ-USB   family   devices,  the  hardware&#8217;s  first  stage  loader        (supporting the 0xA0 vendor request) can&#8217;t write into external  memory.        Configurations  that  put  firmware  into  external  memory thus need a        second stage loader.  For typical "flat" memory architectures, a loader        supporting  the  0xA3 vendor request is used to write into that memory.        Similarly, a second stage loader that supports the 0xA2 vendor  request        is  needed  when  writing boot firmware into an I2C EEPROM.  These 0xA2        and 0xA3 vendor commands are conventions defined by  Cypress.   Devices        that  use  bank  switching or similar mechanisms to stretch the 64KByte        address space may need different approach to loading firmware. 

Not all devices support EEPROM  updates.   Some  EZ-USB  based  devices        don&#8217;t  have  an  I2C  EEPROM;  many such EEPROMs are too small to store        firmware; and some firmware can&#8217;t be placed in bootable I2C EEPROMs.               **&#8220;fxload&#8221; package in Ubuntu**

               
[LIST=1]
[*]     [Ubuntu]("https://launchpad.net/ubuntu")
[*]     &#8220;fxload&#8221; package
[/LIST]
fxload: Firmware download to EZ-USB devices
[https://launchpad.net/ubuntu/+source/fxload](https://launchpad.net/ubuntu/+source/fxload)


**Source Package: fxload (0.0.20081013-1ubuntu1)  [[B]universe**] [/B]
[http://packages.ubuntu.com/source/lucid/fxload](http://packages.ubuntu.com/source/lucid/fxload)

---

### Post by northd_tech on 2011-10-26
> **northd_tech said:**
> 
At this writing,[COLOR=Red][B] "usbfs" is a kernel configuration  option.  That  means        that  device drivers relying on user mode  firmware downloading may need        to depend on that  kernel   configuration  option.   A  less  preferable        alternative   involves  compiling  the  firmware  into  the  kernel  and         managing downloads and renumeration there.  This is less preferable  in         part  because  much  device  firmware is provided with  GPL-incompatible        licensing, and in part be
cause storing such   firmware  firmware  wastes        kernel memory. [/B][/COLOR]

This is beginning to look like a fair portion of my external USB/firmware trouble- the **usbfs** that has been removed from recent Ubuntu kernels (apparently since 9.10 and approx kernel 2.6.31-17):

**Enabling USBFS in ubuntu 10.04**
[http://ubuntuforums.org/showthread.php?t=1532263](http://ubuntuforums.org/showthread.php?t=1532263)

> usbfs is no longer supported by the kernel (not since ~2.6.31-17 IIRC)  so quite a few older printers cause problems. There is a workaround, not  terribly satisfactory, but usually does the job. The following  commands:
     Code:
     sudo mount --bind /dev/bus /proc/bus
sudo ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices 
before printing should do the necessary. After printing it's probably advisable to reverse the above with:
     Code:
     sudo umount   /proc/bus 
as you may well break something else.[http://ubuntuforums.org/showpost.php?p=9363439&postcount=2](http://ubuntuforums.org/showpost.php?p=9363439&postcount=2)

Possible shell script workaround at:

**Usbfs Support, logic and understanding **
[http://www.linuxforums.org/forum/ubuntu-linux/121543-usbfs-support-logic-understanding.html#](http://www.linuxforums.org/forum/ubuntu-linux/121543-usbfs-support-logic-understanding.html#)

Edit:  see also:

**Fix &#8220;An error occurred while mounting /proc/bus/usb&#8221; Bootup Error after Upgrade to Lucid**
May 7, 2010 by [Ubuntu Genius]("http://ubuntugenius.wordpress.com/author/ubuntugenius/")
[http://ubuntugenius.wordpress.com/2010/05/07/fix-an-error-occurred-while-mounting-procbususb-bootup-error-after-upgrade-to-lucid/](http://ubuntugenius.wordpress.com/2010/05/07/fix-an-error-occurred-while-mounting-procbususb-bootup-error-after-upgrade-to-lucid/)

---

### Post by northd_tech on 2011-10-29
> **northd_tech said:**
> usbfs is no longer supported by the kernel (not since ~2.6.31-17 IIRC)   so quite a few older printers cause problems. There is a workaround, not   terribly satisfactory, but usually does the job. The following   commands:
     
     ```
sudo mount --bind /dev/bus /proc/bus
 sudo ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices 
```before printing should do the necessary. After printing it's probably advisable to reverse the above with:
     
     ```
sudo umount   /proc/bus 
```as you may well break something else.

The first code snippet above or some other thing broke my Linux boot (I'm unable to boot into Ubuntu 10.04.3 LTS without using a USB or CD/DVD rescue disk or my UE Ubuntu 2.7 Live DVD).

I'm getting STACKS of error messages that begin "udevd-work" but they scroll past awfully fast, with many of them mentioning **/sbin/modprobe** and **/sbin/init**.  I have looked around quite a bit in **/var/log/**, but my **grep**ping didn't find much in the way of "udevd-work" error messages.

I'm posting this from Vista (since I needed to rebuild my USB rescue stick with Parted Magic 6.7- the wireless connection quit there after I tried to save the persistent changes so I need to go back to the original Parted Magic .ISO file that DID have working wireless).  I cannot control or change too many things from the Ubuntu 10.04.3 LTS Live DVD either- I've had better luck using Parted Magic's linux and changing to /mnt/sda5/var/log/ to review the logfiles.

I do/did have **bootchart** installed on the 'broken' Ubuntu partition **/dev/sda5/**, and inspecting the .PNG graphic files, the boot process looks to be freezing during the **udev** process (but I cannnot access those files right now from the Vista OS to post them here).  There are also some archive files under **/var/log/bootchart/** on **/dev/sda5/** but those mainly look to be process statistics, not diagnostic/errors *per se.*

Image #1: (Oct. 26 PRE-'crash'):
[http://imageshack.us/photo/my-images/843/hpdv9820lucid20111026.png/](http://imageshack.us/photo/my-images/843/hpdv9820lucid20111026.png/)
[[IMG]http://img843.imageshack.us/img843/9092/hpdv9820lucid20111026.th.png[/IMG]](http://imageshack.us/photo/my-images/843/hpdv9820lucid20111026.png/)

Image #2 (Oct. 28- POST-'crash' with many "**udevd-work**" and "**/sbin/modprobe**" error messages:
[http://imageshack.us/photo/my-images/3/hpdv9820lucid20111028.png/](http://imageshack.us/photo/my-images/3/hpdv9820lucid20111028.png/)
[[IMG]http://img3.imageshack.us/img3/5282/hpdv9820lucid20111028.th.png[/IMG]](http://imageshack.us/photo/my-images/3/hpdv9820lucid20111028.png/)

I am trying to avoid re-installing Ubuntu over my previous partition if at all possible (and I would like to know how to** fix** this problem instead of 'paving over' it, but I haven't see this "**udevd-work**" boot hang problem before).

With all my booting off rescue discs, attempts using **boot-repair** and **boot_info_script.sh**, etc. I did discover that I still had an old **menu.lst** file lurking from Ubuntu 9.04 and about 2 years ago- I moved/renamed that and **boot_info_script.sh** no longer sees that file that might have interfered with Grub2 somehow.

The **boot_info_script.sh **recently told me this (before I moved that Grub[1] **menu.lst**, but I forgot to copy the newer RESULTS.txt while I was in Parted Magic, and my wireless networking wasn't working there anyway):

>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOT/BCD

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22
    Boot sector info:   Syslinux looks at sector 39816 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /multiboot 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sdc6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   According to the info in the boot sector, sdc6 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdc6 starts at sector 1483554618. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sdc7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   314,568,764   314,568,702   7 NTFS / exFAT / HPFS
/dev/sda2         464,230,305   488,396,799    24,166,495   7 NTFS / exFAT / HPFS
/dev/sda3         377,334,844   464,230,304    86,895,461   5 Extended
/dev/sda5         377,334,846   455,844,374    78,509,529  83 Linux
/dev/sda6         455,844,438   464,230,304     8,385,867  82 Linux swap / Solaris
/dev/sda4         314,568,765   377,334,719    62,765,955   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             44    15,679,439    15,679,396   b W95 FAT32


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   488,343,869   488,343,807   7 NTFS / exFAT / HPFS
/dev/sdc2         488,343,870   976,687,739   488,343,870   7 NTFS / exFAT / HPFS
/dev/sdc3         976,687,740 1,465,031,609   488,343,870   7 NTFS / exFAT / HPFS
/dev/sdc4       1,465,031,610 1,953,523,711   488,492,102   f W95 Extended (LBA)
/dev/sdc5       1,465,031,673 1,483,554,554    18,522,882   7 NTFS / exFAT / HPFS
/dev/sdc6       1,483,554,618 1,487,747,519     4,192,902   6 FAT16
/dev/sdc7       1,487,751,168 1,532,389,375    44,638,208   7 NTFS / exFAT / HPFS
/dev/sdc8       1,532,392,218 1,591,784,459    59,392,242   7 NTFS / exFAT / HPFS
/dev/sdc9       1,591,784,523 1,953,523,711   361,739,189   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/sda1        608A329A8A326CA2                       ntfs       Vista64_JonHP
/dev/sda2        F89A35E89A35A452                       ntfs       HP_RECOVERY
/dev/sda4        6A8D626A5A721890                       ntfs       CommonSpace1
/dev/sda5        d4d51f55-d761-4dac-b95c-eeca10eb553a   ext4       JonUU2_79modA
/dev/sda6        732636ca-5163-4be5-b549-7cd02d7c5dcd   swap       
/dev/sdb1        6C3A-E22D                              vfat       MULTIBOOT
/dev/sdc1        74EB3E075E7D553F                       ntfs       Bakup_NTFS1
/dev/sdc2        060CDB330CDB1C8D                       ntfs       4_Media
/dev/sdc3        21BE4CB92A7E6250                       ntfs       9G_storage
/dev/sdc5        01CBEFDB5C58F080                       ntfs       SergioL505_RecoveryD
/dev/sdc6        419B-E8F4                              vfat       2BG_FATOLD
/dev/sdc7        232077426B338BBB                       ntfs       Recover2
/dev/sdc8        783578773695B046                       ntfs       DualRecovery
/dev/sdc9        5EE9FE0131783E93                       ntfs       Spare172G

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda4        /media/sda4              fuseblk    (rw,allow_other,blksize=4096)


=========================== sda5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
splashimage (hd0,5)/boot/grub/splashimages/menu-sta.xpm.gz
default 0
timeout 10

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d4d51f55-d761-4dac-b95c-eeca10eb553a

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

# pass the 'ipv6.disable=1' kernel parameter (in your menu.lst)
# configure your net manually, deleting all 'ipv6' strings (in /etc/network/interfaces or in /etc/resolv.conf)


# pass the 'ipv6.disable=1' kernel parameter (in your menu.lst)
# configure your net manually, deleting all 'ipv6' strings (in /etc/network/interfaces or in /etc/resolv.conf)


# pass the 'ipv6.disable=1' kernel parameter (in your menu.lst)
# configure your net manually, deleting all 'ipv6' strings (in /etc/network/interfaces or in /etc/resolv.conf)

title Ubuntu 9.04, kernel 2.6.28-18-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.28-18-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro ipv6.disable=1
initrd /boot/initrd.img-2.6.28-18-generic
savedefault

title Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.28-18-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro single
initrd /boot/initrd.img-2.6.28-18-generic

title Ubuntu 9.04, kernel 2.6.28-17-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.28-17-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro ipv6.disable=1
initrd /boot/initrd.img-2.6.28-17-generic
savedefault

title Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-17-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro single
initrd /boot/initrd.img-2.6.28-17-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Ubuntu 9.04, UU2.3, kernel 2.6.28-19-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.28-19-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro 
initrd /boot/initrd.img-2.6.28-19-generic
savedefault

title Other operating systems:
root

title Windows Vista (loader)
root (hd0,0)
chainloader +1

title VistaRecovery (loader)
root (hd0,1)
chainloader +1
savedefault

--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="${saved_entry}"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=800x600x24
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "UE2.7 hacked 2.9 Linux 2.6.32-34-generic on /dev/sda5" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro   
    initrd    /boot/initrd.img-2.6.32-34-generic
}
menuentry "Ubuntu, with Linux 2.6.32-34-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
    echo    'Loading Linux 2.6.32-34-generic ...'
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-34-generic
}
menuentry "Ultimate Edition 2.7, with Linux 2.6.32-33-generic on /dev/sda5" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro   
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic on /dev/sda5" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro   
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "iffy from USB Multiboot x64Repair_Windows Vista (loader) (on /dev/sdb1)" {
    savedefault
    insmod fat
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6c3a-e22d
    chainloader +1
}
menuentry "Vista 64bit Home Premium(loader) (on /dev/sda1)" {
    savedefault
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 608A329A8A326CA2
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "*** CAUTION- HP Vista64 RECOVERY- can OVERWRITE Windows!!! *** (on /dev/sda2)" {
    savedefault
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set F89A35E89A35A452
    chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/sda2 /media/HP_RECOVERY ntfs-3g user,noauto 0 0
/dev/sda4 /media/CommonSpace1 ntfs-3g user 0 0
/dev/sda1 /media/Vista64_JonHP ntfs-3g user 0 0
/dev/sda5 / ext4 user 0 1
/dev/sda6 swap swap sw 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 180.309809685 = 193.606183936  boot/grub/core.img                             1
 214.172751427 = 229.966240768  boot/grub/grub.cfg                             2
 183.356520653 = 196.877564928  boot/grub/menu.lst                             1
 179.971213341 = 193.242618880  boot/grub/stage2                               1
 206.309172630 = 221.522787328  boot/initrd.img-2.6.32-21-generic              7
 215.043555260 = 230.901259264  boot/initrd.img-2.6.32-33-generic              2
 188.652773857 = 202.564373504  boot/initrd.img-2.6.32-34-generic              1
 184.606577873 = 198.219803648  boot/vmlinuz-2.6.32-21-generic                 1
 211.327254295 = 226.910911488  boot/vmlinuz-2.6.32-33-generic                 1
 184.651755333 = 198.268312576  boot/vmlinuz-2.6.32-34-generic                 1
 188.652773857 = 202.564373504  initrd.img                                     1
 206.309172630 = 221.522787328  initrd.img.old                                 7
 184.651755333 = 198.268312576  vmlinuz                                        1
 184.606577873 = 198.219803648  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  1b 33 96 d6 5d 49 df 34  d5 27 4e ce 99 d3 1b 0c  |.3..]I.4.'N.....|
00000010  4c 9d 06 d5 74 34 76 58  71 b5 7f 55 33 50 dc 5f  |L...t4vXq..U3P._|
00000020  c0 c5 96 bf 04 2b d8 ba  0a 1c 16 d8 3e eb 01 b6  |.....+......>...|
00000030  96 fd 01 7b 04 e4 26 85  62 d0 bb 2c 68 13 ff f3  |...{..&.b..,h...|
00000040  98 e3 30 2b 63 dd 39 19  b8 bd d9 a8 56 5b bd 93  |..0+c.9.....V[..|
00000050  fd 78 8d a9 aa 0d 33 b6  ff 32 8a d8 99 0b 27 27  |.x....3..2....''|
00000060  72 5d c7 f3 7e 90 b3 18  c3 f4 aa 23 c5 eb 30 0e  |r]..~......#..0.|
00000070  16 ba f5 f0 cf e0 73 a9  9a 89 7e 9f 38 e1 1b 3c  |......s...~.8..<|
00000080  50 5f ad 3b 3d 89 8a 07  2e 45 74 19 9b 3e 41 cd  |P_.;=....Et..>A.|
00000090  6b 7e d9 c6 18 4e a9 1f  6d d0 b6 d1 d2 b9 22 0b  |k~...N..m.....".|
000000a0  77 31 5d 87 ab 85 e8 94  d7 e1 3b e5 b4 3c 2d 5d  |w1].......;..<-]|
000000b0  37 3b e5 50 05 72 32 62  5f f3 61 2c a0 2c c4 03  |7;.P.r2b_.a,.,..|
000000c0  f0 27 a5 e7 8a 51 9b d9  a0 2c 86 77 6b f3 d3 30  |.'...Q...,.wk..0|
000000d0  ba a4 15 5d 9c 25 e8 29  1f 3e b0 53 1c 35 9c 6b  |...].%.).>.S.5.k|
000000e0  a1 a2 b5 c9 94 64 7b 7e  c0 cd 7b 1f 3f 42 2f d9  |.....d{~..{.?B/.|
000000f0  1d 23 fb 83 bc 6f d2 5f  af fa ad 31 11 f8 75 2a  |.#...o._...1..u*|
00000100  49 6a 58 dd 32 b3 db 7a  45 69 0d e9 f6 4d 12 ec  |IjX.2..zEi...M..|
00000110  78 1d 56 6c c5 58 1a b0  92 9e 74 f7 9d 17 90 1f  |x.Vl.X....t.....|
00000120  ce 42 15 62 54 c5 11 44  c4 75 7c 6a 29 42 7a da  |.B.bT..D.u|j)Bz.|
00000130  e5 77 36 85 d3 07 bd 34  43 85 d1 3e f2 68 18 59  |.w6....4C..>.h.Y|
00000140  02 7a 22 ef c1 53 c5 69  d5 b8 c5 1b 11 07 d1 88  |.z"..S.i........|
00000150  a8 a1 f8 ae 6e ac 36 2b  31 69 98 32 dd cf 15 a2  |....n.6+1i.2....|
00000160  4c 66 ef ad 44 08 60 99  34 ed 46 db fd 43 8f a2  |Lf..D.`.4.F..C..|
00000170  3c 2a 01 1c d3 ac 44 63  c4 ad f3 e8 37 d1 bd c2  |<*....Dc....7...|
00000180  b3 5c 30 08 85 fc b7 ca  3d b5 29 80 ee 8b 07 6e  |.\0.....=.)....n|
00000190  b7 21 b4 04 85 9d df d7  d9 83 51 09 7d a5 4d ec  |.!........Q.}.M.|
000001a0  da f5 6c 5b a2 24 0c bc  0e 62 db f8 9b 3a bc fe  |..l[.$...b...:..|
000001b0  76 da c1 6c 44 27 c9 e4  aa a7 2b 75 be 43 00 fe  |v..lD'....+u.C..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 d9 f5 ad 04 00 fe  |................|
000001d0  ff ff 05 fe ff ff db f5  ad 04 8a f5 7f 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file or automatically
Edit:  related (pre-'crash') post #31 at:

[http://ubuntuforums.org/showthread.php?t=1468486&page=4](http://ubuntuforums.org/showthread.php?t=1468486&page=4)

---

### Post by northd_tech on 2011-10-30
> **northd_tech said:**
> 
The **boot_info_script.sh **recently told me this (before I moved that Grub[1] **menu.lst**, but I forgot to copy the newer RESULTS.txt while I was in Parted Magic, and my wireless networking wasn't working there anyway):


To simplify things a little, I ran another boot info shell inquiry  WITHOUT my external USB hard disk plugged in this time (since it has 6  partitions).  This time, I booted off my 8GB USB rescue stick, which has  PartedMagic 6.7 on it.  This is the more recent output (AFTER I had deleted the **menu.lst** file that I recently discovered was still hanging on from my old Ubuntu 9.04 & Grub[1] days:

> 
============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOT/BCD

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22
    Boot sector info:   Syslinux looks at sector 39816 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /multiboot 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   314,568,764   314,568,702   7 NTFS / exFAT / HPFS
/dev/sda2         464,230,305   488,396,799    24,166,495   7 NTFS / exFAT / HPFS
/dev/sda3         377,334,844   464,230,304    86,895,461   5 Extended
/dev/sda5         377,334,846   455,844,374    78,509,529  83 Linux
/dev/sda6         455,844,438   464,230,304     8,385,867  82 Linux swap / Solaris
/dev/sda4         314,568,765   377,334,719    62,765,955   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             44    15,679,439    15,679,396   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/sda1        608A329A8A326CA2                       ntfs       Vista64_JonHP
/dev/sda2        F89A35E89A35A452                       ntfs       HP_RECOVERY
/dev/sda4        6A8D626A5A721890                       ntfs       CommonSpace1
/dev/sda5        d4d51f55-d761-4dac-b95c-eeca10eb553a   ext4       JonUU2_79modA
/dev/sda6        732636ca-5163-4be5-b549-7cd02d7c5dcd   swap       
/dev/sdb1        6C3A-E22D                              vfat       MULTIBOOT

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/sda1              fuseblk    (rw,allow_other,blksize=4096)
/dev/sda4        /media/sda4              fuseblk    (rw,allow_other,blksize=4096)
/dev/sda5        /media/sda5              ext4       (rw)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="${saved_entry}"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=800x600x24
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "UE2.7 hacked 2.9 Linux 2.6.32-34-generic on /dev/sda5" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro   
    initrd    /boot/initrd.img-2.6.32-34-generic
}
menuentry "Ubuntu, with Linux 2.6.32-34-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
    echo    'Loading Linux 2.6.32-34-generic ...'
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-34-generic
}
menuentry "Ultimate Edition 2.7, with Linux 2.6.32-33-generic on  /dev/sda5" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro   
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic on /dev/sda5" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro   
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d4d51f55-d761-4dac-b95c-eeca10eb553a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d4d51f55-d761-4dac-b95c-eeca10eb553a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "iffy from USB Multiboot x64Repair_Windows Vista (loader) (on /dev/sdb1)" {
    savedefault
    insmod fat
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6c3a-e22d
    chainloader +1
}
menuentry "Vista 64bit Home Premium(loader) (on /dev/sda1)" {
    savedefault
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 608A329A8A326CA2
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "*** CAUTION- HP Vista64 RECOVERY- can OVERWRITE Windows!!! *** (on /dev/sda2)" {
    savedefault
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set F89A35E89A35A452
    chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/sda2 /media/HP_RECOVERY ntfs-3g user,noauto 0 0
/dev/sda4 /media/CommonSpace1 ntfs-3g user 0 0
/dev/sda1 /media/Vista64_JonHP ntfs-3g user 0 0
/dev/sda5 / ext4 user 0 1
/dev/sda6 swap swap sw 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 180.309809685 = 193.606183936  boot/grub/core.img                             1
 214.172751427 = 229.966240768  boot/grub/grub.cfg                             2
 179.971213341 = 193.242618880  boot/grub/stage2                               1
 206.309172630 = 221.522787328  boot/initrd.img-2.6.32-21-generic              7
 215.043555260 = 230.901259264  boot/initrd.img-2.6.32-33-generic              2
 188.652773857 = 202.564373504  boot/initrd.img-2.6.32-34-generic              1
 184.606577873 = 198.219803648  boot/vmlinuz-2.6.32-21-generic                 1
 211.327254295 = 226.910911488  boot/vmlinuz-2.6.32-33-generic                 1
 184.651755333 = 198.268312576  boot/vmlinuz-2.6.32-34-generic                 1
 188.652773857 = 202.564373504  initrd.img                                     1
 206.309172630 = 221.522787328  initrd.img.old                                 7
 184.651755333 = 198.268312576  vmlinuz                                        1
 184.606577873 = 198.219803648  vmlinuz.old                                    1

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/initrd                                    1
            ?? = ??             boot/vmlinuz                                   1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  1b 33 96 d6 5d 49 df 34  d5 27 4e ce 99 d3 1b 0c  |.3..]I.4.'N.....|
00000010  4c 9d 06 d5 74 34 76 58  71 b5 7f 55 33 50 dc 5f  |L...t4vXq..U3P._|
00000020  c0 c5 96 bf 04 2b d8 ba  0a 1c 16 d8 3e eb 01 b6  |.....+......>...|
00000030  96 fd 01 7b 04 e4 26 85  62 d0 bb 2c 68 13 ff f3  |...{..&.b..,h...|
00000040  98 e3 30 2b 63 dd 39 19  b8 bd d9 a8 56 5b bd 93  |..0+c.9.....V[..|
00000050  fd 78 8d a9 aa 0d 33 b6  ff 32 8a d8 99 0b 27 27  |.x....3..2....''|
00000060  72 5d c7 f3 7e 90 b3 18  c3 f4 aa 23 c5 eb 30 0e  |r]..~......#..0.|
00000070  16 ba f5 f0 cf e0 73 a9  9a 89 7e 9f 38 e1 1b 3c  |......s...~.8..<|
00000080  50 5f ad 3b 3d 89 8a 07  2e 45 74 19 9b 3e 41 cd  |P_.;=....Et..>A.|
00000090  6b 7e d9 c6 18 4e a9 1f  6d d0 b6 d1 d2 b9 22 0b  |k~...N..m.....".|
000000a0  77 31 5d 87 ab 85 e8 94  d7 e1 3b e5 b4 3c 2d 5d  |w1].......;..<-]|
000000b0  37 3b e5 50 05 72 32 62  5f f3 61 2c a0 2c c4 03  |7;.P.r2b_.a,.,..|
000000c0  f0 27 a5 e7 8a 51 9b d9  a0 2c 86 77 6b f3 d3 30  |.'...Q...,.wk..0|
000000d0  ba a4 15 5d 9c 25 e8 29  1f 3e b0 53 1c 35 9c 6b  |...].%.).>.S.5.k|
000000e0  a1 a2 b5 c9 94 64 7b 7e  c0 cd 7b 1f 3f 42 2f d9  |.....d{~..{.?B/.|
000000f0  1d 23 fb 83 bc 6f d2 5f  af fa ad 31 11 f8 75 2a  |.#...o._...1..u*|
00000100  49 6a 58 dd 32 b3 db 7a  45 69 0d e9 f6 4d 12 ec  |IjX.2..zEi...M..|
00000110  78 1d 56 6c c5 58 1a b0  92 9e 74 f7 9d 17 90 1f  |x.Vl.X....t.....|
00000120  ce 42 15 62 54 c5 11 44  c4 75 7c 6a 29 42 7a da  |.B.bT..D.u|j)Bz.|
00000130  e5 77 36 85 d3 07 bd 34  43 85 d1 3e f2 68 18 59  |.w6....4C..>.h.Y|
00000140  02 7a 22 ef c1 53 c5 69  d5 b8 c5 1b 11 07 d1 88  |.z"..S.i........|
00000150  a8 a1 f8 ae 6e ac 36 2b  31 69 98 32 dd cf 15 a2  |....n.6+1i.2....|
00000160  4c 66 ef ad 44 08 60 99  34 ed 46 db fd 43 8f a2  |Lf..D.`.4.F..C..|
00000170  3c 2a 01 1c d3 ac 44 63  c4 ad f3 e8 37 d1 bd c2  |<*....Dc....7...|
00000180  b3 5c 30 08 85 fc b7 ca  3d b5 29 80 ee 8b 07 6e  |.\0.....=.)....n|
00000190  b7 21 b4 04 85 9d df d7  d9 83 51 09 7d a5 4d ec  |.!........Q.}.M.|
000001a0  da f5 6c 5b a2 24 0c bc  0e 62 db f8 9b 3a bc fe  |..l[.$...b...:..|
000001b0  76 da c1 6c 44 27 c9 e4  aa a7 2b 75 be 43 00 fe  |v..lD'....+u.C..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 d9 f5 ad 04 00 fe  |................|
000001d0  ff ff 05 fe ff ff db f5  ad 04 8a f5 7f 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file or automaticallyStill no luck booting Ubuntu 10.04.3 LTS off the hard disk, but I think I will attempt plugging in the external Backpack USB drive to see if it will bypass the "udevd-work" part where it seems to be 'hanging' repeatedly.  I might also wait for an EXCEEDINGLY long time to see if it will somehow bypass the** udev **section(s).

---

### Post by northd_tech on 2011-10-30
Also, this may or may not be helpful information:

> **cat /media/sda5/lib/init/fstab**
# /lib/init/fstab: static file system information.
#
# These are the filesystems that are always mounted on boot, you can
# override any of these by copying the appropriate line from this file into
# /etc/fstab and tweaking it as you see fit.  See fstab(5).
#
# <file system> <mount point>             <type>          <options>                    <dump> <pass>
/dev/root       /                         rootfs          defaults                          0 1
none            /proc                     proc            nodev,noexec,nosuid               0 0
none            /proc/sys/fs/binfmt_misc  binfmt_misc     nodev,noexec,nosuid,optional      0 0
none            /sys                      sysfs           nodev,noexec,nosuid               0 0
none            /sys/fs/fuse/connections  fusectl         optional                          0 0
none            /sys/kernel/debug         debugfs         optional                          0 0
none            /sys/kernel/security      securityfs      optional                          0 0
none            /spu                      spufs           gid=spu,optional                  0 0
none            /dev                      devtmpfs,tmpfs  mode=0755                         0 0
none            /dev/pts                  devpts          noexec,nosuid,gid=tty,mode=0620   0 0
none            /dev/shm                  tmpfs           nosuid,nodev                      0 0
none            /tmp                      none            defaults                          0 0
none            /var/run                  tmpfs           mode=0755,nosuid,showthrough      0 0
none            /var/lock                 tmpfs           nodev,noexec,nosuid,showthrough   0 0
none            /lib/init/rw              tmpfs           mode=0755,nosuid,optional         0 0


Edit: It looked like only one file had been modified in the last 2 weeks in this directory:
[B]
/media/sda5/lib/udev/rules.d/[/B]

This is the file that was last modified on Oct. 20 (nearly one week BEFORE the Ubuntu **udev** booting problem started):
[B]
/media/sda5/lib/udev/rules.d/64-xorg-xkb.rules
-rw-r--r--    1 root     root           537 Oct 20 09:04 64-xorg-xkb.rules

[/B]> root@PartedMagic:/media/sda5/lib/udev/rules.d# **cat 64-xorg-xkb.rules **
ACTION!="add|change", GOTO="xorg_xkb_end"
SUBSYSTEM!="input", GOTO="xorg_xkb_end"
KERNEL!="event*", GOTO="xorg_xkb_end"

# import keyboard layout from /etc/default/keyboard
ENV{ID_INPUT_KEY}=="?*", IMPORT{program}="/bin/grep ^XKB /etc/default/console-setup"

# ignore "SKIP" keyboard model, which is a magic value from console-setup's debconf
ENV{XKBMODEL}=="SKIP", ENV{XKBMODEL}=""
# Similarly, ignore this broken default variant, which breaks keyboard entirely
ENV{XKBVARIANT}=="U.S. English", ENV{XKBVARIANT}=""

LABEL="xorg_xkb_end"


---

### Post by northd_tech on 2011-10-30
In one of my many reboots with various rescue and Live Linux versions, I was finally able to read where exactly it looks like my boot troubles are beginning.

Right after and below "fsck from util-linux-ng 2.17.2" I see:
> mountall: mount / [505] : Permission denied I still haven't found where this is being called from.  In **/mnt/sda5/etc/init/ **, the newest file modification was 28 Apr 2011 (months before my trouble began).  In directory **/mnt/sda5/etc/init.d/ **I did locate 2 files that could be related to my boot troubles based upon the file timestamp:

> -rwxr-xr-x 1 root root 13333 2011-10-27 02:34 vmware
-rwxr-xr-x 1 root root  2908 2011-10-27 02:35 vmware-USBArbitrator
**vmware-USBArbitrator:**
> #!/usr/bin/env bash
#
# Copyright 1998-2010 VMware, Inc.  All rights reserved.
#
# This script manages the VMware USB Arbitrator service
#

### BEGIN INIT INFO
# Provides: vmware-USBArbitrator
# Required-Start: localfs
# Required-Stop: localfs
# X-Start-Before: 
# X-Stop-After: 
# Default-Start: 2 3 5
# Default-Stop: 0 6
# Short-Description: This services starts and stops the USB Arbitrator.
### END INIT INFO


# Load bootstrapper info
. /etc/vmware/bootstrap

# This defines echo_success() and echo_failure() on RedHat
if [ -r "$INITSCRIPTDIR"'/functions' ]; then
   . "$INITSCRIPTDIR"'/functions'
fi

vmware_failed() {
  if [ "`type -t 'echo_failure' 2>/dev/null`" = 'function' ]; then
    echo_failure
  else
    echo -n "$rc_failed"
  fi
}

vmware_success() {
  if [ "`type -t 'echo_success' 2>/dev/null`" = 'function' ]; then
    echo_success
  else
    echo -n "$rc_done"
  fi
}

# Execute a macro
vmware_exec() {
  local msg="$1"  # IN
  local func="$2" # IN
  shift 2

  # On Caldera 2.2, SIGHUP is sent to all our children when this script exits
  # I wanted to use shopt -u huponexit instead but their bash version
  # 1.14.7(1) is too old
  #
  # Ksh does not recognize the SIG prefix in front of a signal name
  if [ "$VMWARE_DEBUG" = 'yes' ]; then
    (trap '' HUP; "$func" "$@")
  else
    (trap '' HUP; "$func" "$@") >/dev/null 2>&1
  fi
  if [ "$?" -gt 0 ]; then
    vmware_failed
    echo
    return 1
  fi

  vmware_success
  echo
  return 0
}

# Start the virtual machine USB Arbitrator service
vmwareStartUSBArbitrator() {
    # The executable checks for already running instances, so it
    #  is safe to just run it.
    "$BINDIR"/vmware-usbarbitrator
}

# Stop the virtual machine USB Arbitrator service
vmwareStopUSBArbitrator() {
   # Find the running process
   # grep instead of pgrep...  Turns out to be more reliable.  pgrep
   #  would return extranneous results.
   pid=`pgrep -f "$BINDIR"/vmware-usbarbitrator`
   # If it is not running
   if [ $? -eq 0 ]; then
     # PID was found, stop it.
     kill $pid
     return 0
   else
     # No process found.
     return 0
   fi
}

vmwareService() {
   case "$1" in
      start)
         vmware_exec 'VMware USB Arbitrator' vmwareStartUSBArbitrator
         exitcode=$(($exitcode + $?))
         if [ "$exitcode" -gt 0 ]; then
            exit 1
         fi
         ;;
      stop)
         vmware_exec 'VMware USB Arbitrator' vmwareStopUSBArbitrator
         exitcode=$(($exitcode + $?))
         if [ "$exitcode" -gt 0 ]; then
            exit 1
         fi
         ;;
      restart)
         "$SCRIPTNAME" stop && "$SCRIPTNAME" start
         ;;
      *)
         echo "Usage: $BASENAME {start|stop|restart}"
         exit 1
   esac
}

SCRIPTNAME="$0"
BASENAME=`basename "$SCRIPTNAME"`

# Check permissions
if [ "`id -ur`" != '0' ]; then
   echo 'Error: you must be root.'
   echo
   exit 1
fi

vmwareService "$1"

exit 0**vmware**
>  #!/usr/bin/env bash
#
# Copyright 1998-2008 VMware, Inc.  All rights reserved.
#
# This script manages the services needed to run VMware software.
#

### BEGIN INIT INFO
# Provides: vmware
# Required-Start: $network $syslog
# Required-Stop: $network $syslog
# X-Start-Before: 
# X-Stop-After: 
# Default-Start: 2 3 5
# Default-Stop: 0 6
# Short-Description: This service starts and stops VMware services
### END INIT INFO


ETCDIR=/etc/vmware
VMIS_MAJOR_VERSION=1

. $ETCDIR/bootstrap
libdir="$LIBDIR"/vmware

. "$libdir"/scripts/util.sh

load_settings "$libdir" || exit 1

VNETLIB_LOG=/var/log/vnetlib
PRODUCT_NAME="VMware VMX"
COMPONENT_NAME="vmware-vmx"

# This comment is a hack to prevent RedHat distributions from outputing
# "Starting <basename of this script>" when running this startup script.
# We just need to write the word daemon followed by a space

# This defines echo_success() and echo_failure() on RedHat
if [ -r "$INITSCRIPTDIR"'/functions' ]; then
   . "$INITSCRIPTDIR"'/functions'
fi

# This defines $rc_done and $rc_failed on S.u.S.E.
if [ -f /etc/rc.config ]; then
   # Don't include the entire file: there could be conflicts
   rc_done=`(. /etc/rc.config; echo "$rc_done")`
   rc_failed=`(. /etc/rc.config; echo "$rc_failed")`
else
   # Make sure the ESC byte is literal: Ash does not support echo -e
   rc_done='[71G done'
   rc_failed='[71Gfailed'
fi

subsys=vmware
driver=vmmon
vnet=vmnet
vmblock=vmblock
vmci=vmci
vmhgfs=vmhgfs
vsock=vsock

vmciNode=vmci
vsockNode=vsock

# SHM settings
shmmaxPath=/proc/sys/kernel/shmmax
shmmaxMinValue=268435456 # 256MB

#
# Are we running in a VM?
#
vmwareInVM() {
   "$BINDIR"/checkvm >/dev/null 2>&1
}

#
# Report a positive number if there are any VMs running.
# May not be the actual vmmon reference count.
#
vmmonUseCount() {
   local count
   # Beware of module dependencies here. An exact match is important
   count=`/sbin/lsmod | awk 'BEGIN {n = 0} {if ($1 == "'"$driver"'") n = $3} END {print n}'`
   # If CONFIG_MODULE_UNLOAD is not set in the kernel, lsmod prints '-' instead of the
   # reference count, so ask vmrun, or if we don't have vmrun, look for running vmx processes
   if [ x${count} = "x-" ]
   then
      type vmrun > /dev/null 2>&1
      if [ $? -eq 0 ]
      then
         count=`vmrun list | awk 'BEGIN {n=0} /^Total running VMs:/ {n = $4} END {print n}'`
      else
         count=`ps -afe | grep "/bin/vmware-vmx" | grep -v grep | wc -l`
      fi
   fi
   echo $count
}

# Is a given module loaded?
isLoaded() {
   local module="$1"

   /sbin/lsmod | awk 'BEGIN {n = "no";} {if ($1 == "'"$module"'") n = "yes";} END {print n;}'
}

# Build a Linux kernel integer version
kernelVersionInteger() {
   echo $(((($1 * 256) + $2) * 256 + $3))
}

# Get the running kernel integer version
getVersionInteger() {
   local version_uts
   local v1
   local v2
   local v3

   version_uts=`uname -r`

   # There is no double quote around the back-quoted expression on purpose
   # There is no double quote around $version_uts on purpose
   set -- `IFS='.'; echo $version_uts`
   v1="$1"
   v2="$2"
   v3="$3"
   # There is no double quote around the back-quoted expression on purpose
   # There is no double quote around $v3 on purpose
   set -- `IFS='-ABCDEFGHIJKLMNOPQRSTUVWXYZ_abcdefghijklmnopqrstuvwxyz'; echo $v3`
   v3="$1"

   kernelVersionInteger "$v1" "$v2" "$v3"
}

vmwareLoadModule() {
   /sbin/insmod -s -f "/lib/modules/`uname -r`/misc/$1.ko" || exit 1
   return 0
}

vmwareUnloadModule() {
   if [ "`isLoaded "$1"`" = 'yes' ]; then
      /sbin/rmmod "$1" || exit 1
   fi
   return 0
}

# Start the virtual machine monitor kernel service
vmwareStartVmmon() {
   vmwareLoadModule $driver
}

# Stop the virtual machine monitor kernel service
vmwareStopVmmon() {
   vmwareUnloadModule $driver
}

# Start the virtual ethernet kernel service
vmwareStartVmnet() {
   vmwareLoadModule $vnet
   "$BINDIR"/vmware-networks --start >> $VNETLIB_LOG 2>&1
}

# Stop the virtual ethernet kernel service
vmwareStopVmnet() {
   "$BINDIR"/vmware-networks --stop >> $VNETLIB_LOG 2>&1
   vmwareUnloadModule $vnet
}

# Returns 0 if networking is enabled, otherwise 1
vmwareIsNetworkingEnabled() {
  [ "$vmdb_NETWORKING" = 'yes' ]
  return
}

# Start the virtual machine communication interface kernel service
vmwareStartVmci() {
   # only load vmci if it's not already loaded
   if [ "`isLoaded "$vmci"`" = 'no' ]; then
      vmwareLoadModule "$vmci"
   fi
   vmware_rm_stale_node "$vmciNode"
   if [ ! -e "/dev/$vmciNode" ]; then
      local minor=`cat /proc/misc | grep $vmciNode | awk '{print $1}'`
      mknod --mode=666 "/dev/$vmciNode" c 10 "$minor"
   else
      chmod 666 "/dev/$vmciNode"
   fi

   return 0
}

# Make sure the system has enough shared memory available to cover shmmaxMinValue.
# To handle overflow/wrapping, check that shmmax is greater than 1 since any overflow
# will make shmmax look negative.  At least until shmmax or shmmaxMinValue wrap around
# again.
vmwareCheckSharedMemory() {
   if [ -f "$shmmaxPath" ]; then
      shmmax=`cat $shmmaxPath`
      # Account for numbers that are too large that they wrap around and alias
      # to a smaller number or they are outright set to -1.  If "1 < XXXX" fails
      # then the XXX value is # out of bounds.  The only acceptable combo is that
      # both values satisfy that condition, else report that the max value the
      # system supports may not satisfy this programs requirements.
      if  ((  $shmmax < 1 )) || (( $shmmaxMinValue < 1 )) \
       || (( $shmmax < $shmmaxMinValue )) ; then
         echo "$shmmaxMinValue" > "$shmmaxPath"
         echo ""
         echo "Setting the max shared memory the system will allow to $shmmaxMinValue."
         echo ""
      fi
   fi
   return 0
}


# Stop the virtual machine communication interface kernel service
vmwareStopVmci() {
   # Hosted now has to interface with Tools.  vmhgfs could possibly be loaded, which
   # will interfere with the removal of vmci.  Only unload it if it's already
   # loaded.
   if [ "`isLoaded "$vmhgfs"`" = 'yes' ]; then
      vmwareUnloadModule "$vmhgfs"
   fi


   # only unload vmci if it's already loaded
   if [ "`isLoaded "$vmci"`" = 'yes' ]; then
     vmwareUnloadModule "$vmci"
   fi
   rm -f "/dev/$vmciNode"
}

isVmciNeeded() {
   if [ "$vmdb_VMCI_CONFED" = 'yes' ]; then
      echo yes
   else
      echo no
   fi
}

# starts after vmci is loaded
vmwareStartVsock() {
   # only load vsock if it's not already loaded
   if [ "`isLoaded "$vsock"`" = 'no' ]; then
      vmwareLoadModule "$vsock"
   fi
   vmware_rm_stale_node "$vsockNode"
   # Give udev 5 seconds to create our node
   vmware_delay_for_node "/dev/$vsockNode" 5
   if [ ! -e "/dev/$vsockNode" ]; then
      local minor=`cat /proc/misc | grep $vsockNode | awk '{print $1}'`
      mknod --mode=666 "/dev/$vsockNode" c 10 "$minor"
   else
      chmod 666 "/dev/$vsockNode"
   fi

   return 0
}

# unloads before vmci
vmwareStopVsock() {
   # only unload vsock if it's already loaded
   if [ "`isLoaded "$vsock"`" = 'yes' ]; then
     vmwareUnloadModule "$vsock"
   fi
   rm -f /dev/vsock
}

isVsockNeeded() {
   if [ "$vmdb_VSOCK_CONFED" = 'yes' ]; then
      echo yes
   else
      echo no
   fi
}

vmware_start_authdlauncher() {
   vmware_bg_exec "`vmware_product_name` Authentication Daemon" \
      "$SBINDIR/vmware-authdlauncher"
}

vmware_stop_authdlauncher() {
   local launcherpid=`pidof vmware-authdlauncher`
   if [ -n "$launcherpid" ]; then
      vmware_synchrone_kill $launcherpid "TERM"
   fi
}

vmwareService() {
   case "$1" in
      start)
         if vmwareInVM; then
            # Refuse to start services in a VM: they are useless
            exit 1
         fi

         echo 'Starting VMware services:'
         exitcode='0'

         vmware_exec 'Virtual machine monitor' vmwareStartVmmon
         exitcode=$(($exitcode + $?))

         if [ "`isVmciNeeded`" = 'yes' ]; then
            vmware_exec 'Virtual machine communication interface' vmwareStartVmci
            exitcode=$(($exitcode + $?))
         fi

         # vsock needs vmci started first
         if [ "`isVsockNeeded`" = 'yes' ]; then
            vmware_exec 'VM communication interface socket family' vmwareStartVsock
            # a vsock failure to load shouldn't cause the init to fail completely.
         fi

         if [ "`is_vmblock_needed`" = 'yes' ] ; then
            vmware_exec 'Blocking file system' vmware_start_vmblock
            exitcode=$(($exitcode + $?))
         fi

         # Try to load parport_pc.
         /sbin/modprobe parport_pc >/dev/null 2>&1

         if vmwareIsNetworkingEnabled; then
            vmware_exec 'Virtual ethernet' vmwareStartVmnet
            exitcode=$(($exitcode + $?))
         fi

         vmware_exec 'VMware Authentication Daemon' vmware_start_authdlauncher

         if [ "$exitcode" -gt 0 ]; then
            exit 1
         fi

         [ -d /var/lock/subsys ] || mkdir -p /var/lock/subsys
         touch /var/lock/subsys/"$subsys"

         vmware_exec "Shared Memory Available"  vmwareCheckSharedMemory
      ;;

      stop)
         echo 'Stopping VMware services:'
         exitcode='0'

         vmware_exec 'VMware Authentication Daemon' vmware_stop_authdlauncher

         # If the 'K' version of this script is running, the system is
         # stoping services not because the user is running vmware-config.pl
         # or running the initscript directly but because the user wants to
         # shutdown.  Suspend all VMs.
         if [ "`echo $BASENAME | sed -ne '/^K[0-9].vmware/p'`" ] ; then
            if [ -x "$BINDIR"/vmrun ] ; then
               for i in `pidof vmware-vmx` ; do
                  "$BINDIR"/vmrun suspend `ps -p $i -f | \
                       sed -ne '/vmware/s/.* \(\/.*\.vmx\)/\1/p'` 2> /dev/null
               done
            fi

         fi

         if [ "`vmmonUseCount`" -gt 0 ]; then
            echo 'At least one instance of '"$PRODUCT_NAME"' is still running.' 1>&2
            echo 'Please stop all running instances of '"$PRODUCT_NAME"' first.' 1>&2
            echo " " >&2

            # Since we stopped authdlauncher to prevent new connections before disabling
            # any vmxs, need to restart it here to restore the environment back to
            # what it was before this init script ran.
            vmware_exec 'VMware Authentication Daemon' vmware_start_authdlauncher

            # The unconfigurator handle this exit code differently
            exit 2
         fi

         # vmci is used by vsock so the module can't unload until vsock does.
         if [ "`isVsockNeeded`" = 'yes' ]; then
            vmware_exec 'VM communication interface socket family' vmwareStopVsock
            exitcode=$(($exitcode + $?))
         fi

         if [ "`isVmciNeeded`" = 'yes' ]; then
            vmware_exec 'Virtual machine communication interface' vmwareStopVmci
            exitcode=$(($exitcode + $?))
         fi

         vmware_exec 'Virtual machine monitor' vmwareStopVmmon
         exitcode=$(($exitcode + $?))

         if [ "`is_vmblock_needed`" = 'yes' ] ; then
            vmware_exec 'Blocking file system' vmware_stop_vmblock
            exitcode=$(($exitcode + $?))
         fi

         # Try to unload parport_pc. Failure is allowed as it does not
         # exist on kernels 2.0, and some other process could be using
         # it.
         /sbin/modprobe -r parport_pc >/dev/null 2>&1

         if vmwareIsNetworkingEnabled; then
        vmwareStopVmnet
         fi

         # The vmware and vmware-tray processes don't terminate automatically
         # when the other services are shutdown.  They persist after calling
         # 'init.d/vmware stop' and will happily keep going through an init
         # start command, continuing to minimally function, blissfully ignorant.
         # Time for a buzzkill.
         for i in `pidof vmware vmware-tray` ; do
            vmware_synchrone_kill $i "INT"
         done

         if [ "$exitcode" -gt 0 ]; then
            exit 1
         fi

         rm -f /var/lock/subsys/"$subsys"
      ;;

      status)
         if [ "`vmmonUseCount`" -gt 0 ]; then
            echo 'At least one instance of '"$PRODUCT_NAME"' is still running.'
            echo
            if [ "$2" = "vmcount" ]; then
               exit 2
            fi
         fi
         if [ "$2" = "vmcount" ]; then
               exit 0
         fi

         exitcode='0'

         echo -n "Module $driver "
         [ "`isLoaded "$driver"`" = 'yes' ] && echo loaded || echo "not loaded"
         if vmwareIsNetworkingEnabled; then
            echo -n "Module $vnet "
            [ "`isLoaded "$vnet"`" = 'yes' ] && echo loaded || echo "not loaded"
         fi

         if [ "$exitcode" -gt 0 ]; then
            exit 1
         fi
      ;;

      restart)
         "$SCRIPTNAME" stop && "$SCRIPTNAME" start
      ;;

      # Called to make sure script is in a runnable state.
      validate)
         exit 100
      ;;

      stoppable)
     [ "`vmmonUseCount`" -lt 1 ]
     exit
      ;;

      *)
         echo "Usage: "$BASENAME" {start|stop|status|restart|stoppable}"
         exit 1
   esac
}

SCRIPTNAME="$0"
BASENAME=`basename "$SCRIPTNAME"`

# Check permissions
if [ "`id -ur`" != '0' ]; then
   echo 'Error: you must be root.'
   echo
   exit 1
fi

vmwareService "$1"

exit 0I'm not really sure if these are the problem or not, but that error message above did point me toward these links:

[10.10  on startup - init: failed to spawn hostname, plymouth, hwclock,  mountall: permission denied]("http://www.reddit.com/r/Ubuntu/comments/eqwiz/1010_on_startup_init_failed_to_spawn_hostname/")
[http://www.reddit.com/r/Ubuntu/comments/eqwiz/1010_on_startup_init_failed_to_spawn_hostname/](http://www.reddit.com/r/Ubuntu/comments/eqwiz/1010_on_startup_init_failed_to_spawn_hostname/)

                                                      **bind or  devpts mounts in /etc/fstab stop the boot process    **

                       
[LIST=1]
[*]     [Ubuntu]("https://launchpad.net/ubuntu")
[*]     [“mountall”  package]("https://launchpad.net/ubuntu/+source/mountall")
[*]     [Bugs]("https://bugs.launchpad.net/ubuntu/+source/mountall")
[*]     Bug #524972
[/LIST]
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/524972](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/524972)

                                                      **LVM -  /var failed to mount during boot    **

                       
[LIST=1]
[*]     [Ubuntu]("https://launchpad.net/ubuntu")
[*]     [Lucid (10.04)]("https://launchpad.net/ubuntu/lucid")
[*]     [“mountall”  source package]("https://launchpad.net/ubuntu/lucid/+source/mountall")
[*]     [Bugs]("https://bugs.launchpad.net/ubuntu/lucid/+source/mountall")
[*]     Bug #561390
[/LIST]
[https://bugs.launchpad.net/ubuntu/lucid/+source/mountall/+bug/561390](https://bugs.launchpad.net/ubuntu/lucid/+source/mountall/+bug/561390)

**the device is busy-Ubuntu 10.10 not booting up on start up dev/sda1  no such directory**

               
[LIST=1]
[*]     [Ubuntu]("https://launchpad.net/ubuntu")
[*]     [“mountall”  package]("https://launchpad.net/ubuntu/+source/mountall")
[*]     [Questions]("https://answers.launchpad.net/ubuntu/+source/mountall")
[*]     Question #152826
[/LIST]
[https://answers.launchpad.net/ubuntu/+source/mountall/+question/152826](https://answers.launchpad.net/ubuntu/+source/mountall/+question/152826)

[SIZE=3][UbuntuBootupHowto]("https://help.ubuntu.com/community/UbuntuBootupHowto?action=fullsearch&context=180&value=linkto%3A%22UbuntuBootupHowto%22")[/SIZE]
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

> **Directories and Configs**

 
[LIST]
[*]**/etc/init**  is where the upstart init configs live. While they are not scripts  themselves, they essentially execute whatever is required to replace  sysvinit scripts.
[*]**/etc/init.d** is where all the  traditional sysvinit scripts and the backward compatible scripts for  upstart live. The backward compatible scripts basically run **service  myservice start** instead of doing anything themselves. Some  just show a notice to use the "service" command.
[*]**/etc/init/rc-sysinit.conf**  controls execution of traditional scripts added manually or with **update-rc.d**  to traditional runlevels in /etc/rc*
[*]**/etc/default** has configuration files  allowing you to control the behaviour of both traditional sysvinit  scripts and new upstart configs.
[/LIST]
 
**Using Services**

 Please note that generally, you  can use either traditional sysvinit scripts and the methods of working  with them as well as the new upstart configs and the command: "service"  interchangeably. It is however recommended you use the new upstart  methods which are both forward and backward compatible. 
[B]
Starting a Service[/B] 

# Traditional:
/etc/init.d/myservice start
# Upstart
service myservice start[B]

Stopping a Service[/B] 

# Traditional: 
/etc/init.d/myservice stop
# Upstart
service myservice stop[B]

Getting a list of Services[/B] 

# Traditional:
ls /etc/init.d
# Upstart: 
service --status-all
[LIST]
[*]**Note:**  Upstart method will show both traditional and upstart services.
[/LIST]
**Adding a Service to Default runlevels** 

# Traditional
update-rc.d apache2 defaults
[LIST]
[*]**Upstart**: there is no concept of  runlevels, everything is event driven with dependencies. You would add  an upstart config to **/etc/init** and potentially source a  config file in **/etc/default** to allow users to override  default behaviour.
[/LIST]
**Removing  a Service from Default runlevels** 

# Traditional - Something along the lines of
rm /etc/rc*/*myscript
[LIST]
[*]**Upstart**: If no config is available in  /etc/default, edit config in /etc/init
[/LIST]
 
**Other Upstart Commands**

 **Controlling Services -  interchangeable with the "service" command** 

[LIST]
[*]**initctl**  - can use in place of "service" with the commands bellow. Run initctl  help.
[*]**start** - start a service
[*]**stop**  - stop a service
[*]**reload** - sends a SIGHUP signal to  running process
[*]**restart** - restarts a service without  reloading its job config file
[*]**status** - requests status of service
[/LIST]
**Rebooting and Powering off the system** 

[LIST]
[*]**halt**  - shutdown the system then power off
[*]**poweroff** - shutdown the system then  power off
[*]**reboot** - reboot the system
[*]**shutdown**  - bring the system down
[/LIST]
**Misc  Upstart Commands** - you generally don't use these directly 

[LIST]
[*]**init**  - Upstart process management daemon
[*]**runlevel** - Backward compatibility with  traditional runlevels
[*]**telinit** - Backward compatibility with  traditional runlevels
[*]**upstart-udev-bridge** - Bridge between  upstart and udev
[/LIST]
  While this has been interesting research, I'm looking forward to having a bootable Ubuntu partition back, so I may just reinstall my modified Ubuntu 10.04.3 LTS.  I still suspect that my VMware virtual WinXP and/or the USB backpack driver colluded to somehow take over my Ubuntu boot process, so I will watch that more carefully in the future.

---

### Post by northd_tech on 2011-11-11
After installing a newer remix of an 'older' 10.04.3 LTS Ubuntu Lucid Lynx, I was able to access the external Backpack USB CDRW drive under a virtual Windows XP (using the Backpack PNP407__.exe Windows drivers) under VMware Player.

I still wasn't able to get any recognition of the USB CDRW drive under Ubuntu natively though.  

While this wasn't the 'proper Linux' solution- it was at least **workable** using 'virtual WinXP.'

I still might play with this hardware and Ubuntu a little, if for no reason other than to learn more about how external USB 'hotplugging' is implemented (esp. with 'external' firmware on EXTERNAL drives using **fxload** ).

---

