---
title: "usb devices change between reboots"
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by incused on 2006-11-26
I am having a strange problem with USB. I have two external harddrives that are listed in my fstab to mount on bootup. It seems that everytime I reboot the machine, the two drives will swap devices. The one which was sdb1 becomes sdc1 and vice versa. 

Here is the offending portion of my fstab:
```

/dev/sdc1       /rsync          ext3    defaults,errors=remount-ro 0       1
/dev/sdb1       /rsync_bkup          ext3    defaults,errors=remount-ro 0      1

```

I'm not sure if it makes a difference, but one drive is a maxtor and the other a seagate. Both are 300GB in size. 

Here is what lspci outputs:
```

00:00.0 Host bridge: Intel Corporation Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation Unknown device 104c (rev 02)
00:1a.0 USB Controller: Intel Corporation USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation SATA Controller RAID (rev 02)
00:1f.3 SMBus: Intel Corporation SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d1 (rev a1)
03:03.0 Communication controller: Conexant HSF 56k Data/Fax Modem

```

Any clues? I recently tried out Fedora Core 6 for a few weeks before coming back to Ubuntu Edgy, during my time in Fedora this problem did not exist.

I have looked for others with my same problem and have so far not had any luck. 

Please, any help ? 

Regards,
-- 
Todd

---

### Post by incused on 2006-12-26
Still no update? 

This is still happening :(

---

