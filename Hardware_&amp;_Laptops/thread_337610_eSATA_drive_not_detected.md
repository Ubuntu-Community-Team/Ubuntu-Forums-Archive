---
title: "eSATA drive not detected"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by glabouni on 2007-01-13
When i hotplug my eSATA hardrive it is not detected (does not appear in fdisk -l).
It is not detected either when it plugged before booting the computer.

lspci shows
```
04:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)

```

lsmod | grep "sata" returns:
```
sata_sil24             12932  0 
sata_nv                11268  4 
libata                 74892  2 sata_sil24,sata_nv

```

- external drive enclosure ([ONNTO TB-M120]("http://www.onnto.com/pro_product.asp?top_desc=Storage_Enclosure&sec_desc=satapro&thd_desc=TB-M12O"))
- hard drive: [hitachi deskstar T7K500]("http://www.hitachigst.com/portal/site/en/menuitem.f053c8a6f66a6a14e85c1a70eac4f0a0/") 320GB
- motherboard: [ASUS crosshair]("http://www.asus.com/products4.aspx?modelmenu=1&model=1283&l1=3&l2=101&l3=0") bios revision 0401
- eSATA chipset: [Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)]("http://www.siliconimage.com/products/product.aspx?id=32")

The drive is working as it should when plugged using firewire or USB.
The whole reason why I bought this specific hardware was to use eSATA, so I'm disappointed that this is the only thing that is not working. Luckily for me the drive enclosure also provide firewire so I'm still able to use my drive but this is only a backup emergency solution. 

any advice is welcomed.

---

### Post by glabouni on 2007-01-13
I'm a bit concernt about using my drive through firewire as I have some weird stuff happening.

blkid 
```
/dev/sdb1: LABEL="           FAT32   ¾&#9516;&#8800;¬"À&#9500;
                                             V´»" UUID="459E-6E1B" TYPE="&#9524;°&#9618;&#9500;" 
/&#9229;&#9226;&#9524;/&#9149;&#9229;&#9225;5: UUID="1578&#9225;193-9&#9225;7&#9225;-46&#9618;6-8455-21&#9225;74510&#9226;3&#9229;5" SEC_TYPE="&#9226;&#9474;&#9500;2" TYPE="&#9226;&#9474;&#9500;3" 
/&#9229;&#9226;&#9524;/&#9149;&#9229;&#9225;6: UUID="&#9226;&#9228;25&#9229;&#9226;75-&#9228;5&#9225;&#9618;-4135-87°1-8&#9226;&#9229;21330&#9226;&#9225;2&#9225;" SEC_TYPE="&#9226;&#9474;&#9500;2" TYPE="&#9226;&#9474;&#9500;3" 
±&#9148;&#9618;&#9225;@&#9149;&#9618;&#9500;&#9146;&#9148;&#9227;:·$ 
```

[[IMG]http://img186.imageshack.us/img186/5127/screenshot1qq0.th.png[/IMG]](http://img186.imageshack.us/img186/5127/screenshot1qq0.png)

 ls -l /dev/disk/by-uuid 
```
lrwxrwxrwx 1 root root 10 2007-01-13 15:39 1578b193-9b7b-46a6-8455-21b74510e3d5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2007-01-13 15:39 459E-6E1B -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-01-13 15:39 ec25de75-c5ba-4135-87f1-8ed21330eb2b -> ../../sdb6
```

mount
```
/dev/sdb5 on /media/ieee1394disk type ext3 (rw,nosuid,nodev)
/dev/sdb6 on /media/ieee1394disk-1 type ext3 (rw,nosuid,nodev)
/dev/sdb1 on /media/ieee1394disk-2 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
```

fdisk -l
```
Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5768    46331428+   b  W95 FAT32
/dev/sdb2            5769       38913   266237212+   5  Extended
/dev/sdb5            5769       26165   163838871   83  Linux
/dev/sdb6           26166       38913   102398278+  83  Linux

```

---

### Post by glabouni on 2007-01-14
as an interesting followup: 
I've done something, I don't know what though (not sure but could be dmraid or xen), that made my drive detected if it is already turned on and plugged on boot.  

hotplug still doesn't work and the nasty UUID error is still here though.

---

### Post by dannyboy79 on 2007-01-31
i have the sis 180 sata raid ports on my foxconn motherboard and according to a website that talks about the sata_sis driver, it is suppose to support hotswapping esata? but when I plug it in nothing happens? it will work however if tht drive is on and plugged in prior to booting. so what do I need to do to simulate a reboot so that the driver and whatever else gets "triggered" to start? any help would be appreciated. the whole reason I bought this was so I could go back and forth between windows and ubuntu is I needed it. it's a 500GB western digital drive 1.5gb sata. $149.99 from tigerdirect. the enclosure is a Vantec Nexstar-3 with usb and esata.

---

### Post by glabouni on 2007-02-01
I've search the web for info about esata hotplug under ubuntu; it seems others are experiencing the same and I've read a couple times that sata hotplug support was broken in edgy. 

hopefully this will be fixed in an upcoming ubuntu release

---

### Post by Pat Prodanovic on 2007-02-05
> **dannyboy79 said:**
> i have the sis 180 sata raid ports on my foxconn motherboard and according to a website that talks about the sata_sis driver, it is suppose to support hotswapping esata? but when I plug it in nothing happens? it will work however if tht drive is on and plugged in prior to booting. so what do I need to do to simulate a reboot so that the driver and whatever else gets "triggered" to start? any help would be appreciated. the whole reason I bought this was so I could go back and forth between windows and ubuntu is I needed it. it's a 500GB western digital drive 1.5gb sata. $149.99 from tigerdirect. the enclosure is a Vantec Nexstar-3 with usb and esata.

I am using the same enclosure, with a western digital 250GB hard drive. When I plug the eSATA cable into the back of my computer, and restart, I am able to see the device as another hard drive. However, when I try to double click on it, Ubuntu tells me that the drive is not removable---I am not able to see the drive's contents. The only way to go is USB, which is kind of slow.

Can someone suggest how may I use this external drive with eSATA? What should I do differently? Any suggestions would be appreciated.

---

### Post by dannyboy79 on 2007-02-06
well, do you have an entry in your fstab? if not then add one and then just make sure that before you turn on your computer that you have the esata plugged in and it's on. then turn on your computer and it should work fine. mine does. I don't have it mounted automagically because sometimes I have it unplugged or turned off, so I just made the fstab entry noauto and users so that any user can mount it. so I basically made a little script that gets called after bootup that checks for /dev/sdb1 and if it's there, then it performs a sudo mount /dev/sdb1 and all is well. if it's not there, it doesn't attempt to mount it. i did this because I had it automounting at first but one time it wasn't on and when the computer tried to mount it, it freaked out and was at a prompt telling me to either enter the root password for maintenance or to hit ctrl-d I think, and then it would continue to bootup.

---

### Post by Pat Prodanovic on 2007-02-07
Thank you dannyboy79, this solves my problem. After restarting the computer with the drive on, I did 

```
sudo mount -t ext2 /dev/sda /mnt 
```

and the drive automatically appeared.

---

### Post by aurelieng on 2007-03-22
Is there any news about detecting an esata hard disk without doing a cold reboot ?

Right now, the only way to use an esata disk is to have it connected upon boot. Then you can umount it, unplug it and turn it off, but if you then try to mount it while the disk is not connected and turned on anymore (let's say you are a bit clumsy), it just freezes the computer (the /dev/foofar entry of the disk is still present even though it was physically removed).

On my laptop, I can unplug/plug my esata controller to have its list of connected devices refreshed, but on a workstation there's no way to unplug/plug an esata controller :/

Is there a workaround to avoid this freeze ?

---

### Post by dannyboy79 on 2007-03-22
well mine doesn't freeze, but it just doesn't show up? not sure what to do about this as I am new to linux. how come it doesn't use the scsi emulation like usb, cause I can plug in a usb device and it appears. there must be something wrong with hald, I think that's what handles auto  mounting of usb devices? According to this ([http://linux-ata.org/driver-status.html#ahci](http://linux-ata.org/driver-status.html#ahci)) the libata driver has added hotplug as of kernel >= 2.6.18-git5 (i.e. what will be 2.6.19). See that page for supported chipsets. I know Dapper uses 2.6.15 and Edgy uses 2.6.17 I think. You could always compile your own 2.6.20 following this guide ([http://www.ubuntuforums.org/showthread.php?t=311158](http://www.ubuntuforums.org/showthread.php?t=311158))  but make sure you ask someone about compiling in support for hotplug or do you just use libata as a module cause I don't know how compiling works but I am going to compiling a 2.6.20 kernel myself for my Dapper box soon so that I take full advantage of Core 2 Duo and large amount of ram and of course this hotplug. If I find anything out I'll post back about how my kernel compile went and if the hotplug works.


I found this below here ([http://bbs.archlinux.org/viewtopic.php?pid=231386](http://bbs.archlinux.org/viewtopic.php?pid=231386)) but it doesn't solve the issue if you turned on your box with the esata drive disconnected and or turned off?

Hi just having a read of this post and the whole hot swapping issue; I have two SATA II drives in basic hot swap bays; I found a way to 'trick' the system into hot plugging; any gurus out there please tell me if this is bad for the drives if it is; but so far I have not run into a single problem.

I use the package hdparm. (pacman -S hdparm) I know this is a package thats meant to be used with IDE drives but it seems to work fine with me, it essentially lets you control basic hardware functions of the drive making it safe to unplug and plug back in with your machine never thinking the drive was gone. Heres the steps.

Plug in your drive(s), then turn your machine on so the machine detects the drives.
You can mount as you would normally, once your ready to unplug umount the drives.
Run the command hdparm -Y /dev/sdX  this completely turns off and locks the drive so it's safe for removal, but leaves it in mtab.
Remove the drive
When you want to plug it back in just do so and the process of plugging it back in will power it back on, ready to be mounted again; repeat the steps (besides the turning on machine part) again again and again...

---

