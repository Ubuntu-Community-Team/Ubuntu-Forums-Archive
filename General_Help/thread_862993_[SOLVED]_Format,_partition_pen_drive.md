---
title: "[SOLVED] Format, partition pen drive?"
date: 2008-07-18
forum: General Help
---

### Post by Spaceman9 on 2008-07-18
Can I use Gparted to partition and format an 8GB pen drive? What should I format it with...ext3, fat 16, fat 32, ntfs? I'm only going to use it with linux. I want to use it for backing up data files. Thankx for any help.

---

### Post by mcduck on 2008-07-18
Yes, you can. First disable the autonmounting of removable drives (as you can't edit mounted partitions). Then plug the drive in and do what you want with gParted. When youa re done you can enable the automounting again.

If you are only going to use it with Linux go for some native Linux filesystem. That way all ownerships and permissions of files will stay intact when you make the backup (FAT and NTFS are not able to handle Linux-style ownerships & permissions). Ext3 would be a good choice.

By the way, whatever file system you chooce, I recommend setting the label for the drive/partition. This way it will always be mounted with the same name and into same place in your file system when you plug it in.  For Ext2/Ext3 filesystems the comamnd for setting the label is "sudo e2label /dev/YOURDEVICE LABEL" (change the device to right one, and label to whatever you want..

---

### Post by kpkeerthi on 2008-07-18
Use ext3 if you are going to use it with only linux. If you want to share it with   non-linux OSes, use FAT32.

You can use gparted to format the pendrive. Boot with Ubuntu live CD and type gparted (or choose Disks & Partitions from Admin Menu). 

There is an option to set the disk label in gparted itself. To set from  command line, see [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by Spaceman9 on 2008-07-18
Thankx mcduck. You live in the country that invented linux...cool. No wonder you know about this linux stuff.


Thankx kpkeerthi. The link really helps.

---

### Post by danwood76 on 2008-07-18
Hehe, the country didnt invent linux ;)

BTW I wouldnt backup data to a flash drive, they have a high chance of failing way before a (USB) hard disk would fail with a similar amount of read and writes.
This is just my opinion, it depends how often you are going to backup and how much that data means to you.

---

### Post by Spaceman9 on 2008-07-18
danwood76, Linus Torvalds, invented linux whilst working at the Department of Computer Science at the University of Helsinki. Helsinki is the capital of Finland. So, it's not grammatically nor factually incorrect to say that mcduck is from the country that invented linux. 'Tis just a saying.

How I Invented Linux [http://www.madpenguin.org/cms/?m=show&id=1800](http://www.madpenguin.org/cms/?m=show&id=1800)

Who wrote Linux? I did! No, Harry did! Or was it the monkey? [http://searchenterpriselinux.techtarget.com/news/column/0,294698,sid39_gci969455,00.html](http://searchenterpriselinux.techtarget.com/news/column/0,294698,sid39_gci969455,00.html)


If you wouldn't use a flash drive for backing up data what do you use a flash drive for? I do have a hard drive I back up my data to and I also back it up to cd-rw's. 

I was thinking of using the flash drive for trying out new distros, but I don't seem to be able to get my head round it and I make a right dogs dinner of it.

NB I looked at Pendrivelinux.com, but they don't have instructions for the distros I want to install to a flash drive.

---

### Post by danwood76 on 2008-07-19
Flash drives are good for transfering data quickly from one PC to another.
I generally use flash when installing windows so I have the drivers on hand to get the internet working, also use it for transfering work that I want to take to another PC.

I also use flash memory a lot in the work I do for storing variables from microcontrollers (also for storing the program memory on the micros).
But its not something you want to write to constantly as the memory blocks break after around 100,000 write cycles. (dont ask me why you would every want a solid state hard disk in a laptop)

Search google for instructions on installing different distros to pen drives, there are countless numbers of guides on there.

---

### Post by mcduck on 2008-07-19
> **Spaceman9 said:**
> Thankx mcduck. You live in the country that invented linux...cool. No wonder you know about this linux stuff.


Thankx kpkeerthi. The link really helps.

Bwahahahah. Even the Freeciv game describes Finland's main exports as "Mobile phones and premium quality operating systems" ;) I actually think that Linux doesn't come from any single country, mainly because both the kernel developers and all the people who help to make it usable OS live all around the world..

Anyway, I'm glad if I could help. :) And I actually prefer using a removable hard disk for my backups. I only connect it to my computer when making the backup, to avoid the nasty possibility of power source failure destroying both the main hard disk _and_ the backup drive at the same time.

Depending on how large amounts of data you need to backup (and how often) either external drive, or one with internal docking bay, would be a good choice. I work a lot with multimedia and video stuff so the backups are very large, but I also need to be able to access the drive with my laptop, so I bought myself external hard disk enclosure that works both with a 5,25" internal docking bay (connected through SATA-2) and as external drive connectable with both USB2 and eSATA. The enclosure & docking bay were about 30€ and a 350GB 2,5" drive was a bit less than 100€. Definitely worth the money, and most likely same hardware will cost a lot less where you live.. (Finland is _very_ expensive country..)

---

### Post by Spaceman9 on 2008-07-19
> **danwood76 said:**
> Flash drives are good for transfering data quickly from one PC to another.
I generally use flash when installing windows so I have the drivers on hand to get the internet working, also use it for transfering work that I want to take to another PC.

I also use flash memory a lot in the work I do for storing variables from microcontrollers (also for storing the program memory on the micros).
But its not something you want to write to constantly as the memory blocks break after around 100,000 write cycles. (dont ask me why you would every want a solid state hard disk in a laptop)

Search google for instructions on installing different distros to pen drives, there are countless numbers of guides on there.

I heard about that problem with flash drives. These sites might have a solution [http://blog.datalight.com/](http://blog.datalight.com/) [http://www.embedded.com/design/205906509](http://www.embedded.com/design/205906509) 

I wonder what people will do when magnetic memory goes on the market? I can't really say I'm attracted to it.

---

### Post by Spaceman9 on 2008-07-19
> **mcduck said:**
> Bwahahahah. Even the Freeciv game describes Finland's main exports as "Mobile phones and premium quality operating systems" ;) I actually think that Linux doesn't come from any single country, mainly because both the kernel developers and all the people who help to make it usable OS live all around the world..

Anyway, I'm glad if I could help. :) And I actually prefer using a removable hard disk for my backups. I only connect it to my computer when making the backup, to avoid the nasty possibility of power source failure destroying both the main hard disk _and_ the backup drive at the same time.

Depending on how large amounts of data you need to backup (and how often) either external drive, or one with internal docking bay, would be a good choice. I work a lot with multimedia and video stuff so the backups are very large, but I also need to be able to access the drive with my laptop, so I bought myself external hard disk enclosure that works both with a 5,25" internal docking bay (connected through SATA-2) and as external drive connectable with both USB2 and eSATA. The enclosure & docking bay were about 30€ and a 350GB 2,5" drive was a bit less than 100€. Definitely worth the money, and most likely same hardware will cost a lot less where you live.. (Finland is _very_ expensive country..)

I didn't know one of Finland's main exports is mobile phones. We call them cell phones in the US of A. Mine says Made in China. I don't mind things made in Red China though. They go really well with a blue table cloth.

I like your idea of a usb hard drive. I saw a 200GB usb hard drive sell on ebay this week for just $40.00. A local office store has a 500GB Seagate usb drive for $109.99

---

### Post by mcduck on 2008-07-20
> **Spaceman9 said:**
> I didn't know one of Finland's main exports is mobile phones. We call them cell phones in the US of A. Mine says Made in China. I don't mind things made in Red China though. They go really well with a blue table cloth.

Yeah, I can't even remember the last time I've seen a Nokia phone that was actualy made in Finland. But their research&development center is still about 5km from where I live, and headqurters are also in the same city.. Actually I think the hardware used for the actual mobile networks is still made here, at least even CIA factbook lists "electronic, telecommunication devices, cell phones and other high-tech exports" (nothing about operating systems there :D)

If the 200GB drive is big enough for your backups that seems like a great buy.

---

### Post by danwood76 on 2008-07-20
> **Spaceman9 said:**
> I heard about that problem with flash drives. These sites might have a solution [http://blog.datalight.com/](http://blog.datalight.com/) [http://www.embedded.com/design/205906509](http://www.embedded.com/design/205906509) 

I wonder what people will do when magnetic memory goes on the market? I can't really say I'm attracted to it.

Even with write leveling the fact of that matter is that a modern PC filesystem like NTFS or EXT3 write constantly to the filesystem and reduce the life considerably.
Thats why all flash memory and flash drives come formatted FAT as on average it uses less write cycles per data block.

Removable hard drives are very good, most new hard disks come with a 5 year warranty also.

BTW Nokia is a finnish company, and as the biggest producer of mobile phones in the world is why its one of their biggest exports.

-- edit --
Oops didnt see mcducks post mentioning Nokia ;)

---

### Post by Spaceman9 on 2008-07-20
> **danwood76 said:**
> Even with write leveling the fact of that matter is that a modern PC filesystem like NTFS or EXT3 write constantly to the filesystem and reduce the life considerably.
Thats why all flash memory and flash drives come formatted FAT as on average it uses less write cycles per data block.

Removable hard drives are very good, most new hard disks come with a 5 year warranty also.

BTW Nokia is a finnish company, and as the biggest producer of mobile phones in the world is why its one of their biggest exports.

-- edit --
Oops didnt see mcducks post mentioning Nokia ;)

Looks like the bottom line is keep the FAT in the flash and hope for the best. If a flash drive burns out can it be said it was FAT fried? I wonder what FAT fried flash drives taste like? I like mine with chips! Thankx for your help.

---

### Post by danwood76 on 2008-07-20
Hehe, yeah they almost sound tasty.

A journaling filesystem (like ntfs or ext3) shouldnt be used if you want the drive to last long.

All this being said flash drives do last quite a long time with many read and writes, I have also managed to recover quite a bit of data from a dead flash drive before although there were quite a few sectors that were completely dead.

Glad to help ;)

---

