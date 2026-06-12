---
title: "Raid controller SiliconImage (SIL3124) on 16.04 amd64, Help!!!"
date: 2016-05-06
forum: Hardware
---

### Post by MaxVio on 2016-05-06
Hi to everybody, i hope to find a solution here after have searched over the web unusefully...
I have two hard disk, a single sata where i want to install the system and a four disks Raid where i stored many datas already;
My trouble is that if the raid is connected to the motherboard there is no way to install the distrubution, instead, if it is not connected the Ubuntu recognize everithing well and finish the installation process;
Also i need to access those datas after the installation but ubuntu doesn't want to ear anything, it dosn't see the Raid controller.
The controller incriminated is the one i wrote in the title...
Is there anybody who can help me?

Thank you in advance for any reply,

Max

---

### Post by MaxVio on 2016-05-07
Nobody is able to help me? 

I add that after a lspci i see that the controller is listed.. this is the return:

[B]04:04.0 RAID bus controller: Silicon Image, Inc. SiI 3124 PCI-X Serial ATA Controller (rev 02)

[/B]but i find no raid volume in the left bar...

---

### Post by MaxVio on 2016-05-07
Also, with a lspci -vv i get this:

**04:04.0 RAID bus controller: Silicon Image, Inc. SiI 3124 PCI-X Serial ATA Controller (rev 02)**
**	Subsystem: Silicon Image, Inc. SiI 3124 PCI-X Serial ATA Controller**
**	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV+ VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-**
**	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-**
**	Latency: 32, Cache Line Size: 32 bytes**
**	Interrupt: pin A routed to IRQ 19**
**	Region 0: Memory at fe8ffc00 (64-bit, non-prefetchable) [size=128]**
**	Region 2: Memory at fe8f0000 (64-bit, non-prefetchable) [size=32K]**
**	Region 4: I/O ports at dc00 [size=16]**
**	Expansion ROM at fe800000 [disabled] [size=512K]**
**	Capabilities: <access denied>**
**	Kernel driver in use: sata_sil24**
**	Kernel modules: sata_sil24**&#8203;

---

### Post by MaxVio on 2016-05-07
sudo fdisk -l return this

**Disk /dev/sdf: 465,8 GiB, 500107862016 bytes, 976773168 sectors**
**Units: sectors of 1 * 512 = 512 bytes**
**Sector size (logical/physical): 512 bytes / 512 bytes**
**I/O size (minimum/optimal): 512 bytes / 512 bytes**
**Disklabel type: dos**
**Disk identifier: 0xa95ebacd**

**Dispositivo Avvio      Start       Fine    Settori   Size Id Tipo**
**/dev/sdf1                 63       2047       1985 992,5K 42 SFS**
**/dev/sdf2   *           2048     718847     716800   350M 42 SFS**
**/dev/sdf3             718848 1953538047 1952819200 931,2G 42 SFS**
**/dev/sdf4         1953538048 1953540095       2048     1M 42 SFS**


**Disk /dev/sdg: 465,8 GiB, 500107862016 bytes, 976773168 sectors**
**Units: sectors of 1 * 512 = 512 bytes**
**Sector size (logical/physical): 512 bytes / 512 bytes**
**I/O size (minimum/optimal): 512 bytes / 512 bytes**
**Disklabel type: dos**
**Disk identifier: 0x849020a3**


**Disk /dev/sdh: 465,8 GiB, 500107862016 bytes, 976773168 sectors**
**Units: sectors of 1 * 512 = 512 bytes**
**Sector size (logical/physical): 512 bytes / 512 bytes**
**I/O size (minimum/optimal): 512 bytes / 512 bytes**
**Disklabel type: dos**
**Disk identifier: 0x6a3ee2d1**

**Dispositivo Avvio      Start       Fine    Settori   Size Id Tipo**
**/dev/sdh1                 63       2047       1985 992,5K 42 SFS**
**/dev/sdh2   *           2048     718847     716800   350M 42 SFS**
**/dev/sdh3             718848 1953538047 1952819200 931,2G 42 SFS**
**/dev/sdh4         1953538048 1953540095       2048     1M 42 SFS**


**Disk /dev/sdi: 465,8 GiB, 500107862016 bytes, 976773168 sectors**
**Units: sectors of 1 * 512 = 512 bytes**
**Sector size (logical/physical): 512 bytes / 512 bytes**
[B]I/O size (minimum/optimal): 512 bytes / 512 bytes

---------------------------------------------------------------------


[/B]So, the system see also the four disks attached to the Raid card, what have i to do then to be able using it????

#-o#-o#-o#-o#-o

---

### Post by MaxVio on 2016-05-13
Up!!

---

