---
title: "MiTAC - PD10EHI - booting takes too long and I can find some problems in kern.log"
date: 2024-01-08
forum: Hardware
---

### Post by kaschulze on 2024-01-08
Hi guys, 
I installed 
Ubuntu Server 22.04.3 LTS.  

It seems that all things are working fine. But I found some problems in the kern.log.
Hardware:
```
 
Motherboard:
  Product: PD10EHI
  Vendor: MiTAC
Memory:  
  2x SODIMM DDR4 Synchronous 3200 MHz (0,3 ns)
CPU:
  Intel(R) Pentium(R) N6415 @ 1.20GHz
SATA (M.2 2280):
   Product: WDC  WDS500G1R0B (465 GiB)
     /dev/sda1 &#8594; /boot/efi
     /dev/sda2 &#8594; /boot
     /dev/sda3 &#8594; /usr
     /dev/sda4 &#8594; /var
     /dev/sda5 &#8594; /root
     /dev/sda6 &#8594; /
     /dev/sda7 &#8594; /res
 SATA controller:  88SE9215 PCIe 2.0 x1 4-port SATA 6 Gb/s Controller
   Product: SAMSUNG HD753LJ (698 GiB) (this hard disk will be replaced later on. This was installed to check the functionality of 4-port SATA controller)
     /dev/sdb1
     /dev/sdb2
 
 
```


 The kernel is waiting for something and it seems a timeout is reached here (2 minutes).  

 Jan  8 01:38:08 homeserver2 kernel: [    3.653444] i915 0000:00:02.0: [drm] fb0: i915drmfb frame buffer device
 Jan  8 01:38:08 homeserver2 kernel: [  122.605112] raid6: sse2x4   gen() 11612 MB/s

Can I prevent this? Should I adjust the BIOS? What is missing here?

 Later on you can see the kernel seems to wait for another thing (1 minute):
 Jan  8 01:38:08 homeserver2 kernel: [  123.150417] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null). Quota mode: none.
 Jan  8 01:38:08 homeserver2 kernel: [  183.281636] pstore: Using crash dump compression: deflate
 
 Finally it is waiting a third time (&#8220;only&#8221; 14 seconds): 
Jan  8 01:38:08 homeserver2 kernel: [  186.702754] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
 Jan  8 01:38:08 homeserver2 kernel: [  200.586508] kauditd_printk_skb: 22 callbacks suppressed
 
 kern.log
```


Jan  8 01:38:08  &#8230;.
 Jan  8 01:38:08 homeserver2 kernel: [    3.521999] [drm] Initialized i915 1.6.0 20201103 for 0000:00:02.0 on minor 0
 Jan  8 01:38:08 homeserver2 kernel: [    3.522923] ACPI: video: [Firmware Bug]: ACPI(GFX0) defines _DOD but not _DOS
 Jan  8 01:38:08 homeserver2 kernel: [    3.524049] ACPI: video: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
 Jan  8 01:38:08 homeserver2 kernel: [    3.524505] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
 Jan  8 01:38:08 homeserver2 kernel: [    3.569501] input: Logitech USB Keyboard System Control as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.1/0003:046D:C31C.0002/input/input5
 Jan  8 01:38:08 homeserver2 kernel: [    3.569709] hid-generic 0003:046D:C31C.0002: input,hidraw1: USB HID v1.10 Device [Logitech USB Keyboard] on usb-0000:00:14.0-7/input1
 Jan  8 01:38:08 homeserver2 kernel: [    3.587617] fbcon: i915drmfb (fb0) is primary device
 Jan  8 01:38:08 homeserver2 kernel: [    3.612638] Console: switching to colour frame buffer device 160x45
 Jan  8 01:38:08 homeserver2 kernel: [    3.653444] i915 0000:00:02.0: [drm] fb0: i915drmfb frame buffer device
 Jan  8 01:38:08 homeserver2 kernel: [  122.605112] raid6: sse2x4   gen() 11612 MB/s
 Jan  8 01:38:08 homeserver2 kernel: [  122.673113] raid6: sse2x4   xor()  7271 MB/s
 Jan  8 01:38:08 homeserver2 kernel: [  122.741112] raid6: sse2x2   gen() 14389 MB/s
 Jan  8 01:38:08 homeserver2 kernel: [  122.809112] raid6: sse2x2   xor()  8080 MB/s
 Jan  8 01:38:08 homeserver2 kernel: [  122.877113] raid6: sse2x1   gen() 12779 MB/s
 Jan  8 01:38:08 homeserver2 kernel: [  122.945112] raid6: sse2x1   xor()  7732 MB/s
 Jan  8 01:38:08 homeserver2 kernel: [  122.945126] raid6: using algorithm sse2x2 gen() 14389 MB/s
 Jan  8 01:38:08 homeserver2 kernel: [  122.945142] raid6: .... xor() 8080 MB/s, rmw enabled
 Jan  8 01:38:08 homeserver2 kernel: [  122.945177] raid6: using ssse3x2 recovery algorithm
 Jan  8 01:38:08 homeserver2 kernel: [  122.946491] xor: measuring software checksum speed
 Jan  8 01:38:08 homeserver2 kernel: [  122.946962]    prefetch64-sse  : 21867 MB/sec
 Jan  8 01:38:08 homeserver2 kernel: [  122.947478]    generic_sse     : 19651 MB/sec
 Jan  8 01:38:08 homeserver2 kernel: [  122.947492] xor: using function: prefetch64-sse (21867 MB/sec)
 Jan  8 01:38:08 homeserver2 kernel: [  122.948576] async_tx: api initialized (async)
 Jan  8 01:38:08 homeserver2 kernel: [  123.014064] Btrfs loaded, crc32c=crc32c-intel, zoned=yes, fsverity=yes
 Jan  8 01:38:08 homeserver2 kernel: [  123.127076] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null). Quota mode: none.
 Jan  8 01:38:08 homeserver2 kernel: [  123.150417] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null). Quota mode: none.
 Jan  8 01:38:08 homeserver2 kernel: [  183.281636] pstore: Using crash dump compression: deflate
 Jan  8 01:38:08 homeserver2 kernel: [  183.284252] pstore: Registered efi as persistent store backend
 Jan  8 01:38:08 homeserver2 kernel: [  183.306382] EXT4-fs (sda6): re-mounted. Opts: (null). Quota mode: none.
 Jan  8 01:38:08 homeserver2 kernel: [  183.306853] EXT4-fs (sda3): re-mounted. Opts: (null). Quota mode: none.
 Jan  8 01:38:08 homeserver2 kernel: [  183.371444] Adding 8388604k swap on /swap.img.  Priority:-2 extents:29 across:201310340k SSFS
 Jan  8 01:38:08 homeserver2 kernel: [  183.384876] alua: device handler registered
 Jan  8 01:38:08 homeserver2 kernel: [  183.386259] emc: device handler registered
 Jan  8 01:38:08 homeserver2 kernel: [  183.390385] rdac: device handler registered
 Jan  8 01:38:08 homeserver2 kernel: [  183.738133] mei_me 0000:00:16.0: enabling device (0000 -> 0002)
 Jan  8 01:38:08 homeserver2 kernel: [  183.782024] ee1004 0-0050: 512 byte EE1004-compliant SPD EEPROM, read-only
 Jan  8 01:38:08 homeserver2 kernel: [  184.056036] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null). Quota mode: none.
 Jan  8 01:38:08 homeserver2 kernel: [  184.062583] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null). Quota mode: none.
 Jan  8 01:38:08 homeserver2 kernel: [  184.069365] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null). Quota mode: none.
 Jan  8 01:38:08 homeserver2 kernel: [  184.109917] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null). Quota mode: none.
 Jan  8 01:38:08 homeserver2 kernel: [  184.111665] loop0: detected capacity change from 0 to 129944
 Jan  8 01:38:08 homeserver2 kernel: [  184.116044] loop1: detected capacity change from 0 to 130888
 Jan  8 01:38:08 homeserver2 kernel: [  184.116525] loop2: detected capacity change from 0 to 229272
 Jan  8 01:38:08 homeserver2 kernel: [  184.120201] loop3: detected capacity change from 0 to 83672
 Jan  8 01:38:08 homeserver2 kernel: [  184.123021] loop4: detected capacity change from 0 to 82800
 Jan  8 01:38:08 homeserver2 kernel: [  184.155173] mei_hdcp 0000:00:16.0-b638ab7e-94e2-4ea2-a552-d1c54b627f04: bound 0000:00:02.0 (ops i915_hdcp_component_ops [i915])
 Jan  8 01:38:08 homeserver2 kernel: [  184.166786] intel_rapl_common: Found RAPL domain package
 Jan  8 01:38:08 homeserver2 kernel: [  184.166790] intel_rapl_common: Found RAPL domain core
 Jan  8 01:38:08 homeserver2 kernel: [  184.166791] intel_rapl_common: Found RAPL domain uncore
 Jan  8 01:38:08 homeserver2 kernel: [  184.264208] audit: type=1400 audit(1704674271.959:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lsb_release" pid=774 comm="apparmor_parser"
 Jan  8 01:38:08 homeserver2 kernel: [  184.268791] audit: type=1400 audit(1704674271.963:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe" pid=775 comm="apparmor_parser"
 Jan  8 01:38:08 homeserver2 kernel: [  184.268797] audit: type=1400 audit(1704674271.963:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe//kmod" pid=775 comm="apparmor_parser"
 Jan  8 01:38:08 homeserver2 kernel: [  184.271117] audit: type=1400 audit(1704674271.967:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=777 comm="apparmor_parser"
 Jan  8 01:38:08 homeserver2 kernel: [  184.271123] audit: type=1400 audit(1704674271.967:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=777 comm="apparmor_parser"
 Jan  8 01:38:08 homeserver2 kernel: [  184.271126] audit: type=1400 audit(1704674271.967:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=777 comm="apparmor_parser"
 Jan  8 01:38:08 homeserver2 kernel: [  184.276299] audit: type=1400 audit(1704674271.971:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="tcpdump" pid=783 comm="apparmor_parser"
 Jan  8 01:38:08 homeserver2 kernel: [  184.281140] audit: type=1400 audit(1704674271.975:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=786 comm="apparmor_parser"
 Jan  8 01:38:08 homeserver2 kernel: [  184.282878] audit: type=1400 audit(1704674271.979:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=784 comm="apparmor_parser"
 Jan  8 01:38:08 homeserver2 kernel: [  184.282883] audit: type=1400 audit(1704674271.979:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=784 comm="apparmor_parser"
 Jan  8 01:38:08 homeserver2 kernel: [  186.702046] igb 0000:02:00.0 enp2s0: igb: enp2s0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
 Jan  8 01:38:08 homeserver2 kernel: [  186.702046] igb 0000:01:00.0 enp1s0: igb: enp1s0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
 Jan  8 01:38:08 homeserver2 kernel: [  186.702457] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready
 Jan  8 01:38:08 homeserver2 kernel: [  186.702754] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
 Jan  8 01:38:08 homeserver2 kernel: [  200.586508] kauditd_printk_skb: 22 callbacks suppressed
 Jan  8 01:38:08 homeserver2 kernel: [  200.586512] audit: type=1400 audit(1704674288.283:34): apparmor="DENIED" operation="open" profile="/usr/sbin/ntpd" name="/snap/bin/" pid=864 comm="ntpd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
 Jan  8 01:38:11 homeserver2 kernel: [  203.386226] loop5: detected capacity change from 0 to 8
 Jan  8 01:51:06 homeserver2 kernel: [  978.859483]  sdb: sdb1 sdb2
  
 
```

Last but not least: When I shut down the system the /var filesystem cannot be unmounted (it seems so).

Link to pastebin: [https://paste.ubuntu.com/p/XPmDr5d4s7/](https://paste.ubuntu.com/p/XPmDr5d4s7/)

```

~$ sudo systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @21.173s
&#9492;&#9472;multi-user.target @21.171s
  &#9492;&#9472;snapd.seeded.service @20.604s +92ms
    &#9492;&#9472;snapd.service @17.760s +2.839s
      &#9492;&#9472;basic.target @17.685s
        &#9492;&#9472;sockets.target @17.682s
          &#9492;&#9472;snapd.socket @17.665s +13ms
            &#9492;&#9472;sysinit.target @17.606s
              &#9492;&#9472;cloud-init.service @17.084s +514ms
                &#9492;&#9472;systemd-networkd-wait-online.service @2.167s +14.905s
                  &#9492;&#9472;systemd-networkd.service @2.100s +62ms
                    &#9492;&#9472;network-pre.target @2.097s
                      &#9492;&#9472;cloud-init-local.service @1.562s +533ms
                        &#9492;&#9472;var.mount @1.226s +23ms
                          &#9492;&#9472;systemd-fsck@dev-disk-by\x2duuid-b1b6bcf1\x2d2af5\x2d4703\x2d8900\x2debaca3905912.service @1.119s +71ms
                            &#9492;&#9472;dev-disk-by\x2duuid-b1b6bcf1\x2d2af5\x2d4703\x2d8900\x2debaca3905912.device @1.106s


```

 Any support for this problem is appreciated.
 Thanks

---

### Post by kaschulze on 2024-01-11
Unfortunately I bought a "new" board with an old BIOS (version D8230A05).

I contacted the seller who hasn't had experience in Linux and told me this board was not released for Linux.
MiTAC told me I have to update the BIOS to version D8230A06 which will fix the Linux boot issues.

Finally I updated the BIOS and now Ubuntu Server boots quickly without no "waiting for something" issues.

Here the steps to flash the Bios from D8230A05 to D8230A06:
- Install Windows 10 on a harddisk (remove the disk with Linux first)
- download the latest version from vendors's page
- If you see the message "The ROM file information does not match the system BIOS!" select the "E" option. This option will update entire BIOS region and exit.
After a few minutes, you will have the latest BIOS installed on your board
- destroy Windows 10 ;-)

---

