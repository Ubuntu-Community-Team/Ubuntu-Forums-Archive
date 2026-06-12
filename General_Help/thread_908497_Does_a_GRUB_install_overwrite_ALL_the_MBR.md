---
title: "Does a GRUB install overwrite ALL the MBR?"
date: 2008-09-02
forum: General Help
---

### Post by Telémakhos on 2008-09-02
Hi all, I think I've a virus in the MBR. I've a triboot system and I've formatted with gparted and reinstalled winXP which is in the first partition but the worm still remains there.

My question is. If I reinstall ubuntu will grub delete all the MBR?
Anyone knows another options?

Thnx

---

### Post by oilchangeguy on 2008-09-02
> **Telémakhos said:**
> Hi all, I think I've a virus in the MBR. I've a triboot system and I've formatted with gparted and reinstalled winXP which is in the first partition but the worm still remains there.

My question is. If I reinstall ubuntu will grub delete all the MBR?
Anyone knows another options?

Thnx

first, you "think" but don't know for sure if you have a virus. what has made you think you might have a virus in such a strange place as the master boot record?

---

### Post by Telémakhos on 2008-09-02
Well, I would tell you all the story but the mods have deleted my first post... to sum up: in my XP partition Spybot S&D detected the well known trojan/worm '**[Agobot]("http://en.wikipedia.org/wiki/Agobot_(computer_worm)")**' trying to add an entry to the registry. My antivirus (AVG) didn't detected it after a scan. Then I tried to connect to Kaspersky online scanner and... oh! Kaspersky webpage doesn't load! Neither viruslist.com nor sophos.com, etc...

Now take a look at one of the symptoms of this worm:

> The worm blocks access to security-related websites by adding the following 
entries to the Windows hosts file: 
127.0.0.1 [www.symantec.com](www.symantec.com)
127.0.0.1 securityresponse.symantec.com
127.0.0.1 symantec.com
127.0.0.1 [www.sophos.com](www.sophos.com)
127.0.0.1 sophos.com
127.0.0.1 [www.mcafee.com](www.mcafee.com)
127.0.0.1 mcafee.com
127.0.0.1 liveupdate.symantecliveupdate.com
127.0.0.1 [www.viruslist.com](www.viruslist.com)
127.0.0.1 viruslist.com
127.0.0.1 viruslist.com
127.0.0.1 f-secure.com
127.0.0.1 [www.f-secure.com](www.f-secure.com)
127.0.0.1 kaspersky.com
127.0.0.1 [www.avp.com](www.avp.com)
127.0.0.1 [www.kaspersky.com](www.kaspersky.com)


Well, after I formatted NTFS and FAT32 partitions with gparted and reinstalled 2 times my XP the problem still remains, have no access to that domains... why? In ubuntu (same box , another partition) or using a webproxy I can access without troubles... It's weird. 

I've more partitions: 

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36eb36ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19581   157284351    7  HPFS/NTFS
/dev/sda2           19582       39162   157284382+  af  Unknown
/dev/sda3           39163       41773    20972857+  83  Linux
/dev/sda4           41774       60801   152842410    5  Extended
/dev/sda5           41774       56133   115346668+  83  Linux
/dev/sda6           56134       60801    37495678+   b  W95 FAT32


So, there are 2 probabilities:

1.- The worm has replicated itself to another EXT3 partition (very weird) 
2.- The worm has replicated itself to the MBR (more probably)

What do you think? Another options? I need advice

---

### Post by caljohnsmith on 2008-09-02
I personally don't think it's too plausible that the worm is in your MBR, because for one thing the boot loader part of MBR itself is only 446 bytes. It would be difficult to hide a worm in only 446 bytes, but it could link to other code that they hide in the first track of your HDD I guess. But anyway, if you want to make sure you've wiped it clean, just boot your Windows Install CD, go to the recovery console, and run "fixmbr". That replaces whatever boot loader is in the MBR with the Windows XP one.

---

### Post by luvr on 2008-09-02
> **Telémakhos said:**
> Anyone knows another options?
If you really, *really,* **really** want to make sure that the MBR is gone, plus anything that may be hiding in the space immediately following it, **and** if you don't mind losing all data on the disk, then you could overwrite the first few sectors with all null bytes:
```
dd if=/dev/zero of=/dev/*hdx* bs=512 count=2048
```(where *"hdx"* designates the disk--e.g., "hda," "sda," etc.).

This command will write null bytes (read from the */dev/zero* input source) to the harddisk; it will actually write 2048 blocks (as specified by the *count* argument), of 512 bytes each (as specified by the *bs* argument--which stands for *"blocksize"*). In short, it will clear the first megabyte of the disk.

Again, do keep in mind that **anything** that was on the disk will be **lost** after you execute the command; the disk won't even contain a valid partition table--not even an *empty* one. (The *"dd"* command means something like *"dump data,"* but because it is so destructive, it is sometimes called *"destroy disk"* instead.)

To write a new, empty, partition table to the disk after you *"destroyed"* it, you will have to run the *fdisk* command:
```
fdisk /dev/*hdx*
```The *fdisk* command will complain about an invalid partition table; just do a **w** (*"write"*) to reinitialise the partition table, and, consequently, end up with a completely empty disk--just like new. *(Of course, the data after the first megabyte is still physically there, but there's no longer any way to **logically** access it.)*

(Remember that the *"dd"* and *"fdisk"* commands have to be run by the *root* user, so you will likely have to prepend them with **sudo.**)

---

### Post by Derp on 2008-09-02
Have you tried opening %systemroot%\system32\drivers\etc\hosts (with a text editor of your choice) and seeing if those websites are in there?

---

### Post by Telémakhos on 2008-09-02
> **Derp said:**
> Have you tried opening %systemroot%\system32\drivers\etc\hosts (with a text editor of your choice) and seeing if those websites are in there?

Yes, I do. However its empty... 

I like the luvr option. It's a fresh install so nothing its configured.. I'm gonna trying it 

(sorry i'm a bit paranoic with this issues)

Thanx

---

