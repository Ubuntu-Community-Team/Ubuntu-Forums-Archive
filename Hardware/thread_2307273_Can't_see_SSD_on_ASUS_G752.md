---
title: "Can't see SSD on ASUS G752"
date: 2015-12-23
forum: Hardware
---

### Post by someone2353 on 2015-12-23
Hi.
I try to install Ubuntu on Asus G752, but when It's time to configure partitions, I see only my HDD. Someone knows what can I do about this?
This is my lspci:
```

00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Sky Lake PCIe Controller (x16) (rev 07)
00:04.0 Signal processing controller: Intel Corporation Device 1903 (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-H LPSS I2C Controller #0 (rev 31)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-H LPSS I2C Controller #1 (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 RAID bus controller: Intel Corporation SATA Controller [RAID mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #3 (rev f1)
00:1c.3 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #4 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #5 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
01:00.0 VGA compatible controller: NVIDIA Corporation GM204M [GeForce GTX 970M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GM204 High Definition Audio Controller (rev a1)
02:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)

```

---

### Post by oldfred on 2015-12-23
You are showing Skylake with nVidia. And is RAID really on? Some high end laptops do have RAID or Intel SRT which looks like RAID?

What version of Ubuntu? 
With Skylake you need the newest plus some updates to have it work well or wait for 16.04. You can try a test install of 16.04, but until released in April, 2016, should not necessarily rely on it. Updates may break it at any point.

       Best Ubuntu version for new Z170 motherboards /w Intel video? Oct 2015
[http://ubuntuforums.org/showthread.php?t=2292521](http://ubuntuforums.org/showthread.php?t=2292521)

   Xeon Skylake Users May Run Into Display Problems With Current Distributions Dec 2015
[http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset](http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset)
Intel's Skylake Audio Firmware Lands
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Skylake-Audio-Firmware](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Skylake-Audio-Firmware)
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-BXT-Firmware-Blobs](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-BXT-Firmware-Blobs)
Skylake Intel Core i5 6500: A Great Skylake CPU For $200, Works Well On Linux, 4.3 kernel  for best graphics
[http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1)
Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[URL="http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support"]http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support

[/URL]
 ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)

[URL="http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support"]
[/URL]

---

### Post by someone2353 on 2015-12-23
without 16.04 it won't at all, or it won't work optimally?
I try to install 15.10, and RAID is marked as ON on BIOS. Currently I try to focus on my SSD problem, before I'll move on to my Skylake problems (I hope I won't have any)

---

### Post by oldfred on 2015-12-23
Is it RAID as you have two drives, or RAID using Intel SRT which creates a smaller hibernation partition. 
What type of SSD. 
Some new NVMe also need newer drivers and newer version of gparted than in installer.
 gparted should be at least version 0.24.0-1 to recognize NVMe devices

---

### Post by someone2353 on 2015-12-23
I have two drives, 128 SSD, and 1T HDD.
My SSD is nvme samsung mzvpv128.

---

### Post by oldfred on 2015-12-23
If you download the newer gparted does it show the NVMe devices?
 The simple part is to look in "/dev/nvme*". The devices will be numbered and the actual block device will have an n1 on the end, to support NVMe namespaces. So if you have one PCIe card or front-loading 2.5" drive, you'll have /dev/nvme0n1 as a block device to format, partition and use.

This says that NVMe should be in latest Ubuntu. Do you see drives with commands shown?
[https://communities.intel.com/community/itpeernetwork/blog/2014/10/10/finding-your-new-intel-ssd-for-pcie-think-nvme-not-scsi](https://communities.intel.com/community/itpeernetwork/blog/2014/10/10/finding-your-new-intel-ssd-for-pcie-think-nvme-not-scsi)
You may need to load the driver or compile kernel:
[http://manpages.ubuntu.com/manpages/vivid/man4/nvme.4freebsd.html](http://manpages.ubuntu.com/manpages/vivid/man4/nvme.4freebsd.html)

---

### Post by someone2353 on 2015-12-23
[COLOR=#1f497d][FONT=Calibri] [B]lspci | grep 0953: nothing
lsblk|grep nvm: nothing
```

filename:       /lib/modules/4.2.0-16-generic/kernel/drivers/block/nvme.ko
version:        1.0
license:        GPL
author:         Matthew Wilcox <willy@linux.intel.com>
srcversion:     25AFBF2AB9A28059C4784ED
alias:          pci:v*d*sv*sd*bc01sc08i02*
depends:        
intree:         Y
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6A:1C:9C:21:F0:4A:B8:6F:D1:D7:CE:D6:CA:11:35:40:FC:8E:35:B6
sig_hashalgo:   sha512
parm:           admin_timeout:timeout in seconds for admin commands (byte)
parm:           io_timeout:timeout in seconds for I/O (byte)
parm:           shutdown_timeout:timeout in seconds for controller shutdown (byte)
parm:           nvme_major:int
parm:           nvme_char_major:int
parm:           use_threaded_interrupts:int

```
[/B][/FONT][/COLOR][COLOR=#1f497d][FONT=Calibri][B]lsmod | grep nvm: nothing
[COLOR=#1f497d][FONT=Calibri] [B]ll /dev/nvme*n1: ls: cannot access /dev/nvme*n1: No such file or directory

hdparm -tT --direct /dev/nvme01: nothing[/B][/FONT][/COLOR] 
[/B][/FONT][/COLOR]

---

### Post by oldfred on 2015-12-23
It is beyond me now.
Did you look at the Asus user with a somewhat differnent model in post #2? He seemed to use NVMe.

---

### Post by someone2353 on 2015-12-24
Do you mean this user? [https://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](https://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)

---

### Post by someone2353 on 2015-12-24
I've tried 16.04. I still cannot see the SSD.

---

### Post by oldfred on 2015-12-24
Supposedly bug fixed back with 2014.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1303710](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1303710)

So maybe your Intel RAID settings are real issue in combination with NVMe?

These are all older installs, and most posts show it now works without these issues.
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
HP Envy  Windows 7 with MBR & SRT
[http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx](http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

---

### Post by Serge_Malo on 2016-01-02
Hi all,

I'm facing the same issue with ASUS ROG G752VY-DH2.
I have tried several suggestions ([https://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](https://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)) with Ubuntu 15.10, without success.

Please, let me know if you find anything new, or have another suggestion.

Regards,
Serge

---

### Post by Serge_Malo on 2016-01-02
I have been able to go a bit further than "someone2353":
I have booted on the Ubuntu 15.10 Live USB, then:

modinfo | grep nvme **returned that the nvme driver is actually in the kernel.**
lsmod | grep nvme showed that the nvme driver was not loaded.
I loaded the driver with modprobe nvme.
Then, lsmod | grep nvme showed that is was loaded.

But then, I'm stuck: there is still no device named "/dev/nvme*", and I don't see the SSD listed with lsblk.

Is there anything I should do after loading the driver? Or how can I make sure that nvme driver is loaded at boot time, on the live USB?

Regards,
Serge

---

### Post by Serge_Malo on 2016-01-03
Hi again,

After other researches and trials, I come to the same conclusion as "travo5200": This is a BIOS issue.
[https://rog.asus.com/forum/showthread.php?79205-Cannot-see-NVMe-M-2-Samsung-Drive-in-Linux-on-ASUS-G752V](https://rog.asus.com/forum/showthread.php?79205-Cannot-see-NVMe-M-2-Samsung-Drive-in-Linux-on-ASUS-G752V)

I'm running today's latest BIOS of the G752 (V 208), and there is no other choice than "RAID" in the SATA section of the BIOS.

I found that DELL XPS users are facing a similar issue, but they can fix this by using "nvme_load=YES" on the linux boot command.
[http://www.dell.com/support/article/us/en/04/SLN151664/en](http://www.dell.com/support/article/us/en/04/SLN151664/en)

I have tried this on the ASUS G752, with no success (Ubuntu 14.04 and 15.10)

For the moment, in my ASUS G752, I'm really unable to see its "M2 Samsung sm951 (MZVPV256HDGL-00000)" SSD in Ubuntu 14.04 or 15.10.

---

### Post by pino-silvaggio on 2016-01-13
I will receive my G752VY soon, so I'm very interested in this.

Did you try Fedora Live DVD ? Their kernel is much more recent.

---

### Post by pino-silvaggio on 2016-01-29
Asus updated their BIOS for g752vt and now support AHCI. I guess g752vy will be next.

Linux should now be able to see the drives.

---

### Post by s-byczkowski on 2016-12-19
> **pino-silvaggio said:**
> Asus updated their BIOS for g752vt and now support AHCI. I guess g752vy will be next.Linux should now be able to see the drives.

But it also should see it in IRST Raid mode. I fiddled with this and it seems disconnecting NVME SSD physically from laptop and linux sees the HDD and internal cd drive right away.
With SSD connected and Raid mode in BIOS. There are  Samsung 950Pro and HGST HTS721010A9E630 and TSSTcorp CDDVDW SU-228GB connected to IRST Raid in JBOD mode, the Samsung 950Pro does not get detected!
1. Open terminal.
2. su [enter]
3. mdadm --detail-platform
Platform : Intel(R) Rapid Storage Technology
        Version : 14.8.0.2377
    RAID Levels :
    Chunk Sizes : 4k 8k 16k 32k 64k 128k
    2TB volumes : supported
      2TB disks : supported
      Max Disks : 7
    Max Volumes : 2 per array, 4 per controller
 I/O Controller : /sys/devices/pci0000:00/0000:00:17.0 (SATA)
          Port0 : - no device attached -
          Port1 : - no device attached -  <= should see drives here, but none are present, which is total screwup by ASUS.

 Problems with ata driver from dmesg:
```
[    9.206647] ata2.00: qc timeout (cmd 0xa1)
[    9.206655] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[    9.206670] ata1.00: qc timeout (cmd 0xef)
[    9.206677] ata1.00: failed to enable AA (error_mask=0x4)
[    9.517319] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    9.517343] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    9.520588] ata1.00: ATA-8: HGST HTS721010A9E630, JB0OA3J0, max UDMA/133
[    9.520592] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   19.958671] ata2.00: qc timeout (cmd 0xa1)
[   19.958679] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   19.958682] ata2: limiting SATA link speed to 1.5 Gbps
[   20.269167] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   25.590680] ata1.00: qc timeout (cmd 0x27)
[   25.590687] ata1.00: failed to read native max address (err_mask=0x4)
[   25.590689] ata1.00: HPA support seems broken, skipping HPA handling
[   25.590691] ata1.00: revalidation failed (errno=-5)
[   25.590741] ata1: limiting SATA link speed to 3.0 Gbps
[   25.590743] ata1.00: limiting speed to UDMA/133IO3
[   25.901171] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[   40.950718] ata1.00: qc timeout (cmd 0xef)
[   40.950724] ata1.00: failed to set xfermode (err_mask=0x4)
[   40.950777] ata1.00: disabled
[   40.950790] ata1: hard resetting link
[   41.261221] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[   41.261230] ata1: EH complete
[   50.678741] ata2.00: qc timeout (cmd 0xa1)
[   50.678749] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   50.989249] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
```

As you can see ata1 is HDD ata2 is probably NVME SSD or maybe cddrive but it is not getting detected due to above errors.
Now with disconnected NVME SSD:

```
root@live> mdadm --detail-platform
Platform : Intel(R) Rapid Storage Technology
        Version : 14.8.0.2377
    RAID Levels :
    Chunk Sizes : 4k 8k 16k 32k 64k 128k
    2TB volumes : supported
      2TB disks : supported
      Max Disks : 7
    Max Volumes : 2 per array, 4 per controller
 I/O Controller : /sys/devices/pci0000:00/0000:00:17.0 (SATA)
          Port1 : - non-disk device (TSSTcorp CDDVDW SU-228GB) -
          Port0 : /dev/sda (JR10004M09SMLF)
```
Now both HDD and cd drive are getting detected in RAID mode.
 I know you can use AHCI with BIOS 2.11 up in linux,but if you do use dual boot with Windows you [URL="https://answers.microsoft.com/en-us/windows/forum/windows_10-update/windows-10-anniversary-update-install-on-m2-ssd/d9f4f796-0373-4659-ab4e-0d66e6894e4f"]won't be able to install major
Windows updates like 1607 due to BSOD 0xc0000225 "winload.efi missing or corrupt".[/URL] Believe me I have tried to do it. BIOS in G752vy does not properly present NVME SSD to the system.
One symptom of this is BIOS not showing the name of NVME SSD in F12 BootUp Menu, for SSD it will just display "Windows Boot Manager", but for HDD it will display "Windows Boot Manager PO:HGST HTS721010A9E630".
But in Raid mode you get both names for SSD and HDD in Boot Menu. Check it!
 The G752 bios does not recognize the SSD in the proper way. Asus know about it, because I reported this problem many times to their support. Up to this day there is no fix. Windows
also has problems installing on this laptop when SSD is in. When you load a IRST RAID driver(old F6 option) in Windows Setup it will BSOD IRQ_NOT_LESS_OR_EQUAL or WATCHDOG_VIOLATON. So far ASUS support recomended, that I install from bootable usb and then install IRST RAID driver, because installing Windows from cddrive will casuse BSODs. Buy saying that, support admited they know about the problem, but I do not think support is doing anything to fix it.
[Here ]("https://rog.asus.com/forum/showthread.php?79822-G752-with-Samsung-950-Pro-SSD-new-information")is a report from ASUS-Samsung conference calling each other names and blaiming each other, because of that problem. But it is the problem with every NVME SSD and G752!

---

### Post by s-byczkowski on 2016-12-19
> **pino-silvaggio said:**
> Asus updated their BIOS for g752vt and now support AHCI. I guess g752vy will be next.Linux should now be able to see the drives.

But it also should see it in IRST Raid mode. I fiddled with this and it seems disconnecting NVME SSD physically from laptop and linux sees the HDD and internal cd drive right away.
With SSD connected and Raid mode in BIOS. There are  Samsung 950Pro and HGST HTS721010A9E630 and TSSTcorp CDDVDW SU-228GB connected to IRST Raid in JBOD mode, the Samsung 950Pro does not get detected! This is with 16.10.
1. Open terminal.
2. su [enter]
3. mdadm --detail-platform
Platform : Intel(R) Rapid Storage Technology
        Version : 14.8.0.2377
    RAID Levels :
    Chunk Sizes : 4k 8k 16k 32k 64k 128k
    2TB volumes : supported
      2TB disks : supported
      Max Disks : 7
    Max Volumes : 2 per array, 4 per controller
 I/O Controller : /sys/devices/pci0000:00/0000:00:17.0 (SATA)
          Port0 : - no device attached -
          Port1 : - no device attached -  <= should see drives here, but none are present, which is total screwup by ASUS.

 Problems with ata driver from dmesg:
```
[    9.206647] ata2.00: qc timeout (cmd 0xa1)
[    9.206655] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[    9.206670] ata1.00: qc timeout (cmd 0xef)
[    9.206677] ata1.00: failed to enable AA (error_mask=0x4)
[    9.517319] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    9.517343] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    9.520588] ata1.00: ATA-8: HGST HTS721010A9E630, JB0OA3J0, max UDMA/133
[    9.520592] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   19.958671] ata2.00: qc timeout (cmd 0xa1)
[   19.958679] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   19.958682] ata2: limiting SATA link speed to 1.5 Gbps
[   20.269167] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   25.590680] ata1.00: qc timeout (cmd 0x27)
[   25.590687] ata1.00: failed to read native max address (err_mask=0x4)
[   25.590689] ata1.00: HPA support seems broken, skipping HPA handling
[   25.590691] ata1.00: revalidation failed (errno=-5)
[   25.590741] ata1: limiting SATA link speed to 3.0 Gbps
[   25.590743] ata1.00: limiting speed to UDMA/133:PIO3
[   25.901171] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[   40.950718] ata1.00: qc timeout (cmd 0xef)
[   40.950724] ata1.00: failed to set xfermode (err_mask=0x4)
[   40.950777] ata1.00: disabled
[   40.950790] ata1: hard resetting link
[   41.261221] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[   41.261230] ata1: EH complete
[   50.678741] ata2.00: qc timeout (cmd 0xa1)
[   50.678749] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   50.989249] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
```

As you can see ata1 is HDD ata2 is probably NVME SSD or maybe cddrive but it is not getting detected due to above errors.
Now with disconnected NVME SSD:

```
root@live> mdadm --detail-platform
Platform : Intel(R) Rapid Storage Technology
        Version : 14.8.0.2377
    RAID Levels :
    Chunk Sizes : 4k 8k 16k 32k 64k 128k
    2TB volumes : supported
      2TB disks : supported
      Max Disks : 7
    Max Volumes : 2 per array, 4 per controller
 I/O Controller : /sys/devices/pci0000:00/0000:00:17.0 (SATA)
          Port1 : - non-disk device (TSSTcorp CDDVDW SU-228GB) -
          Port0 : /dev/sda (JR10004M09SMLF)
```
Now both HDD and cd drive are getting detected in RAID mode.
 I know you can use AHCI with BIOS 2.11 up in linux,but if you do use dual boot with Windows you [URL="https://answers.microsoft.com/en-us/windows/forum/windows_10-update/windows-10-anniversary-update-install-on-m2-ssd/d9f4f796-0373-4659-ab4e-0d66e6894e4f"]won't be able to install major
Windows updates like 1607 due to BSOD 0xc0000225 "winload.efi missing or corrupt".[/URL] Believe me I have tried to do it. BIOS in G752vy does not properly present NVME SSD to the system.
One symptom of this is BIOS not showing the name of NVME SSD in F12 BootUp Menu, for SSD it will just display "Windows Boot Manager", but for HDD it will display "Windows Boot Manager PO:HGST HTS721010A9E630".
But in Raid mode you get both names for SSD and HDD in Boot Menu. Check it!
 The G752 bios does not recognize the SSD in the proper way. Asus know about it, because I reported this problem many times to their support. Up to this day there is no fix. Windows
also has problems installing on this laptop when SSD is in. [When you load a IRST RAID driver(old F6 option) in Windows Setup it will BSOD IRQ_NOT_LESS_OR_EQUAL or WATCHDOG_VIOLATON]("https://rog.asus.com/forum/showthread.php?88586-G752vy-Buggy-AHCI-Mode-in-BIOS-up-to-2-13-Do-not-switch-to-AHCI-on-NVME-SSD"). So far ASUS support recomended, that I install from bootable usb and then install IRST RAID driver, because installing Windows from cddrive will casuse BSODs. Buy saying that, support admited they know about the problem, but I do not think support is doing anything to fix it.
[Here ]("https://rog.asus.com/forum/showthread.php?79822-G752-with-Samsung-950-Pro-SSD-new-information")is a report from ASUS-Samsung conference calling each other names and blaiming each other, because of that problem. But it is the problem with every NVME SSD and G752!

---

