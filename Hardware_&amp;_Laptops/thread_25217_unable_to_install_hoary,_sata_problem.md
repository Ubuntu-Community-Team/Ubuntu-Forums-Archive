---
title: "unable to install hoary, sata problem"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by olvesh on 2005-04-09
I have earlier had troubles moving from kernel 2.6.8 (2.6.9 and 2.6.10 give a kernel panic - do a search for 'olve' to see the posts). I also have a few other minor problems, and given the easy installation warty proved to be, I have decided to try to reinstall to another drive, and salvage my home directory from the second drive.
Both my drives are sata drives, see the snippet from /proc/scsi/scsi below.

I am running hoary now, an upgrade from a warty installation.

During the installation, the partition program gives an error, saying it doesnt find any attached drives, while the hoary live cd does find them, giving my two sata drives the devices /dev/sdf and /dev/sdg (probably adding them after all the usb-gizmos I have attached - in 2.6.8 they appear as /dev/sda and /dev/sdb). The installation of warty was utterly painless - it seems like hoary has stepped a few steps backwards in terms of hardware compatability. :?

I guess that the problems I have with the 2.6.10 kernel also are the same that prevents me reinstalling hoary. 

I have been using linux (debian and now ubuntu) for some time, but have never really understood which module goes with which main-board (io controller). I guess this problem eventually boiles down to something like that.

I hope someone can help me with my problems, since I have earlier been very keen on spreading the "ubuntu gospel" O:)

 ```

cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA	  Model: ST3160023AS	  Rev: 3.00
  Type:   Direct-Access				    ANSI SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA	  Model: ST3160023AS	  Rev: 3.00
  Type:   Direct-Access

``` 

lspci 
 ```

0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 915G/P/GV PCI Express Root Port (rev 04)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 3e50
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 3e70
0000:0b:04.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:0b:05.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
0000:0b:06.0 FireWire (IEEE 1394): Lucent Microelectronics FW323 (rev 61)
0000:0b:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:0b:09.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
0000:0b:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
0000:0b:0b.0 Communication controller: Conexant: Unknown device 2f20


```

---

### Post by alastair on 2005-04-09
Not finding the SATA drives at install time /might/ be a BIOS issue. Linux SATA has no support (yet I think) for Advanced Host Controller Interface (AHCI), which is in the Intel ICH6 controller.

Go into your BIOS and check the SATA settings. Switch to "legacy" if available (or "ATA" mode maybe).

I think the support module is "ata_piix". Check using "lsmod" on a working system.

Hope that helps.

---

### Post by olvesh on 2005-04-09
[QUOTE=alastair]Not finding the SATA drives at install time /might/ be a BIOS issue. Linux SATA has no support (yet I think) for Advanced Host Controller Interface (AHCI), which is in the Intel ICH6 controller.

Go into your BIOS and check the SATA settings. Switch to "legacy" if available (or "ATA" mode maybe).[/QUOTE]
I have been running the bios in native (dunno the diference between legacy and native, I do have a legacy mode as well, in addition to raid and ahci) mode all along. It works for 2.6.8, but not 2.6.9/10. AHCI only partially works with the 2.6.11 kernel, it boots, but hangs later on, not sure if it is because of the sata drives. 

 > 
 I think the support module is "ata_piix". Check using "lsmod" on a working system.
 
The ata_piix is loaded when using 2.6.8.
>lsmod|grep ata
ata_piix                8388  7
libata                 42020  1 ata_piix
scsi_mod              127972  5 sbp2,sr_mod,sd_mod,usb_storage,libata

I'll experiment with the legacy mode, but I am puzzled to why the native bios mode doesn't work with hoary (2.6.9/10) when it did work with 2.6.8. I'll post more news about my progress tomorrow.

Thanks for the help so far.
Olve

---

### Post by olvesh on 2005-04-10
[QUOTE=alastair]Not finding the SATA drives at install time /might/ be a BIOS issue. Linux SATA has no support (yet I think) for Advanced Host Controller Interface (AHCI), which is in the Intel ICH6 controller.

Go into your BIOS and check the SATA settings. Switch to "legacy" if available (or "ATA" mode maybe).

I think the support module is "ata_piix". Check using "lsmod" on a working system.

Hope that helps.[/QUOTE]

I have messeda around with the bios settings now, and I don't have a 'legacy' setting. I have a AHCI, Native, Compatible and RAID setting. If I switch to Compatible, my current installed os becomes unbootable. 

I tried starting up the system in compatible mode, and started the intstaller, and it found my harddrive, but only one of the two. In the bios, I can either choose to enable both SATA channels, and disable P-ATA (i.e. no cdrom support), or I can disable two of the SATA channels, and still have P-ATA access.

In my mind the Native mode should work satisfactory as I am running a 2.6.8 Ubuntu kernel. This is the OS I use for my daily work. Booting into the live cd also give me access to the drives. I guess the modules needed are not loaded until after the system boots.. If I knew which to add, I could add them in my /etc/mkinitrd/modules list, and reinstall the 2.6.10 kernel. This is what I tried in
[http://ubuntuforums.org/showthread.php?t=13077](http://ubuntuforums.org/showthread.php?t=13077) and
[http://ubuntuforums.org/showthread.php?t=20231](http://ubuntuforums.org/showthread.php?t=20231)

Using an OS that doesn't fully support my hardware is kind of dangerous. If I get some kind of failure forcing me to reinstall from backups, I am in deep shit as it is now, because I can't use the hoary installer to reinstall my system.

Are there anything else you  can think of that can help me in my situation? 

Thanks for putting up with me so far :-)

-- 
Olve S. Hansen

---

### Post by Dinler on 2005-04-19
[QUOTE=olvesh]I have messeda around with the bios settings now, and I don't have a 'legacy' setting. I have a AHCI, Native, Compatible and RAID setting. If I switch to Compatible, my current installed os becomes unbootable. 

I tried starting up the system in compatible mode, and started the intstaller, and it found my harddrive, but only one of the two. In the bios, I can either choose to enable both SATA channels, and disable P-ATA (i.e. no cdrom support), or I can disable two of the SATA channels, and still have P-ATA access.

In my mind the Native mode should work satisfactory as I am running a 2.6.8 Ubuntu kernel. This is the OS I use for my daily work. Booting into the live cd also give me access to the drives. I guess the modules needed are not loaded until after the system boots.. If I knew which to add, I could add them in my /etc/mkinitrd/modules list, and reinstall the 2.6.10 kernel. This is what I tried in
[http://ubuntuforums.org/showthread.php?t=13077](http://ubuntuforums.org/showthread.php?t=13077) and
[http://ubuntuforums.org/showthread.php?t=20231](http://ubuntuforums.org/showthread.php?t=20231)

Using an OS that doesn't fully support my hardware is kind of dangerous. If I get some kind of failure forcing me to reinstall from backups, I am in deep shit as it is now, because I can't use the hoary installer to reinstall my system.

Are there anything else you  can think of that can help me in my situation? 

Thanks for putting up with me so far :-)

-- 
Olve S. Hansen[/QUOTE]

I have a Fujutsi-Siemens with 2 250GB SATA disks. I have same options in bios like you and if i change from one to another, something would not work.

Have you figured out the problem yet?

PLEASE HELP US (ME)!

---

### Post by olvesh on 2005-04-19
Nope, don't seem like my brew of hardware is supported by Ubuntu (a ScaleoT Fujitsu Siemens). I guess it is "only" a kernel config issue, so if you find the correct modules and compile them in, it should work, since I can mount the drives after the live-cd has booted.
It is does work in 2.6.8 (from warty), but not using 2.6.10.

I am pretty sure that the Native bios mode is the right one, even windows doesn't work with ahci on.

I just think it is a shame that ubuntu doesn't support the hardware they did support in warty anymore..

---

### Post by Dinler on 2005-04-19
[QUOTE=olvesh]Nope, don't seem like my brew of hardware is supported by Ubuntu (a ScaleoT Fujitsu Siemens). I guess it is "only" a kernel config issue, so if you find the correct modules and compile them in, it should work, since I can mount the drives after the live-cd has booted.
It is does work in 2.6.8 (from warty), but not using 2.6.10.

I am pretty sure that the Native bios mode is the right one, even windows doesn't work with ahci on.

I just think it is a shame that ubuntu doesn't support the hardware they did support in warty anymore..[/QUOTE]

WORD!

---

