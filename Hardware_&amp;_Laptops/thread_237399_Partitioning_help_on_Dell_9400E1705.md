---
title: "Partitioning help on Dell 9400/E1705"
date: 2006-08-16
forum: Hardware &amp; Laptops
---

### Post by drlinux on 2006-08-16
I have recently bought a Dell Inspiron 9400 with a 100Gb HDD and 1Gb RAM. I am wanting to install Ubuntu with Windows dual boot. 

I plan on keeping my linux partitions simple with a 500MB swap partition ( I believe there is no advantage in going any larger than this) a / partition and a home partition.

In the wisdom of Dell have taken up 3 primary partitions as below:

DELL INSPIRON 9400
HD PARTITION TABLE

                                      Size          Used

01 dev/sda1 fat16                  47.03MB        32.17MB

02 dev/sda2 ntfs                      88.70GB      10.19GB

03 dev/sda3 fat32               3.00GB       1.91GB Dell Restore

04 dev/sda-1 free                   7.84MB        n/a

I was planning on using Gparted to shrink partition 2 to 40Gb and then moving partition 03 next to it leaving a free 04 partition of approx. 45Gb in which to put Ubuntu. 

I realise if I am going to do this I will have to make 04 an Extended partition and split it into Logical partitions. I was also going to put Grub in the MBR but am concerned that the 01 partition above is only 47 MB and I see that most linux boot partitions are 100MB in size.

Do you foresee any disadvantages/problems/pitfalls with having the Extended/Logical partitions as suggested above? Will I run into problems with my dual boot if I go ahead with Grub in the MBR?
Your advice is much appreciated? :confused:

---

### Post by s0lar on 2006-08-16
I also had this original partition table. I suggest you make another :).
You can try to make an image of your harddisc, hopefully it fits on one or two dvd's so you can easily go back to you original OS. Or do like I did and buy yourself another harddisc, change it and make it a ubuntu only laptop.

---

### Post by Original Brownster on 2006-08-16
Hi There,
It's quite an ambitious project, a bit like taking a scalpel to your disk however if you feel upto it, my advice first and foremost is take a back up of your important data, then take another one! If you have something to create an image of your windows partition even better, do that as well. Chances are you'll be fine but it's better to think ' how would I feel now if I just toasted everything? What have I lost? ' 

If you don't have a live cd or other bootable cd I would recommend getting one in case you have any problems, make sure that this can connect to the net (normally easy if you have a ethernet connection to a decent DSL modem)

Enough rambling, /boot should be reasonable size and 100mb is good, mine is not on a separate partition at all, looking at the disk usage it's now 48mb after 18 months of new kernels etc. I used to slice up my disks all over the place but invariably found I ham strung myself somewhere along the line, so nowadays i have one big root partition and a separate huge partition for all my music which I just mount and share. 
There are pros and cons to this approach but it suits me, another option is to use LVM (logical volume manager). 

Back to your question, if your mobo is reasonably modern it should support LBA (logical block addressing) and therefore there is no reason why you cannot put your /boot partition anywhere on the disk, it was the older bios's that use chs addressing that could only read from the first 1024 cylinders. Check first in your mobo bios settings or manual and see if it's supported and if so you can just create a logical partition in your extended partition like

/sda5 - /boot 100mb
/sda6 - /root 5gb
/sda7 - swap 500mb 
/sda8 - /home the rest

if you install grub in your mbr it should work, it'll just point to the /boot at hda5. Also the installer should 'see' your windows partition and create an entry to boot that too. Having said that people _do_ have problems dual booting, a search on here will show it's not uncommon. Be prepared for the worst hence the above precautions!

If you need to use your partition 1 (sda1) for boot, you could run into problems later on when successive kernel upgrades fill it up unless you keep removing the old images yourself.

HTH

---

### Post by coffeecat on 2006-08-16
First, I think your idea of making an extended partition split into logical partitions is a good one. In fact it's your only option if you're going to leave the Dell Windows partitions as-is! One advantage of Linux is that it can boot from a logical partition - unlike a certain so-called OS from Redmond. :wink:

Of the rest I think you are confusing what you have in sda1, a Linux boot partition and the MBR. I have no idea what that small sda1 is. It's probably a Dell special and best left alone but, be warned, these odd little proprietary partitions (particularly the hidden ones) can cause problems when installing Linux. Sometimes they confuse the partitioner. The MBR is the first 512 bytes of your HD and is separate from the actual partitions. [This link]("http://www.cpqlinux.com/mbr.html") explains more. Grub stage 1 will occupy the first 446 bytes when you have installed Linux.

A linux boot partition is used by those who wish to keep this separate from their / (root) partition. There are pros and cons to having a separate /boot, but many people go for the simpler option of having /boot within the main root partition. A default Ubuntu installation does this.

So - Grub will go into the MBR if you use the live CD installer. You have no other choice. If you want to put Grub elsewhere you must use the alternate CD. But it's easiest to put it in the MBR and it won't overwrite sda1, but it will overwrite the Windows boot code. As it will also set up a dual-boot menu this is not an issue unless you wish to get rid of Linux and revert to a Windows-only box. But you won't want to do that will you? :)

---

### Post by drlinux on 2006-08-16
Thank you guys for the detailed explanations and advice - I have asked this question on 2 or 3 forums and your answers have been the most clear and complete - so gold star all round!

Just a note to let you know I have dicsovered the Dell 3GB partition is purely for restore and nothing else - I already have Dell Windows restore CD's and so am thinking of deleting that 3GB restore partition.  This is a new laptop and I am yet to add any serious data to the hard disk so am not worried re data loss. All my serious work will be done under Linux  - Windows  is only there for the games - sad I know!

One last question - are there any disadvantages to extended/logical partitions?

Thanks again for your help. :KS

---

### Post by Original Brownster on 2006-08-17
Hi,
AFAIK there is no advantage to using primary partitions over logical other than that pointed out by coffeecat.

I dual boot windows, it's there only under sufferance. Sometimes it's useful for work purposes and the occasional game but these days it rarely gets CPU time :-)

Regards

---

### Post by sonnywise on 2006-08-17
sudo parted /dev/sda print
Disk geometry for /dev/sda: 0kB - 100GB
Disk label type: msdos
Number Start End    Size    Type     File system  Flags
1      32kB   21GB  21GB    primary  ntfs         boot
2      21GB   93GB  72GB    extended lba
5      21GB   23GB  2147MB  logical  ntfs
6      23GB   93GB  70GB    logical  ntfs
7      93GB   93GB  280MB   logical  linux-swap
3      93GB   99GB  5610MB  primary  ext3
4      99GB  100GB  1078MB  primary  ntfs

In my new HP Pavilion DV5615ea I had a configuration like yours so I deleted the restore 5 GB partition after preparing 2 DVDs for restore (if I'll decide to resell my laptop :D ) then I used the available space for linux root and swap partitions.

Dual boot is working well for me with this setup.

---

