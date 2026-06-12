---
title: "Portable SSD (External) 8TB USB 3.1"
date: 2022-05-11
forum: Hardware
---

### Post by acepa2 on 2022-05-11
Hello Guys,

I need help to my portable SSD (M.2 SSD - external) 8 TB (USB 3.1), model SHL-R320 (M.2/NGFF 2230/2242/2260/2280), drive on ubuntu 22.04 LTS. It works fine on windows 10, but doesn´t work on ubuntu. I tried use gparted and it show I/O error when I try to format  NTFS the partition. The device doesn´t show on file manager and the I can´t mount the volum manually.

Could you help me please? 

commands lsusb and fdisk -l results below:

lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 05c8:0383 Cheng Uei Precision Industry Co., Ltd (Foxlink) HP HD Camera
Bus 001 Device 004: ID 138a:003f Validity Sensors, Inc. VFS495 Fingerprint Reader
Bus 001 Device 003: ID 8087:0a2b Intel Corp. Bluetooth wireless interface
Bus 001 Device 008: ID 048d:1234 Integrated Technology Express, Inc. Chipsbank CBM2199 Flash Drive
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

fdisk -l

Disco /dev/sdb: 7,63 TiB, 8388608000000 bytes, 2048000000 setores
Disk model: USSD            
Unidades: setor de 1 * 4096 = 4096 bytes
Tamanho de setor (lógico/físico): 4096 bytes / 4096 bytes
Tamanho E/S (mínimo/ótimo): 4096 bytes / 4096 bytes
Tipo de rótulo do disco: dos
Identificador do disco: 0x40f96057


Dispositivo Inicializar Início        Fim    Setores Tamanho Id Tipo
/dev/sdb1                  256 2047999999 2047999744    7,6T 83 Linux



Thanks in advance.

Antonio

---

### Post by TheFu on 2022-05-11
8TB drives must use GPT. This is required for Windows too.
Using 'dos' or 'msdos' or 'mbr' partitioning limits the drive to 2TB.

Use Gparted.  Create a new partition table - pick GPT.  Then create the partitions you want. I always limit mine to 4TB, because my backup disks are all 4TB even if the drive is 8+TB.

After you create the partitions you want, right click on each and select the file system format you'd like.  Using NTFS for data is fine, but not for programs or home directories or any non-Windows OS.  NTFS doesn't retain owner, group, ACLs, xattrs and permissions like Unix-based file systems (ext4, f2fs, zfs, xfs, .... ) do.

This issue has nothing to do with Linux.

---

### Post by oldfred on 2022-05-11
Many SSD need firmware update.
And often UEFI needs firmware update also.

May not be a real 8TB drive.
[https://forums.tomshardware.com/threads/how-to-merge-ssd-8tb-drive-that-is-really-4-2tb-drives.3726599/](https://forums.tomshardware.com/threads/how-to-merge-ssd-8tb-drive-that-is-really-4-2tb-drives.3726599/)

---

### Post by acepa2 on 2022-05-12
Hi, TheFu,

Thanks for your response!


I tried to create the gpt table in gparted but the same error occurred (I/O  error).


Does this problem have to do with device drivers in the linux kernel? I am using kernel 5.15.0.27 generic kernel linux.

Thanks again.

Antonio

---

### Post by TheFu on 2022-05-12
oldfred - that link has this link: [https://magazine.renderosity.com/article/6277/dont-fall-for-the-cheap-ssd-drive-scam](https://magazine.renderosity.com/article/6277/dont-fall-for-the-cheap-ssd-drive-scam) Seems to be a HW scam. 
[https://www.youtube.com/watch?v=4iMm6wIktNk](https://www.youtube.com/watch?v=4iMm6wIktNk) shows something claimed to be 2TB, but turned out to be 4x32GB flash drives that he paid $80 - which is about 2x the real cost.

This isn't a Linux issue and Windows is lying about what the storage truly is. Sorry.

---

### Post by acepa2 on 2022-05-13
Hello, Guys!

I would like to thank everyone who replied to this topic. 

The Colleague TheFu was right, the ssd drive is fake, so it's not a linux problem. 

Thank you again!

---

