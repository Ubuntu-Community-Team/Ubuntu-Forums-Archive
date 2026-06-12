---
title: "Hibernate on Asus W6F  with Feisty upgrade"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by insitu on 2007-05-04
Hello,
I have an Asus W6F laptop. I just upgraded from Dapper to Edgy then to Feisty. In the process, I managed to solve my sound problem which is fine, but I lost suspend-to-disk. I installed the uswsusp package manually, edited the config file manually (dpkg-reconfigure did not work), added resume=/dev/sda5 in my kernel options, but I still does not work: I can go to sleep, but at boot time ubuntu does not read back the image from /dev/sda5. 

I have attached my kernel's boot mesg (dmesg outputt, which BTW seems to show that my dual core is not recognized...)

Here is my lspci output:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:03.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
08:03.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:03.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
08:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
08:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


Help greatly appreciated as this is a major stopper for me.

Regards,
Arnaud

---

### Post by insitu on 2007-05-06
I managed to solve my problem using a rather radical solution: I re-installed Feisty from boot CD. Now, everything is working fine with some comment:
 - X configuration was not detected properly (too low resolution, scrolling with touchpad disabled...). I just copied my old configuration and it's ok
 - sound did not work. I followed instructions on [http://doc.ubuntu-fr.org/materiel/portable/inspiron_9400](http://doc.ubuntu-fr.org/materiel/portable/inspiron_9400) (in french) for recompiling alsa-drivers and libs and it worked perfectly
 - network is ok out of the box (ipw3945)
 - acpi is perfect: I have not only suspend-to-disk but also suspend-to-ram that used not to work
 - 3D effects are cool ! We can now make those MacOS weenies cry... :-)
 - java-package is still lagging behind sun's jvm: java 6 is missing in the configs and I don't really know how to add it properly. 

I was about to throw away Ubuntu, but I kept faith and was rewarded. Thanks everybody who happens to read these lines and contribute to ubuntu for such a great work.

Regards,

Insitu

---

### Post by insitu on 2007-05-07
Hello,
I spoke too quickly. I am still experiencing problems with hibernate/sleep on Feisty with my laptop. Symptoms:
 - wifi no more works on upon resume from sleep to disk and sometimes does not work at boot time. It MAY restart upon switch off/switch on of wifi button (this is a button on asus w6f that turns on/off wifi and bluetooth
 - could not always resume from suspend to ram: screen is blank but system seems up and running (pings work but no port is open according to nmap)

Help appreciated of course

Arnaud

---

### Post by insitu on 2007-05-09
When I resume from suspend-to-disk, I can get back my wifi doing the following:
  1. suspend-to-ram
  2. resume 
  3. modprobe -r ipw3945
  4. modprobe  ipw3945
  5. turn of radio kill switch
  6. turn on radio kill switch

I can see where to put modprobes in my resume scripts but not why I have this discrepancy between str and std.

Thanks for any help.

Insitu

---

