---
title: "Cannot alter files on USB HDD"
date: 2008-12-25
forum: Hardware
---

### Post by AuronGrande on 2008-12-25
For some reason, I cannot make any alterations to anything on my USB hard drive. The permissions are fixed at read-only.

I have tried altering the permissions, but it says that I cannot change access permissions on a read-only file system. The format is the default FAT32 that you get whenever you buy a USB hard drive.

I use this hard drive for important backups of data. How can I change the permissions so that I can make alterations?

---

### Post by AuronGrande on 2008-12-25
I did a google search for this problem and found that I am definately not alone, but all the solutions that I found just don't want to work.

The site is this one [http://ubuntuforums.org/showthread.php?t=515084]("http://ubuntuforums.org/showthread.php?t=515084")

Upon doing a dmesg in the terminal, here is the chunk at the very end which I think refers to my USB hard drive (sorry it's a bit long, but that's as it shows, copy and pasted. Before that is just a repeat.);

> [11545.857267] usb 2-2: USB disconnect, address 2
[11564.696016] usb 2-2: new high speed USB device using ehci_hcd and address 5
[11564.830108] usb 2-2: configuration #1 chosen from 1 choice
[11564.836335] scsi9 : SCSI emulation for USB Mass Storage devices
[11564.836597] usb-storage: device found at 5
[11564.836598] usb-storage: waiting for device to settle before scanning
[11569.836920] usb-storage: device scan complete
[11569.839025] scsi 9:0:0:0: Direct-Access     WD       5000AAC External 1.65 PQ: 0 ANSI: 4
[11569.840327] sd 9:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[11569.843609] sd 9:0:0:0: [sdb] Write Protect is off
[11569.843616] sd 9:0:0:0: [sdb] Mode Sense: 21 00 00 00
[11569.843618] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[11569.849283] sd 9:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[11569.855146] sd 9:0:0:0: [sdb] Write Protect is off
[11569.855154] sd 9:0:0:0: [sdb] Mode Sense: 21 00 00 00
[11569.855156] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[11569.855502]  sdb: sdb1
[11569.864954] sd 9:0:0:0: [sdb] Attached SCSI disk
[11569.865069] sd 9:0:0:0: Attached scsi generic sg2 type 0
[11619.080544] FAT: Filesystem panic (dev sdb1)
[11619.080551]     fat_get_cluster: invalid cluster chain (i_pos 0)
[11619.080554]     File system has been set read-only
[11619.080675] FAT: Filesystem panic (dev sdb1)
[11619.080676]     fat_get_cluster: invalid cluster chain (i_pos 0)
[11619.088115] FAT: Filesystem panic (dev sdb1)
[11619.088123]     fat_get_cluster: invalid cluster chain (i_pos 0)
[11623.679061] FAT: Filesystem panic (dev sdb1)
[11623.679068]     fat_get_cluster: invalid cluster chain (i_pos 0)
[19436.479383] FAT: Filesystem panic (dev sdb1)
[19436.479390]     fat_get_cluster: invalid cluster chain (i_pos 0)
[19436.480703] FAT: Filesystem panic (dev sdb1)
[19436.480710]     fat_get_cluster: invalid cluster chain (i_pos 0)
[19436.485371] FAT: Filesystem panic (dev sdb1)
[19436.485376]     fat_get_cluster: invalid cluster chain (i_pos 0)

I tried to do the fsck but it just doesn't want to work. I have tried > fsck.vfat -t -r /dev/sdb1 but it comes up > auron@auronlinux:~$ fsck.vfat -t -r /dev/sdb1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open /dev/sdb1: Permission denied

However, I know not what that command would do anyway. All I need is to be able to backup files to my USB hard drive.

---

### Post by AuronGrande on 2008-12-26
This is an extension from my thread [http://ubuntuforums.org/showthread.php?t=1021221]("http://ubuntuforums.org/showthread.php?t=1021221") which no-one has replied to, but now the problem is more serious and I am desperate for a solution, hence this new thread.

The HDD is formatted in the original FAT32 file system as I have not reformatted it ever. However, after mentioned in the other thread, I can no longer use the drive on a Windows machine. Windows comes up saying that it's installed the new hardware, but it cannot access the drive to view the contents.

This is an important drive with well over 200GB of important data on it which I regularly update. I can only access the drive as read only in Ubuntu 8.10.

Can anyone help?

---

### Post by dmizer on 2008-12-26
Merged your threads. It's probably the same problem with an additional symptom.

1) Don't panic. Seriously, if you try something you don't completely understand in a bid to regain access, you're more likely to break things and/or loose data.
2) If you need urgent and immediate help, ubuntu IRC is a better idea than to post in the forums: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)

I suggest you try a different USB carrier. Your current one could be damaged in some way.

---

### Post by AuronGrande on 2008-12-26
I haven't a clue how the posts have merged, but it's too late to worry about that now.

What do you mean by a different USB carrier?

---

### Post by ianhaycox on 2008-12-26
I've had similar problems with USB keys if they are not unmounted cleanly. My fix was to insert the USB key into a windows machine, check the the files are OK, then use the 'Safely remove' option. Reinserting into a Linux box and everything was OK. I know you said Windows couldn't read the files but it's worth a try.

I'm guessing from your dmesg output that something similar is happening.

If you haven't got a spare Windows machine then you could re-try your fsck command with sudo preprended AFTER copying all the data somewhere else whilst in READ-ONLY mode. However, I can't guarantee that your data won't get trashed by fsck, so be careful.

---

### Post by dmizer on 2008-12-26
> **AuronGrande said:**
> I haven't a clue how the posts have merged, but it's too late to worry about that now.

What do you mean by a different USB carrier?

I merged them. :)

You said you have a USB HDD. I assume that means that you have a largish device with an actual ide hard drive inside a box (or carrier) which you can plug into any computer via USB cable. Like this: [http://www.it-reality.co.uk/Reviews/ExternalDriveBox/CloseUp2.jpg](http://www.it-reality.co.uk/Reviews/ExternalDriveBox/CloseUp2.jpg)

If that is not the case, then I've misunderstood.

If that is the case, then try a different cable or carrier (they're fairly cheap)

---

### Post by AuronGrande on 2008-12-26
> I've had similar problems with USB keys if they are not unmounted cleanly. My fix was to insert the USB key into a windows machine, check the the files are OK, then use the 'Safely remove' option. Reinserting into a Linux box and everything was OK. I know you said Windows couldn't read the files but it's worth a try.

Yeah, I tried to connect it to a windows setup to run it's scandisk program on the drive. However, the drive wouldn't show in "My Computer". The darn thing also locked up the machine. Took a few forced resets (pressing the reset button on the case) before it finally got back onto the desktop.

> I'm guessing from your dmesg output that something similar is happening.

From what I gather, there is at least 1 corrupt file/folder on the drive because until I access a certain folder, I can actually write stuff to the drive. After opening or even highlighting that folder, Linux only allows read only. To get that full access I unplug the drives USB cable and plug it back in.

> If you haven't got a spare Windows machine then you could re-try your fsck command with sudo preprended AFTER copying all the data somewhere else whilst in READ-ONLY mode. However, I can't guarantee that your data won't get trashed by fsck, so be careful.

Sadly, this is a no go. I have nowhere to transfer all the data too. The hard drive in the machine is 200GB tops with about 15GB used up by Ubuntu and any programs I have installed. The amount of data on the external drive is about 230GB out of 500GB capacity.

I can probably get a new USB hard drive with the same capacity for about £50 plus p&p, but it will take several months before I can order one. Is there anything else you can suggest?

---

### Post by AuronGrande on 2008-12-26
Re: dmizer
> I merged them.

I thought someone might have done that, or there was a glitch in the system.

> You said you have a USB HDD. I assume that means that you have a largish device with an actual ide hard drive inside a box (or carrier) which you can plug into any computer via USB cable. Like this: (link removed)

If that is not the case, then I've misunderstood.

If that is the case, then try a different cable or carrier (they're fairly cheap)

Sadly no, it's this drive; [http://www.wdc.com/en/products/products.asp?driveid=351]("http://www.wdc.com/en/products/products.asp?driveid=351")

I cannot find how to get into it to get the drive out to try directly in a computer. However, in doing so, I may cause more harm to it than good, as the casing may end up shattering. It looks like the casing is clipped in place, and not knowing where the clips are, which may or may not be the reusable clips, I could end up snapping the clips.

---

### Post by AuronGrande on 2008-12-27
If I got a new USB HDD, would the same problem occur if I connected it to my machine with Ubuntu and copied the files over?

If not, then I'd have to buy a deck of 100 blank DVDs and do it the hard way. Even though we've got a router, the darn thing won't allow any computers to see each other through it (the dreaded BT HomeHub 2), and using a crossover cable is a no-go as well. Shame.

---

### Post by dmizer on 2008-12-28
> **AuronGrande said:**
> If I got a new USB HDD, would the same problem occur if I connected it to my machine with Ubuntu and copied the files over?

If not, then I'd have to buy a deck of 100 blank DVDs and do it the hard way. Even though we've got a router, the darn thing won't allow any computers to see each other through it (the dreaded BT HomeHub 2), and using a crossover cable is a no-go as well. Shame.

Is the device still under warranty by any chance? Although, you may damage the device by pulling it apart, it may be the only option you have for recovering your data.

FYI: [http://datacent.com/datarecovery/hdd/western_digital/WDH1U5000](http://datacent.com/datarecovery/hdd/western_digital/WDH1U5000)

And here: [http://www.carltonbale.com/2008/01/western-digital-my-book-opening-the-case-removing-the-drive/](http://www.carltonbale.com/2008/01/western-digital-my-book-opening-the-case-removing-the-drive/)

---

### Post by AuronGrande on 2008-12-28
> Is the device still under warranty by any chance? Although, you may damage the device by pulling it apart, it may be the only option you have for recovering your data.

I've had it for over a year now, so I haven't a clue on the warranty.

> FYI: [http://datacent.com/datarecovery/hdd...ital/WDH1U5000](http://datacent.com/datarecovery/hdd...ital/WDH1U5000)

I wouldn't be too surprised if the drive is building up to this. We have a problem with a house electrics which the council who owns the house won't sort out. The mains supply causes steady damage to anything and everything in the house. I've had 2 pairs of computer speakers blow up on my desk. (The desk now has burnt marks to prove it). Also the main TV has had to be repaired twice now in another room. I've also had to replace the PSU in this computer, but that was down to the fan inside it dying.

I guess I better replace the USB HDD ASAP.

---

### Post by dmizer on 2008-12-28
If you are damaging hardware because of bad mains, I highly suggest investing in a battery backup. It's a bit pricey, but nothing compared to loosing data.

---

### Post by Rohan Kapoor on 2008-12-29
Bad mains... Ouch. You could also try getting a surge protector with your UPS.

---

### Post by dmizer on 2008-12-29
> **darth-vader said:**
> Bad mains... Ouch. You could also try getting a surge protector with your UPS.

Most (if not all) battery backups perform both dip and surge protection.

---

### Post by AuronGrande on 2008-12-29
I did look into a UPS not so long ago. Sadly, there is none that I can find that provides the correct sockets to plug my computer into. They're either like the connections where the power lead connects into the computer PSU or a straight up socket of the wrong type. In the UK they use the 3-point sockets at 230V. The ones I found are the European connections of either 2-point, or the wrong shape 3-point.

We have heavy duty surge protectors in every room of this house, and they don't help. Surge protectors protect against electrical spikes, not electrical noise. It's like sugar or bleach in a cars oil supply. Eventually it wears the appliances down.

I have ordered a new USB HDD with a deck of 100 DVDs. It's going to take me quite a while to put all the data onto the DVDs for transferring onto the new drive.

Sadly, I will be leaving Linux back to the awful Microsoft when that's done.

---

### Post by Rohan Kapoor on 2008-12-29
Ah okay I see. Why would switching back to M$ help you at all?

---

### Post by AuronGrande on 2008-12-30
For one, it'd make things easier for me.

When it comes to Linux, fglrx doesn't like my Radeon X1950 Pro, Linux doesn't really support surround sound except for when a game can handle surround, or when playing something like a DVD which never seems to play well. There's my keyboard not being supported when everywhere I look on the internet says that it should, and the right-click on my mouse software wise is extremely annoying.

I love Linux, but there's so many incompatibilities. Perhaps in a few more years I look into returning. As time goes by, Linux becomes better and better. Last time I tried Linux, I tried Ubuntu 6.x, can't remember which one.

---

### Post by Rohan Kapoor on 2008-12-30
Ah allright, well we'll miss you so come back soon!

---

### Post by AuronGrande on 2008-12-30
Well, this will probably be my final response to this thread. I am writing this as a final note so to speak.

I have received my new USB HDD which is a Buffalo DriveStation Turbo USB with Power Saving Mode at 500GB. [http://www.buffalo-technology.com/products/external-drives/drivestation/drivestation-turbousb-with-power-saving-mode/]("http://www.buffalo-technology.com/products/external-drives/drivestation/drivestation-turbousb-with-power-saving-mode/")

I first tested it on the windows machine and it works fine, then plugged it into Linux and everything was fine. So I copied almost every files/folders straight over from the Western Digital MyBook drive to the Buffalo. The only files that wouldn't transfer were the ones where I had a backup of my Thunderbird Profile. That's no biggy as I simply copied my most recent one from the /home/aurongrande/.mozilla-thunderbird directory after getting Thunderbird to compact the folders to prevent a problem that I can't remember later on when reinstalling the backup into the program.

Other than that, everything went smoothly, taking almost 4 hours to transfer the data. Then, I retried the Buffalo drive in the windows machine. No problems, it's recognised and I could browse the drive.

Now then, once I have reinstalled the awful Vista, I will see if I can rescue the WD MyBook by redoing the partition on it. If I can, that's a bonus, increasing my USB HDD storage to 1TB and be able to spread my data and backups. Important data on one drive, none important on the other.

Thank you for your help folks. You may see me again in a few years when I retry Linux.

---

### Post by Rohan Kapoor on 2008-12-30
BTW: Ubuntu can manage partitions as well. GO to System-Administration-Partition Editor

---

### Post by tghe-retford on 2008-12-30
[QUOTE=AuronGrande]I wouldn't be too surprised if the drive is building up to this. We have a problem with a house electrics which the council who owns the house won't sort out. The mains supply causes steady damage to anything and everything in the house. I've had 2 pairs of computer speakers blow up on my desk. (The desk now has burnt marks to prove it). Also the main TV has had to be repaired twice now in another room. I've also had to replace the PSU in this computer, but that was down to the fan inside it dying.[/QUOTE]
[QUOTE=AuronGrande]We have heavy duty surge protectors in every room of this house, and they don't help. Surge protectors protect against electrical spikes, not electrical noise. It's like sugar or bleach in a cars oil supply. Eventually it wears the appliances down.[/QUOTE]

Reading up on some sources on electrical noise, if you are correct (for the benefit of other forum members, I personally know this user), then reinstalling Vista may be the least of your problems and won't fix any problems with your USB HDD, if as you fear, the electrical supply in your house has steadily damaged it in the same way as your other equipment. Reading up on articles I could find from the Internet, you need to find the source of where the noise is coming from and isolate it. If it is something the council is responsible for, contact them as they are duty bound to fix it, particularly if it is damaging equipment.

You may be better off asking on a specific forum who know about how electric works or to an electrician as to why your equipment is getting damaged. Good luck.

---

