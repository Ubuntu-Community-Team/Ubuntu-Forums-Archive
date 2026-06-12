---
title: "Removing Dual Boot"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by epic concept on 2009-09-04
I have recently added a new HDD,  I've transfered all my stuff using Windows XP Is there a way I could install ubuntu without having to format my new HDD?


I've noticed that you don't need to format the partitions if you're creating a dual boot with Windows or whatever, But I've already installed linux twice with a dual boot now I have a list of boot menu's popping up everytime I reboot, Is there a way to remove those entries and recreate a dual boot?

---

### Post by chinmaya_n on 2009-09-04
I'm sorry to say !
you are not clear in your words, can you xplain what do u mean by 
> "Is there a way I could install ubuntu without having to format my new HDD?"

Do u want to install ubuntu in your old hard disk or new !!
Does your new hard disk 've partitions or a single, whole bunched partition ?
Does your system already 've linux ( i mean now presently having linux , b'se u said:*boot menu's popping up everytime I reboot* )

---

### Post by epic concept on 2009-09-05
Okay, I've got 2 Hard drives, a 40 Gig one and a 160 Gig.
I currently have Windows XP and Ubuntu installed on the 40 Gig HDD
and I had installed ubuntu twice so I get 3 different boot options 2 for Ubuntu and 1 for XP, I would like to remove them somehow and be able to reinstall ubuntu only on the 40 Gig Hard Drive. The 160 Gig is formatted in NTFS and I don't want to lose the files on the 160 gig Hard Drive.

What do i do?

---

### Post by chinmaya_n on 2009-09-05
To my knowledge its quite easy (if i've understood u!)

You anyway going to format your old HDD, so install ubuntu only in that HDD in what ever the way you like(create partitions in that HDD as you like)

and if you dont want to loose your Win XP which is already in the old HDD, dont format that partition, leave it as-it-is! (delete the partitions of ubuntu you previously installed)

So in no way you are going to affect your 160 HDD!(you wont loose any data)
To know the partions names for installation process(i mean the partions of 40HDD), use the following commands(in your termial of ubuntu which is already present or use a live cd):
```
$sudo fdisk -l

```the following command shows only the mounted partitions:
```
$sudo mount
```
If you dont understand those outputs post the outputs here. 
ubuntu will automatically detect Your 160HDD!
If you 've any doubts plz let me know with out any hesitation :)

---

### Post by epic concept on 2009-09-05
I want to install Ubuntu on my 40 Gig HDD, (Getting rid of windows for good) however my 160 Gig HDD is formatted as NTFS would it work without formatting the 160 Gig HDD?

---

### Post by Petertje on 2009-09-05
I think i know what you mean. There is some data on the 160 GB drive you want to remain intact, and you want to convert the disk to ext3 or other non-ntfs/fat format. The way i did it was resizing it, copying data to new ext3 partition and resize further until all data is transfered and whole disk is converted in new format.

btw if you want to remove entries from GRUB or want to change settings (10s menu delay etc) do this:
```

sudo nano /boot/grub/menu.lst

```

With Ubuntu graphical install it is easy to delete old windows partition and overwrite it with new ubuntu, and if it is going to be the only OS you'll be running you can select "do not install grub".
I seriously recommend to convert the 160 NTFS disk to ext3 though ;).

I hope i understood you correctly, good luck :)

---

### Post by epic concept on 2009-09-05
I didn't really understand that part how do I format the 160 Gig to a ext4 or 3?

---

### Post by Hobgoblin on 2009-09-05
> **epic concept said:**
> I want to install Ubuntu on my 40 Gig HDD, (Getting rid of windows for good) however my 160 Gig HDD is formatted as NTFS would it work without formatting the 160 Gig HDD?

Yes.

Just boot from the Ubuntu CD, use partition manager to delete all partitions on the 40GB drive. Then run the Ubuntu installer and tell it to use that drive.

---

### Post by chinmaya_n on 2009-09-05
Dont bother!

Nothing will happent to your 160HDD, if you format the 40HDD. Ubuntu will automatically detect the 160HDD and show the partitions of it in "PLACES" and 'COMPUTER'.

You are anyway getting rid of WINDOWS!! ( good :))
So directly keep the cd in cdrom and boot. Then install in the 40HDD. Plz be careful before you select or delete the partitions during installation. I already insisted some commands.... try them if you want know on which partitions you 've to do your operations!

NTFS to EXT3:
what Mr.Petertje saying  is copy all your data to some or the other HDD (say your 40HDD after or before installing) then delete the old partitons and convert to ext3 using partition editor(gparted). Then after conversion copy the old data from 40HDD to new HDD!
But i dont know how to convert NTFS to EXT3 directly with the data intact!! (i mean if your data in 160HDD is more than 40HDD you can not do the previous copying method)

If still 've any doubts dont hesitate to post:P

---

### Post by epic concept on 2009-09-07
Okay so that answers my question I can format the 40 gig one without touching the 160 Gig HDD, now how would I know if I'm not formatting the 160 Gig HDD would it show up separately during the install?

I really can't afford to lose any data on 160 Gig.

---

### Post by crownedzero on 2009-09-07
When you reboot with the Ubuntu iso go through the motions. I'm assuming you are using a graphic installer. Once you get the the partitions portion it will give you an 'expert' option. this will display your drives and the partitions on them. If I recall correctly it will even give you the option to choose a single disc(it will show the size) and install to entire disc. Just double check the partitions and don't hit 'Next' til you are sure you've done it right. It will even setup a swap root and home directory on the disc.

---

### Post by chinmaya_n on 2009-09-07
to know on  which partitions you 've to install ubuntu, use this command in the terminal:
```
$sudo fdisk -l
```

the output of this command looks like this
```
Disk /dev/sda: 320.0 GB[COLOR="Red"](this is my HDD)[/COLOR], 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0aaf0aaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3315    26627706    7  HPFS/NTFS
/dev/sda2            3316       34050   246878887+   f  W95 Ext'd (LBA)
/dev/sda3           34051       38913    39062047+  83  Linux
/dev/sda5            3316        9689    51199123+   7  HPFS/NTFS
/dev/sda6            9690       22437   102398278+   7  HPFS/NTFS
/dev/sda7           22438       28811    51199123+   7  HPFS/NTFS
/dev/sda8           28812       33214    35367066    7  HPFS/NTFS
/dev/sda9           33215       34050     6715138+  82  Linux swap / Solaris

Disk /dev/sdb: 4016 MB[COLOR="Red"](this is my pendrive 4GB)[/COLOR], 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders
Units = cylinders of 2250 * 512 = 1152000 bytes
Disk identifier: 0x000a3d2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           4        3487     3917824    b  W95 FAT32

```

Thus you will be specified your both HDD's with sizes. Now remember the name of yur 40Gig HDD . 
[COLOR="Blue"]Eg:[/COLOR] 320HDD- /dev/sda and 4GB pendrive- /dev/sdb1

Remember that /dev/sda* (i'e /dev/sda1,2,3.. ) are partitions of the same HDD. So while installing you 've to delete all the partitions on that HDD and create partitions as you like!! You anyway know how to install ubuntu ( you said ... "i installed ubuntu twice" ) If you 've doubt just google it! Mark  the expert option, as Mr.crownedzero said!!

[COLOR="DarkRed"]NOTE:[/COLOR]If you 've doubt cancel the installation at any time before 7th step!!
Don't be lenient, you may loose your data!!

---

### Post by chinmaya_n on 2009-09-10
When you are finished with the thread... dont 4get to mark it "solved"

"Threadtools > Mark this thread as solved"

---

### Post by epic concept on 2009-09-12
Thank you guys. :) < Happy Linux User. Lol

---

