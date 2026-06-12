---
title: "dmesg output -- whattya make of it?"
date: 2011-05-27
forum: Hardware
---

### Post by daniel.cotter on 2011-05-27
[57064.058131] DMA: Out of SW-IOMMU space for 69 bytes at device 0000:06:00.0


when I type ```
dmesg
```

this is the output I get, repeated about a million times, with the only change from line to line being the (address?) between the brackets.

If you know what this means, what do I do to fix it?

---

### Post by DanneStrat on 2011-05-27
Some device is causing those messages to appear in the logs.

If you look at the output you posted:

[57064.058131] DMA: Out of SW-IOMMU space for 69 bytes at device 0000:06:00.0

This is the important part:

"0000:06:00.0"

This is the device ID for the device that causes the messages

so let's find out more about it.

Open terminal and do:

```
cat /var/log/kern.log
```

This will show you the kernel log.

Post the output.

Try to post at least part of the log(it may be quite long).

---

### Post by daniel.cotter on 2011-05-27
DanneStrat,

I am in the process of pasting together the output, with each of the errors it contains (it is nearly 12 million lines long, so I am sampling from each error).  It's gonna take some time, but I will paste it in tomorrow.

Thanks,

---

### Post by Toz on 2011-05-28
**lspci** will show all of the pci codes. Is it your network card?

---

### Post by DanneStrat on 2011-05-28
> **daniel.cotter said:**
> DanneStrat,

I am in the process of pasting together the output, with each of the errors it contains (it is nearly 12 million lines long, so I am sampling from each error).  It's gonna take some time, but I will paste it in tomorrow.

Thanks,

Hi again.

You don't need to post every one of them.

(only one of those messages with the ID 0000:06:00.0

would be necessary to determine the device)

```
lspci
```

would also give the info we need  as Toz said.

---

### Post by daniel.cotter on 2011-05-28
lspci:

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
02:00.1 Audio device: ATI Technologies Inc RV710/730
06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
07:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
07:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
07:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
```0000:06:00.0

Does this match up to the Network adapter?  I have a laptop, with everything integrated.

I have noticed some lag in download  speeds.


I tried to edit the kern.log output to make the size manageable, but that thing is a monster, and took a lot of my time.  If the problem can be determined by reading the lspci, that suits me fine.

---

### Post by DanneStrat on 2011-05-28
Thanks for the output.

Then we know that this is the culprit:

"06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)"

We need to find out which driver is being used.

Post output from:

```
sudo lshw -c Network
```

and

```
lsmod
```

---

### Post by daniel.cotter on 2011-05-28
```
daniel@daniel-Pangolin:~$ sudo lshw -c Network
[sudo] password for daniel: 
  *-network DISABLED      
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 10
       serial: 48:5d:60:6e:61:06
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 latency=0 link=no multicast=yes wireless=802.11bg
       resources: irq:18 ioport:4000(size=256) memory:f0300000-f0303fff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:07:00.5
       logical name: eth0
       version: 03
       serial: 00:90:f5:ac:75:75
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.7 duplex=full ip=192.168.0.8 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 memory:f0400000-f0403fff ioport:5400(size=128) ioport:5000(size=256)
daniel@daniel-Pangolin:~$ 
```I am using JMicron's proprietary driver.  (I disable wireless most of the time)
 I remember adding the proprietary driver at one time, but I can't find that screen again.

```
daniel@daniel-Pangolin:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40283  1 
ipt_MASQUERADE         12759  0 
xt_state               12578  0 
ipt_REJECT             12576  0 
xt_tcpudp              12603  0 
iptable_filter         12810  0 
nf_nat_h323            17002  0 
nf_conntrack_h323      58565  1 nf_nat_h323
nf_nat_pptp            12629  0 
nf_conntrack_pptp      13839  1 nf_nat_pptp
nf_conntrack_proto_gre    13606  1 nf_conntrack_pptp
nf_nat_proto_gre       12767  1 nf_nat_pptp
nf_nat_tftp            12489  0 
nf_conntrack_tftp      12953  1 nf_nat_tftp
nf_nat_sip             17087  0 
nf_conntrack_sip       29609  1 nf_nat_sip
nf_nat_irc             12643  0 
nf_conntrack_irc       13383  1 nf_nat_irc
nf_nat_ftp             12649  0 
nf_conntrack_ftp       13359  1 nf_nat_ftp
iptable_nat            13182  0 
nf_nat                 25736  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19640  3 iptable_nat,nf_nat
nf_conntrack           81956  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
ip_tables              27456  2 iptable_filter,iptable_nat
x_tables               29581  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
joydev                 17606  0 
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_si3054    13084  1 
snd_hda_codec_realtek   336693  1 
snd_hda_intel          33211  4 
snd_hda_codec         103804  4 snd_hda_codec_hdmi,snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  4 snd_hda_codec_hdmi,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
fglrx                2739144  575 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
r8192se_pci           524220  0 
snd                    67382  19 snd_hda_codec_hdmi,snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178528  1 r8192se_pci
jmb38x_ms              17596  0 
psmouse                73535  0 
soundcore              12680  1 snd
memstick               16520  1 jmb38x_ms
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13166  0 
video                  19438  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
ahci                   25951  3 
jme                    40728  0 
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
libahci                26642  1 ahci
daniel@daniel-Pangolin:~$
```

Well, what do you think?

---

### Post by DanneStrat on 2011-05-28
> Well, what do you think?

It seems to be some sort of communications problem with the

driver and the network card.

I think your best bet is to file a bug report for the "rtl819xSE" driver

over at launchpad.

First register an account here(upper right corner):

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

Then file a bug report here:

[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

(also upper right)

Good luck!

---

### Post by IcarusR on 2011-05-29
Before you post a bug report.

It is your wireless card (RTL8191SEvB Wireless LAN Controller) causing the error 

> device 0000:06:00.0

> 06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)


This has nothing to do with 

> I am using JMicron's proprietary driver.

This is driver for your Ethernet card

> 07:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)

You need to enable the wireless card then reboot & check your log files again to see if you still get the errors.

---

