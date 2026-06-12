---
title: "Using Startech ECUSB3S2 USB 3.0 Expresscard on Ubuntu 10.04"
date: 2010-08-14
forum: Hardware
---

### Post by nkinar on 2010-08-14
Hello,

I recently purchased a Startech ECUSB3S2 USB 3.0 Expresscard adapter, and I would like to get it set up and running on Ubuntu 10.04 x86_64.  I believe that this card is based on the NEC chipset, and there should be kernel support for USB 3.0.

I followed the instructions posted here:

[https://help.ubuntu.com/community/ExpressCard](https://help.ubuntu.com/community/ExpressCard)

The instructions indicate that I need to modprobe pciehp or edit /etc/default/grub.  I've tried to modprobe pciehp, but nothing seems to show up in the kernel log after running dmesg.  Alternately, I've tried editing /etc/default/grub and then running sudo update-grub, but this seems to do nothing as well.

Here is the output of running the uname command:

nkinar@matilda:~$ uname -a
Linux matilda 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

I have Ubuntu 10.04 LTS installed on a Macbook Pro.

Where am I going wrong, and what can I do to use the ExpressCard as a USB 3.0 port?

---

### Post by nkinar on 2010-08-14
Moreover, checking in the /boot directory, it appears that the default kernel has been compiled with the proper options for PCI hotplug.  Here is the line from the default kernel config (config-2.6.32-24-generic):

```

CONFIG_HOTPLUG_PCI_PCIE=y

```

What can I do to check and see if the ExpressCard is working properly?

---

### Post by nkinar on 2010-08-14
Running the lspci command does indeed show that the USB controller is showing up on the bus; this appears to be the entry at the very end of the list:

```

nkinar@matilda:/proc$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 07)
06:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)

```

But why doesn't the controller appear to respond when I plug in a peripheral such as a USB 2.0 mouse?

---

### Post by nkinar on 2010-08-14
On second thought, perhaps this entry is another USB controller manufactured by NEC, such as a USB 2.0 controller.

I tried removing the ExpressCard, and found that the lspci command still shows the controller, so perhaps this is the USB 2.0 controller inside of the laptop.  :(

---

### Post by nkinar on 2010-08-14
So now I am certain that the USB 3.0 ExpressCard is showing up on the PCI bus.  Running lspci while the card is plugged in shows:

```

nkinar@matilda:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 07)
06:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)

```
However, the last line of the above output changes if the ExpressCard is unplugged:

```

nkinar@matilda:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 07)
06:00.0 USB Controller: NEC Corporation Device 0194 (rev ff)

```

So perhaps the problem is figuring out how to mount the USB controller bus on the ExpressCard?  How would I do this?

---

### Post by nkinar on 2010-08-14
Running the lspci -v command shows a little bit more information about the controller:

```

06:00.0 USB Controller: NEC Corporation Device 0194 (rev 03) (prog-if 30)
    Subsystem: NEC Corporation Device 0194
    Flags: fast devsel
    Memory at db100000 (64-bit, non-prefetchable) [disabled] [size=8K]
    Capabilities: <access denied>
    Kernel modules: xhci

```

---

### Post by nkinar on 2010-08-14
I updated the PCI IDs using the following command:

```

nkinar@matilda:~$ sudo update-pciids
Downloaded daily snapshot dated     2010-07-14 03:15:03

```

Now after running lspci -v it is more than apparent that the USB 3.0 controller is being detected:

```

06:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) (prog-if 30)
    Subsystem: NEC Corporation uPD720200 USB 3.0 Host Controller
    Flags: fast devsel
    Memory at db100000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel modules: xhci

```

---

### Post by nkinar on 2010-08-14
The USB 3.0 controller does not show up as a USB hub on the system:

```

nkinar@matilda:~$ lsusb
Bus 004 Device 009: ID 046d:c069 Logitech, Inc. 
Bus 004 Device 004: ID 05ac:8213 Apple, Inc. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 05ac:0236 Apple, Inc. 
Bus 003 Device 002: ID 05ac:8242 Apple, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 05ac:8507 Apple, Inc. 
Bus 001 Device 002: ID 059b:0379 Iomega Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by nkinar on 2010-08-14
Running lshw at the bash prompt returns the following about the USB 3.0 controller:

```

           *-usb UNCLAIMED
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:db100000-db101fff

```

Apparently this controller is marked as "unclaimed."  Is there a way to "claim" the controller, or is the driver missing?

---

### Post by nkinar on 2010-08-14
IMHO, it is unusual that the USB 3.0 hub is marked as "unclaimed" since there should be support for USB 3.0 already in the kernel.  

Since the kernel module is shown to be xhci, then it should be more than possible to be able to use this hardware.  I believe that the same NEC chip has been soldered to motherboards designed by Asus.

So why is the USB controller showing up as "unclaimed"?

---

### Post by nkinar on 2010-08-14
Compared to the Firewire controller also on the system, it appears that there is no kernel driver in use.  Notice that the firewire controller has a kernel driver that is listed as being "in-use."  The NEC controller does not have a driver in use:

```

05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 07) (prog-if 10)
    Subsystem: Agere Systems Device 5900
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at df200000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

06:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) (prog-if 30)
    Subsystem: NEC Corporation uPD720200 USB 3.0 Host Controller
    Flags: fast devsel
    Memory at db100000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel modules: xhci

```

I've tried to "modprobe xhci" but unfortunately the lsmod command shows that the driver is not in use:

```

nkinar@matilda:/lib/modules/2.6.32-24-generic/kernel/drivers/usb/host$ lsmod
Module                  Size  Used by
pci                     3829  0 
mtd                    20899  1 pci
chipreg                 2621  1 pci
xhci                   41214  0 
acpiphp                20317  0 
michael_mic             2164  4 
arc4                    1473  2 
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
binfmt_misc             7960  1 
rfcomm                 40393  4 
ppdev                   6375  0 
sco                     9617  2 
bridge                 53184  0 
stp                     2171  1 bridge
bnep                   11884  2 
l2cap                  34806  16 rfcomm,bnep
snd_hda_codec_realtek   279040  1 
lib80211_crypt_tkip     8676  0 
wl                   1964968  0 
hid_apple               5418  0 
iptable_nat             5219  0 
nf_nat                 19501  1 iptable_nat
nf_conntrack_ipv4      12980  3 iptable_nat,nf_nat
nf_conntrack           73966  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
iptable_mangle          3315  0 
iptable_filter          2791  0 
ip_tables              18390  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               22461  2 iptable_nat,ip_tables
fbcon                  39270  72 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
uvcvideo               62467  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
joydev                 11072  0 
applesmc               29217  0 
led_class               3764  1 applesmc
input_polldev           3106  1 applesmc
mbp_nvidia_bl           2335  0 
bcm5974                 7853  0 
btusb                  12969  2 
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
usbhid                 41084  0 
hid                    83440  2 hid_apple,usbhid
snd_hda_intel          25677  3 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71106  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211                6151  2 lib80211_crypt_tkip,wl
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
nvidia              10832442  40 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
i2c_nforce2             6099  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
usb_storage            49833  1 
ohci1394               30260  0 
ieee1394               94771  1 ohci1394
ahci                   37870  2 
forcedeth              55592  0 


```

---

### Post by nkinar on 2010-08-15
Okay, now I think that I know what the issue is, but at this time I do not understand how to fix it. ;)

Running dmesg, it appears that the USB 3.0 controller is being detected, but an interrupt cannot be set:

```

nkinar@matilda:~$ dmesg | grep xhci
[   15.298454] xhci_hcd 0000:06:00.0: PCI INT A -> GSI 0 (level, low) -> IRQ 0
[   15.298457] xhci_hcd 0000:06:00.0: Found HC with no IRQ.  Check BIOS/PCI 0000:06:00.0 setup!
[   15.298607] xhci_hcd 0000:06:00.0: PCI INT A disabled
[   15.298609] xhci_hcd 0000:06:00.0: init 0000:06:00.0 fail, -19

```

So what could possibly cause this behavior, and what can I do to fix it?

---

### Post by nkinar on 2010-08-15
I feel that this has something to do with the EFI bus on a Macbook Pro.  Since these computers do not have a BIOS, is there a way that I can get rid of these errors?

---

### Post by nkinar on 2010-08-15
After a little bit of experimentation, I found that there are two things that can be done; however, these solutions are non-optimal.  Note that I am running Ubuntu 10.04 LTS on a Macbook Pro (hardware revision 5,1).

(1) Edit the parameters passed into the kernel to turn off acpi:

```

pciehp.pciehp_force=1 acpi=off acpi_osi=Darwin

```The USB 3.0 Expresscard bus can now be detected by Ubuntu, but ACPI is off :(

(2) Edit the parameters so that ACPI does not map the IRQs:

```

pciehp.pciehp_force=1 acpi=noirq acpi_osi=Darwin

```However, this makes the cursor on the GNOME desktop freeze, particularly when an interrupt occurs.  Note that if only acpi_osi=Darwin is passed in, there will be a problem with a "GPE Storm" that is detected, and the kernel will hang.

Since none of these solutions are optimal, I think that the best way to proceed would be to simply not use the ExpressCard.  This is a shame, but I think that it should be possible to use the ExpressCard technology on systems without EFI.

---

### Post by nkinar on 2011-01-30
Shortly after making my last post, I returned the USB 3.0 ExpressCard to my local computer store.  Since I have a Macbook Pro (mid-2009 model), and I am running Ubuntu, I believe that many problems may have occurred due to the Apple hardware.

This problem may have been fixed in the Linux kernel by now, and your mileage may vary if you try the same ExpressCard on another type of laptop.  However, I do not have the ExpressCard, and consequently I cannot test this hardware.

---

### Post by scotty64 on 2011-03-17
I just got the same card and tried it on Ubuntu 10.04 (32bit). Works perfectly here. I know from my firewire express card that the express slot hotplugging does not work properly, so I plug the card into the Dell laptop before booting it up.
The only limitation I came across is that the powersupply of the adapter is not strong enough to power my external USB3.0 Iomega eGo harddisk. I have to use the second plug on the drives cable to supply power from one of the USB2.0 slots.

---

### Post by jsgarvin on 2011-05-14
I have the same card and am also using 10.04

The card was instantly recognized on first boot with it and I could use it as USB 2.0 ports, however, I'm not able to get it to work as USB 3.0.

I have two [NexStar CX USB 3.0 Drive Enclosures]("http://www.amazon.com/gp/product/B004TPCFXM/ref=as_li_ss_tl?ie=UTF8&tag=skydivergearc-20&linkCode=as2&camp=217145&creative=399349&creativeASIN=B004TPCFXM") each with 2TB WD Drives, and am using the USB 3.0 cables that came with the enclosures, plugged into the startech ExpressCard. However, System/Administration/Disk Utility reports the "Connection" for both drives to be "USB at 480.0 MB/s", which is USB 2.0.  Transferring big chunks of files to and from the drives runs at the same speed as when using the built-in USB 2.0 ports.

Anybody got any ideas?  Thanks.

---

### Post by locutus42 on 2011-06-18
incase anyone find this and is having expresscard hotplug issues, what worked for me was enabling acpi hot plug support with:

sudo modprobe acpiphp

I knew the kernel had pci Express hot plug enabled looking at dmesg output:

[    0.274741] pciehp: PCI Express Hot Plug Controller Driver version: 0.4

---

### Post by dda on 2011-10-17
> **locutus42 said:**
> incase anyone find this and is having expresscard hotplug issues, what worked for me was enabling acpi hot plug support with:

sudo modprobe acpiphp

I knew the kernel had pci Express hot plug enabled looking at dmesg output:

[    0.274741] pciehp: PCI Express Hot Plug Controller Driver version: 0.4

Thank you! That solves the problem completely. 

**nkinar**, thank you for starting that thread. I'm sure that that solution would work for you, too. Can you mark the thread as SOLVED?

---

