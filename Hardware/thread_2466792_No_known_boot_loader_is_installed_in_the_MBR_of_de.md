---
title: "No known boot loader is installed in the MBR of /dev/sda.sdb"
date: 2021-09-06
forum: Hardware
---

### Post by axjacks on 2021-09-06
I am running Ubuntu 20.04, which continuously fails to boot, instead taking me to BusyBox with a list of commands that do not work.

I booted off a USB, ran Boot Repair, which reports the following:




 ```
boot-repair-4ppa130                                              [20210906_0849]


============================== Boot Info Summary ===============================


 => No known boot loader is installed in the MBR of /dev/sda.


sdb: ___________________________________________________________________________


    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of
                       sdb and looks at sector 0 of the same hard drive for
                       core.img, but core.img can not be found at this
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.




================================ 0 OS detected =================================




============================ Architecture/Host Info ============================


CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Ubuntu 21.04, hirsute, x86_64)




===================================== UEFI =====================================


BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.


efibootmgr -v
BootCurrent: 0018
Timeout: 0 seconds
BootOrder: 0019,0018,0001,0017,0013,0000,0014,0015,0016,001A,001B
Boot0000* Windows Boot Manager HD(1,GPT,2533f1ed-55da-495e-b28d-b9db32311971,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...&............. ...
Boot0001* ubuntu HD(1,GPT,8cfd47b5-517c-4441-9cf8-c9d4b18936c4,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0010  Setup FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0011  Boot Menu FvFile(86488440-41bb-42c7-93ac-450fbf7766bf)
Boot0012  Diagnostic Splash FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0013* USB FDD: VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0014* NVMe: VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a4)
Boot0015* ATA NVMe: VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f602)
Boot0016* ATA HDD: ST1000LM035-1RK172                       PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,0,0)..bYVD.A...O.*..
Boot0017* ATAPI CD: HL-DT-ST DVDRAM GUE0N                   PciRoot(0x0)/Pci(0x17,0x0)/Sata(0,0,0)......!N.:^G.V.T
Boot0018* USB HDD: VendorCo ProductCode PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)3.!..3.G..A.....
Boot0019* USB CD: VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot001A* PCI LAN: EFI Network (IPv4) PciRoot(0x0)/Pci(0x1c,0x5)/Pci(0x0,0x0)/MAC(54ee75fe6e36,0)/IPv4(0.0.0.00.0.0.0,0,0)x.J.+*.N.....=8.
Boot001B* PCI LAN: EFI Network (IPv6) PciRoot(0x0)/Pci(0x1c,0x5)/Pci(0x0,0x0)/MAC(54ee75fe6e36,0)/IPv6([::]:<->[::]:,0,0)x.J.+*.N.....=8.
This session has been detected as 'live' because df -Th / contains overlay






============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________




Partitions info (1/3): _________________________________________________________




Partitions info (2/3): _________________________________________________________




Partitions info (3/3): _________________________________________________________




fdisk -l (filtered): ___________________________________________________________


Disk sdb: 7.5 GiB, 8053063680 bytes, 15728640 sectors
Disk identifier: AF8737A9-1E23-4373-B87A-C8B16199D461
        Start      End  Sectors  Size Type
sdb1       64  5494643  5494580  2.6G Microsoft basic data
sdb2  5494644  5504683    10040  4.9M EFI System
sdb3  5504684  5505283      600  300K Microsoft basic data
sdb4  5509120 15728576 10219457  4.9G Linux filesystem


parted -lm (filtered): _________________________________________________________


sda:1000GB:scsi:512:4096:unknown:ATA ST1000LM035-1RK1:;
sdb:8053MB:scsi:512:512:gpt:VendorCo ProductCode:;
1:32.8kB:2813MB:2813MB::ISO9660:hidden, msftdata;
2:2813MB:2818MB:5140kB::Appended2:boot, esp;
3:2818MB:2819MB:307kB::Gap1:hidden, msftdata;
4:2821MB:8053MB:5232MB:ext4::;


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL              PARTLABEL
sda                                                                                                          
sdb    iso9660  2021-04-20-11-16-16-00                                                    Ubuntu 21.04 amd64
&#9500;&#9472;sdb1 iso9660  2021-04-20-11-16-16-00               af8737a9-1e23-4373-b87b-c8b16199d461 Ubuntu 21.04 amd64 ISO9660
&#9500;&#9472;sdb2 vfat     F940-6C0E                            af8737a9-1e23-4373-b878-c8b16199d461 ESP                Appended2
&#9500;&#9472;sdb3                                               af8737a9-1e23-4373-b879-c8b16199d461                    Gap1
&#9492;&#9472;sdb4 ext4     eb03d3bc-fb49-430d-90f9-66bb318fdbf1 d896654f-7481-a640-a95f-5d068a35e1fb writable          


df (filtered): _________________________________________________________________


                                                          Avail Use% Mounted on
disk/by-label/writable[/install-logs-2021-09-06.0/crash]   4.5G   0% /var/crash
disk/by-label/writable[/install-logs-2021-09-06.0/log]     4.5G   0% /var/log
sdb1                                                          0 100% /cdrom


Mount options: __________________________________________________________________


disk/by-label/writable[/install-logs-2021-09-06.0/crash] rw,relatime
disk/by-label/writable[/install-logs-2021-09-06.0/log]   rw,relatime
sdb1                                                     ro,noatime,nojoliet,check=s,map=n,blocksize=2048




======================== Unknown MBRs/Boot Sectors/etc =========================


Unknown MBR on /dev/sda






=============================== StdErr Messages ================================


ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
File descriptor 63 (pipe:[62175]) leaked on lvs invocation. Parent PID 11492: /bin/bash


Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would not act on the boot.


Any advice would be greatly appreciated.
```

---

### Post by oldfred on 2021-09-06
Please use code tags for longer text or terminal output. I added them for you in first post.
Easy to add by highlighting text and using # icon in Forum's advanced editor.

Better to follow Boot-Repair's instructions and just post the link to the summary report.

And you should not have a boot loader in MBR for UEFI boot. MBR is only used for the now very old BIOS configuration.
But vendors still call UEFI as BIOS to confuse users. UEFI replaced BIOS for almost all systems in 2012 when Microsoft required Windows to be booted in UEFI mode from gpt partitioned drives.

You also show UEFI Secure Boot on, which prevents BIOS boot. Many find it easier to just turn off Secure Boot, but still use UEFI boot.
UEFI Secure Boot should work if you installed in UEFI secure boot mode and do not have proprietary video or WiFi. You can use proprietary drivers but you, as owner must verrify the code is secure.

Your sda drive is not shown and do you have a NVMe drive also?
Is Windows fast start up off?
UEFI fast boot off?

What brand, model system?
Have you updated UEFI and if NVMe updated NVMe firmware?

---

### Post by axjacks on 2021-09-06
Thanks. Apologies for not using code tags. This is my first bug report to Ubuntu.

Re [COLOR=#000000]UEFI Secure Boot, I did turn that off after seeing it suggested in a related thread. Still won't boot though.

The model is [/COLOR][B]Lenovo V130- Core i5-7200U 8GB 1TB NVMe SSD
[/B]So yes, it has an NVMe drive. 

I'm pretty sure I have not updated UEFI and NVMe firmware.


[COLOR=#000000]Windows fast start up does not appear in BIOS. Just Windows Boot Manager. And BIOS does not show UEFI Fast Boot - just "Boot Mode [UEFI]", which can't be toggled to a different mode.[/COLOR]

The fact that the SDA drive is not showing worries me. It seems like Boot Repair and GParted can't detect the hard drive. :(

Thanks again for any suggestions.
[COLOR=#000000]
 [/COLOR]

---

### Post by oldfred on 2021-09-06
Brand new Lenovo's are UEFI class 3 or UEFI only.
Yours looks older, so should have CSM aka BIOS aka Legacy boot mode. Microsoft required that in the past.
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)

While for USB-C on these models, update of UEFI often fixes many other issues.
UEFI update required for USB-C port issues 2017 thru 2019 models
ThinkPad models including the ThinkPad X1 Carbon (5th Gen to 7th Gen), X1 Yoga (2nd Gen to 4th Gen), and P-series 
[https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/](https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/)
Spectre virus, repoline firmware update
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.

---

### Post by tea for one on 2021-09-06
> **axjacks said:**
> Windows fast start up does not appear in BIOS. Just Windows Boot Manager. And BIOS does not show UEFI Fast Boot - just "Boot Mode [UEFI]", which can't be toggled to a different mode.

The fact that the SDA drive is not showing worries me. It seems like Boot Repair and GParted can't detect the hard drive. 

Windows Fast Start Up is a setting [COLOR="#0000FF"]within[/COLOR] Windows 10.
It hibernates the disk to allow Windows to boot quickly.

[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

Some Windows updates re-enable Fast Start Up even after the user has disabled it.

---

### Post by axjacks on 2021-09-07
Thanks. It sounds like an update of UEFI might fix the problem. Given that I can't boot from the hard disk, will I be able to update the firmware by running Ubuntu on a USB stick?

---

### Post by oldfred on 2021-09-07
Only some newer systems now support firmware update from Linux. You can see if yours is available:
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

Most also update from within UEFI if you download update file into a FAT32 partition, either on system or flash drive.
Some have a DOS bootable flash drive that lets you run the update program and file. Someone did post how to extract update file from an .exe from Linux, but I did not have any reference to that.
A few only seem to update from Windows, or users just did not understand how to do it.

My Asus motherboard updates from within UEFI.I made ESP larger, so I have room from download.
My NVMe Samsung drive had a bootable ISO download just for my model & firmware version. It was very simple and looked somewhat like old DOS screen, but worked without issue.

---

### Post by axjacks on 2021-09-08
Unfortunately, my system is not on the list. But I did find a reference to creating a DOS bootable flash drive for pretty much the same purpose: [boot - How to create a bootable USB stick to flash a BIOS - Ask Ubuntu]("https://askubuntu.com/questions/46886/how-to-create-a-bootable-usb-stick-to-flash-a-bios") Seems like a possible way around the fact that Windows is required for a BIOS update for this model. Will give it shot.

---

### Post by axjacks on 2021-09-09
OK. I tried to resolve this by using FreeDOS to update the BIOS using the requried .exe firmware file. But unfortunately FreeDOS will not work with UEFI and this ThinkPad model does not allow me to switch from UEFI to Legacy. It's UEFI only. 

So, unless I'm missing something, it looks like it's the end of the line for my laptop. :(

At this point, all I want to do now is recover the data on my hard drive. I can see the drive when I run lsblk (name sda), but that's not a directory and I have no way of mounting the drive so as to recover the files. Is the data on my internal drive unrecoverable now?

---

### Post by tea for one on 2021-09-09
> **axjacks said:**
> At this point, all I want to do now is recover the data on my hard drive. I can see the drive when I run lsblk (name sda), but that's not a directory and I have no way of mounting the drive so as to recover the files. Is the data on my internal drive unrecoverable now?

The data to be recovered - is it in the Ubuntu system or the Windows system?

Boot-repair shows 0 (zero) Operating Systems detected but you do have an Ubuntu and Windows entries via efibootmgr.

Also, according to the boot-repair report, your drive is a Seagate model.

[COLOR="#0000FF"]sda:1000GB:scsi:512:4096:unknown:ATA ST1000LM035-1RK1 [/COLOR]= Seagate ST1000LM035

Secondly, the line in the report [COLOR="#0000FF"]ERROR: jmicron: reading /dev/sda[Input/output error][/COLOR] indicates that, possibly, the controller is not allowing the drive to be recognised.

It's difficult to diagnose the exact problem:-

Faulty drive
Faulty controller

if you cannot mount the drive in a live session:-

Remove the drive
Buy/borrow an external drive holder with USB connection
Perhaps the drive can be seen as an external device.

---

### Post by axjacks on 2021-09-10
Thanks for the suggestions.

I didn't set it up for dual operating systems, just wiped the HD entirely and installed Ubuntu. So the data is in Ubuntu, since that's only operating system on the drive. (I'm learning what a mistake it was to get rid of Windows completely!)

I will do as you suggest and see if I can use an external drive holder with a USB connection and hopefully I can see the device that way and extract data.

I think I will mark this thread as closed, seeing as it was originally intended to solve the BIOS update problem and I've effectively moved on to a different topic.

---

