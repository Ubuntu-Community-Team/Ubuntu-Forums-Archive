---
title: "Hal Running Wild with CD/DVD drive"
date: 2009-01-20
forum: Hardware
---

### Post by fwallace99 on 2009-01-20
Hello all, maybe someone can help me with my ongoing problems with My System. HAL is running wild, taking up WAY too much CPU (easily 60%).

My system:

uname -a
Linux Prytania 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686 GNU/Linux

[Hardy Heron 8.04]

2 GB RAM, Toshiba Satellite A135-S2276.

I WAS able to play commercial DVDs on this, with 7.04 Feisty. Now the DVDs play slow, like junk, many motion artifacts. CD/DVD drive becomes unuseable and K3B refuses to start, or hangs for a long time, says drive is unavailable, I get a lot of messages in dmesg about well, stuff like this:

 ide: failed opcode was: unknown
[  824.223338] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
[  824.223342] end_request: I/O error, dev hdc, sector 128404
[  824.227531] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[  824.227539] hdc: command error: error=0x50 { LastFailedSense=0x05 }
[  824.227542] ide: failed opcode was: unknown


I get the usual messages from dbus complaining about not mounting the audio disc (this is when the computer's CD/DVD drive is empty).

The computer slows down to a crawl, randomly, top reveals that hal-addon-storage daemon is taking up lots of CPU time, around 60% or more.

Killing that daemon certainly makes my computer run a LOT faster. But I still can't play DVDs, at all, even with manual mounting. Leaving the daemon running leaves me with a very sloooowwww DVD drive, when under FEISTY it ran like a top (video playback was GREAT, better than a DVD player).

Here's my hardware info:

```
floyd@Prytania:~$ sudo lshw -short
[sudo] password for floyd: 
H/W path           Device     Class       Description
=====================================================
                              system      Satellite A135
/0                            bus         IAYAA
/0/0                          memory      108KiB BIOS
/0/4                          processor   Genuine Intel(R) CPU           T2060  
/0/4/5                        memory      16KiB L1 cache
/0/4/6                        memory      1MiB L2 cache
/0/4/0.1                      processor   Logical CPU
/0/4/0.2                      processor   Logical CPU
/0/12                         memory      2GiB System Memory
/0/12/0                       memory      1GiB DIMM DRAM Synchronous
/0/12/1                       memory      1GiB DIMM DRAM Synchronous
/0/1                          processor   
/0/1/0.1                      processor   Logical CPU
/0/1/0.2                      processor   Logical CPU
/0/100                        bridge      ATI Technologies Inc
/0/100/1                      bridge      RS480 PCI Bridge
/0/100/1/5                    display     RC410 [Radeon Xpress 200M]
/0/100/6                      bridge      RS480 PCI Bridge
/0/100/6/0         wifi0      network     AR242x 802.11abg Wireless PCI Express 
/0/100/12          scsi0      storage     IXP SB400 Serial ATA Controller
/0/100/12/0.0.0    /dev/sda   disk        80GB TOSHIBA MK8037GS
/0/100/12/0.0.0/1  /dev/sda1  volume      2047MiB Linux swap volume
/0/100/12/0.0.0/2  /dev/sda2  volume      72GiB EXT3 volume
/0/100/13                     bus         IXP SB400 USB Host Controller
/0/100/13.1                   bus         IXP SB400 USB Host Controller
/0/100/13.2                   bus         IXP SB400 USB2 Host Controller
/0/100/14                     bus         IXP SB400 SMBus Controller
/0/100/14.1                   storage     IXP SB400 IDE Controller
/0/100/14.1/1      ide1       bus         IDE Channel 1
/0/100/14.1/1/0    /dev/hdc   disk        MATSHITADVD-RAM UJ-850S
/0/100/14.2                   multimedia  IXP SB4x0 High Definition Audio Contro
/0/100/14.3                   bridge      IXP SB400 PCI-ISA Bridge
/0/100/14.4                   bridge      IXP SB400 PCI-PCI Bridge
/0/100/14.4/4                 bridge      CB1410 Cardbus Controller
/0/100/14.4/6      eth0       network     RTL-8139/8139C/8139C+
/1                            power       TOSHIBA

```


What's going on?

Obviously HAL is running wild. Ubuntu team has said basically, go use kernel 2.6.27 (which I don't know how to do anyway, and I don't want to compile a kernel -- a three day affair min to compile, test, fix, test, fix, compile more, test again, maybe more, just to play DVDs).

ANY solutions would be most appreciated.

I'm looking to both tame HAL, so it does not go wild, and play DVDs at the speed FEISTY played them (i.e. without the annoying motion artifacts all the time).

---

