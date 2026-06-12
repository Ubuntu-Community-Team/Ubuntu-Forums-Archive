---
title: "External Hard Drive and Ubuntu"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by alvarez1900 on 2008-01-03
I have read every post about ubuntu and eSATA and most have got their drives going however my situation is a bit unique. I am using a PCM-ES2 PCMCIA eSATA card that does show up in Hardware Information. However using the fstab command and partition manager my external hard drive does not show at all.

 In Windows it pops right up, however nothing happens whatsoever in ubuntu on connect or from fresh boot or restart. 

 Any ideas of where to start? It is very frustrating having to boot into windows to transfer files over then reboot to ubuntu. I am a guitar teacher and use ubuntu in my lessons a lot now that I have guitar pro and all my audio apps running well. However it can be embarrassing when they ask me why I have to boot to windows for certain files. In all other areas I have all my students extremely interested in finding out what ubuntu is all about hehehe.

---

### Post by alvarez1900 on 2008-01-04
any guesses?

---

### Post by alvarez1900 on 2008-01-04
is there something I can do to check if the hard drive is recognized at all and maybe not mounting?

---

### Post by talkingwires on 2008-01-04
> **alvarez1900 said:**
> is there something I can do to check if the hard drive is recognized at all and maybe not mounting?Boot your system, plug in your drive, and run:```
dmesg | tail
```If nothing else, the output will help you refine your search and get some help. I wish I could help more, but I'm still stuck in PATA/USB1.1 land. :(

---

### Post by dannyboy79 on 2008-01-04
on feisty esata hot plugging wasn't working. I can't speak for gutsy. But I have to have the esata drive enclosure ON and connected prior to even turning on the computer. So, turn computer off, plug in esata drive, power it on, then turn on computer and then post the output of dmesg.

you can issue this command to see all hard drives and each of the hard drives partitions.

sudo fdisk -l

---

### Post by alvarez1900 on 2008-01-05
[   33.104919] Bluetooth: RFCOMM TTY layer initialized
[   33.104924] Bluetooth: RFCOMM ver 1.8
[   37.389818] NET: Registered protocol family 10
[   37.390047] lo: Disabled Privacy Extensions
[   37.390752] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.390888] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   67.323230] NET: Registered protocol family 17
[   70.640065] ieee80211_crypt: registered algorithm 'WEP'
[   70.739335] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   85.251431] eth1: no IPv6 routers present

---

### Post by alvarez1900 on 2008-01-05
I did the fdisk from another thread and it looks as if the external is not showing at all.. I have tryed from fresh boot and hot plugging as I mentioned in the OP.

here is the fdisk result though, I see both my laptops drives but not the 500gig external at all.

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa36cd64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          65       12200    97482388+   7  HPFS/NTFS
/dev/sda2           12201       13985    14338012+  83  Linux
/dev/sda4               1          64      514048+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3e15a8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

---

### Post by alvarez1900 on 2008-01-08
Does that help any at all?

---

### Post by dannyboy79 on 2008-01-08
well if you say that your laptop has 2 hard drives than I would say that's weird unless that's a usb disk? I definitely don't see the 500gb there that's for sure!
 my sata chipset is a VIA on an ASRock motherboard. which sata chipset do you use and is the module  getting loaded?

what does this return?

lsmod | grep sata

you can see what mine returns below.
sata_via               12548  2
libata                125720  2 sata_via,ata_generic

you can find out by issuing 

lspci

to see what ide/sata controllers are in your computer.

---

### Post by alvarez1900 on 2008-01-09
sata_inic162x          14980  0 
libata                138928  4 sata_inic162x,ata_piix,ahci,ata_generic

( However currently the external Harddrive is not plugged in. ) I will plug it in, in a second and repost the results.

 I am guessing the inic162x is the PCMCIA card (PCM-ES2 kingwin eSATA card) like i said earlier in my post in hardware information the PCM-ES2 shows up correctly just like in windows as INI-1623 PCI SATA-II Controller which is by the Initio Corporation.

 The problem is the HD is not showing from there.

07:00.0 SATA controller: Initio Corporation INI-1623 PCI SATA-II Controller (rev 02) is the result os LSPCI command.

---

### Post by dannyboy79 on 2008-01-09
let me see the entire dmesg output. paste it at pastebin.com and then paste the link here that way it doesn't take up tons of room.

I see that the modules are loading, but I can't see if there are any errors in your dmesg after bootup regarding any pcmcia problems. I didn't know that you were talking about a pcmcia card.

also, just to note, make sure that the hard drive enclosure is on and plugged in before you even turn the computer on. then ouput the dmesg like I asked for. I may or not be able to help you from there.

---

### Post by alvarez1900 on 2008-01-10
[http://pastebin.com/m1ef39685](http://pastebin.com/m1ef39685)

thats with the drive plugged in.

---

### Post by dannyboy79 on 2008-01-10
i need the entire dmesg ouput not only the tail of it. as I said, turn off computer. turn on sata hard drive enclosure, plug it into computer. then turn on computer. then first thing you do is issue

dmesg

and paste teh output. also do this again

sudo fdisk -l

and

lsmod | grep sata

as well. thanks. I hopefully can help but not until I see all that output.

---

### Post by alvarez1900 on 2008-01-11
[http://pastebin.com/m2f1c4e77](http://pastebin.com/m2f1c4e77)

 You have already helped me learn some commands for some diagnosis. I am sure these commands will come in handy for me on later hardware issues I might face. So thank you!

---

### Post by alvarez1900 on 2008-01-11
[   26.676652] sata_inic162x: probe of 0000:07:00.0 failed with error -22

 that stood out to me. Now to find out what error -22 is.

---

### Post by dannyboy79 on 2008-01-11
yeah, this doesn't look good. I gogled sata_inic162x: failed with error -22 and found some info on this module. It's fairly new and the hardware controller is, per the things I read, not a very compatible sata controller. I can't help anymore as I don't know how to apply patches, read code or anything high up like that. Either wait for someone else to help, maybe you could contact either of the guys working on this module ([http://www.mail-archive.com/linux-ide@vger.kernel.org/msg13154.html](http://www.mail-archive.com/linux-ide@vger.kernel.org/msg13154.html)) or get a new pcmcia sata controller. good luck

---

### Post by matvrix on 2008-06-17
I have the same exact problem. Hate to say this, but, having installed the Kingwin PCM-ES2 Driver on windoz I could connect to the external contraption. 
I'm missing crucial bit here.. However, I use Suse x64.  Any tips and ideas to get this working ?

>>lspci :
16:00.0 SATA controller: Initio Corporation INI-1623 PCI SATA-II Controller (rev 02)

[COLOR="Red"]>>dmesg| grep error :
rtc_cmos: probe of 00:07 failed with error -16
sata_inic162x: probe of 0000:16:00.0 failed with error -22
[/COLOR]

>>lsmod | grep sata :
sata_inic162x          29828  0
libata                166800  4 sata_inic162x,ata_generic,ata_piix,ahci

Any advice greatly received!
John

---

