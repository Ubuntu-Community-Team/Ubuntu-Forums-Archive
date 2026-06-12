---
title: "Marvell 88SE6121 eSATA not recognized (Asus M4A79XTD EVO MOBO)"
date: 2009-12-08
forum: Hardware
---

### Post by Zavior on 2009-12-08
I have just installed Ubuntu 9.10 on a new Asus M4A79XTD EVO motherboard. All other hardware seems to be running fine, all my internal drives are recognized (though these are on the AMD SB750). I have had difficulties with eSATA and ubuntu in the past with other motherboards. When diagnosing problems I use dmesg. This time however when I turn on my eSATA drive I don't get any kind of new output with dmesg. Has anyone gotten eSATA on a Marvell 88SE6121 working? If so how? If you can't help me specifically, is there another command I need to use to try and monitor what is going on when I turn on my drive. I get the feeling that nothing at all is happening when I turn on my drive... I used hwinfo to try and find out if Ubuntu is even seeing my controller and it is indeed. Here is the relevant section:

```
40: PCI 400.0: 0101 IDE interface
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_11ab_6121
  Unique ID: YmUS.f481h2xHnF9
  Parent ID: WL76.T8BQG7pYTS8
  SysFS ID: /devices/pci0000:00/0000:00:09.0/0000:04:00.0
  SysFS BusID: 0000:04:00.0
  Hardware Class: storage
  Model: "Marvell 88SE6121 SATA II Controller"
  Vendor: pci 0x11ab "Marvell Technology Group Ltd."
  Device: pci 0x6121 "88SE6121 SATA II Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x822f 
  Revision: 0xb2
  Driver: "pata_marvell"
  I/O Ports: 0xec00-0xec07 (rw)
  I/O Ports: 0xe880-0xe883 (rw)
  I/O Ports: 0xe800-0xe807 (rw)
  I/O Ports: 0xe480-0xe483 (rw)
  I/O Ports: 0xe400-0xe40f (rw)
  Memory Range: 0xf7fffc00-0xf7ffffff (rw,non-prefetchable)
  IRQ: 17 (7631 events)
  Module Alias: "pci:v000011ABd00006121sv00001043sd0000822Fbc01sc01i8f"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (PCI bridge)
```

I have enabled AHCI in my bios. If you need any other information please let me know. Thanks in advance for any help you can offer!

---

### Post by spydeyrch on 2009-12-08
I have had the same type of issue. Except my mobo is the Asus M3A79-T Deluxe. I don't remember the chipset for the eSata though. It is very similar to the one mentioned in the original problem. It is off by just a few numbers (88SE6xxx). I have had this issue since 8.04 and in every consecutive release. Any body have any suggestions?  Thanks!
 
-Spydey  :confused:

---

### Post by Zavior on 2009-12-08
UPDATE: I found this: [link]("https://bugzilla.redhat.com/show_bug.cgi?id=455833"). I tried blacklisting ahci but that did not help. I tried disabling AHCI in my BIOS. This did not help either. I did find that Ubuntu recognizes my external HDD if I have it on during boot. So it seems the issue is that the pata_marvell driver does not support hot swapping. Can I use the ahci kernel module instead of pata_marvell? If so how do I force Ubuntu to do this? If not is there another driver/kernel module (I'm not sure which would be the proper term) I could use to enable hotswapping. Again thanks in advance for any help.

---

### Post by crazy_bob_uk on 2009-12-14
I too have been having problems with a Marvell Sata controller on 9.10.  I have found many places reccomending adding ahci.marvell_enable=1 to the boot options, which kinda works but doesnt seam to work right with my mdadm raid array.
The next thing I'm gonna try is to install the mvsata driver ([http://www.keffective.com/mvsata/FC3/](http://www.keffective.com/mvsata/FC3/)), though I need to do some more reading first to find out how to do this (I've only been using linux about a month).

---

