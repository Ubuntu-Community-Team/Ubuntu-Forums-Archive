---
title: "Easiest way to clone system disk to SSD"
date: 2015-10-26
forum: Hardware
---

### Post by dogatedog on 2015-10-26
Hi,

I've checked the forum, but couldn't really find a post that handles my specific situation. 

Currently I have several HDD's in my server (Ubuntu 14.04.3 LTS). Lately some of them have been failing so I've been replacing them and just copying the contents over as necessary.

Since my boot disk is of the same model and make as some of the failed disks, I'm getting paranoid and want to replace it as well. So, as long as I'm replacing, I might as well use this opportunity to make my server a bit faster. 

Current situation :

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdk2       3.6T  167G  3.3T   5% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            7.8G   12K  7.8G   1% /dev
tmpfs           1.6G  780K  1.6G   1% /run
none            5.0M  4.0K  5.0M   1% /run/lock
none            7.8G  4.0K  7.8G   1% /run/shm
none            100M     0  100M   0% /run/user
/dev/sdk1       511M  3.4M  508M   1% /boot/efi
```

As you can see, the 4TB disk that is now my boot disk is way too big (and it even contains 100gb I could easily part with if needed). The data used is not even 170gb in total.
The 4TB is :


/dev/sdk:


 ```
Model=ST4000DM000-1F2168, FwRev=CC52, SerialNo=Z300RRLV
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=7814037168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7
```

The SSD I ordered is a Kingston SSD 2.5", 240GB, SATA600, SSDNow V300. More than enough to hold the 170gb and then some.

What I want is to clone the 4TB HDD to the 240GB SSD. I know there are tools in Windows (Norton/Symantec Ghost) which can perfectly clone entire Windows installatie from a larger HDD to a smaller SSD, but I doubt these would work if I hooked up the Ubuntu 4TB to a Windows machine and let it do its magic, so I'd rather do it all on Ubuntu.

The things I've read on this forum all apply to cloning to an equal in size or larger new HDD and that's not applicable in my case.

Can anyone give me the steps to perform the HDD to SSD cloning ? Preferably as fail-safe as possible. I do have another Ubuntu server I could use to perform the cloning (so I could hook up the 4TB and the SSD there) if that makes things easier.

I did find this tutorial from 2012 : [http://blog.oaktreepeak.com/2012/03/move_your_linux_installation_t.html](http://blog.oaktreepeak.com/2012/03/move_your_linux_installation_t.html)
Don't know if it's still relevant/working to the current situation, though ?

---

### Post by Bucky Ball on 2015-10-26
Welcome. You want to clone a 4Tb partition to a 240Gb one??? Unsure how that works. If you are talking about cloning only the OS partition, then Clonezilla could be what you are looking for. These links can help with that:

Home site:
[http://clonezilla.org/](http://clonezilla.org/)

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

If you have a source partition of, say, 100Gb, the target partition you're cloning to must be 100Gb or bigger. There is no way I know of to shrink 4Tb of data onto a 240Gb partition. You can compress the files and drop them onto the smaller partition, but doubt you could compress them that much. 

So, bit confused by what you're actually wanting to do. If you 4Tb partition has only 200Gb of data on one partition, I suggest you shrink that partition to 200Gb then clone that using Clonezilla. Good luck. :)

(PS: Please use code tags for terminal output. See the last link in my signature. Thanks.)

---

### Post by dogatedog on 2015-10-26
Thanks (and I've put the terminal output in code tags, sorry about that) for your fast reply.

Maybe cloning is the wrong term then. Shrinking my partition on my 4TB HDD is a risk I don't want to take. I don't want to touch the HDD at all, except for reading data.
And you're absolutely correct, even commercial programs like Acronis True Image require that you shrink the partition you want to clone to fit on the destination disk.

So, I think I might go with the site I linked ([http://blog.oaktreepeak.com/2012/03/move_your_linux_installation_t.html](http://blog.oaktreepeak.com/2012/03/move_your_linux_installation_t.html)) as a first attempt. I was just a bit worried because it's an article from 2012, which might not take into consideration caveats introduced since then.

---

### Post by Bucky Ball on 2015-10-26
Well, what I did when I did this a couple of year or two ago was Clone the Ubuntu and XP partitions to an external drive, stick in the SSD and created partitions on it the same size as the ones I'd cloned, then cloned the clones using the SSD partitions as targets. Voila, fiddled with Grub and done. 

But that was fine for my setup. Might not be for yours. My Ubuntu partition was 15Gb and the XP one was about 20Gb so ...

---

### Post by dogatedog on 2015-10-26
I'll report back once I did it. Parts need to come in first (probably tomorrow or the day after). Decided to also buy a new power supply as I suspect this to be a factor in my failing HDD's as well (3 in a week can't be a coincidence..).  Thanks for now !

---

### Post by Bucky Ball on 2015-10-26
The PSU is the heart of the machine, yes, and anyone that's been here a few years will possibly have seen me banging on about them.

Get a name brand, not a generic silver box, and rated 80+. You won't regret it. Cheap PSU are unreliable and dangerous. They can take out the components in your box when they spark, flame and blow smoke, or worse (a friend of mine set the curtains alight and almost burnt their kitchen down using a generic silver box PSU, and that's not the only story you'll find about them).

And you're not powering a small city so think about overkill. You won't need a 1,000Watt job for a box with a few hard drives, a graphics card and couple of other bits. There are a few PSU calculators about on the net if you have a look. Antec used to have a very good one, but calibrated to their efficient PSUs. 

Good luck.

---

### Post by dogatedog on 2015-10-26
This is the one I ordered this morning (prior to posting here) : [http://www.corsair.com/en-us/cs-series-modular-cs750m-750-watt-80-plus-gold-certified-psu](http://www.corsair.com/en-us/cs-series-modular-cs750m-750-watt-80-plus-gold-certified-psu)

I've done the calculations, with my 12 HDD's I should be good with 400watt, but just in case. :)

---

### Post by Bucky Ball on 2015-10-26
Quiet and efficient. Looks like a good choice, if a little 'killing a mosquito with an elephant gun', but you never know what you're going to want to put in the box in future, so 750W is future-proofing I guess. :) 

Generally gamers or pro-audio/video production boxes with steam coming out of their vents require that stratosphere of PSU wattage, but as I say, if you have a couple of PCIe slots and what not, could get crowded in future.

---

### Post by weatherman2 on 2015-10-26
> **dogatedog said:**
> Thanks (and I've put the terminal output in code tags, sorry about that) for your fast reply.

Maybe cloning is the wrong term then. Shrinking my partition on my 4TB HDD is a risk I don't want to take. I don't want to touch the HDD at all, except for reading data.
And you're absolutely correct, even commercial programs like Acronis True Image require that you shrink the partition you want to clone to fit on the destination disk.

Not necessarily.  I recently used True Image Home 2012 to clone a larger partition to a smaller one, automatically.  I used the rescue disk, booted from USB, not a Windows install of True Image.

Of course, my source disk - 750GB - had only about 150GB used, so it fit easily on a 500GB destination SSD.  Obviously, no matter what software you use, you can't clone a partition that uses more space than your destination partition.

---

### Post by dogatedog on 2015-10-27
A little background story if I may :)

I'm somewhat convinced that my current power supply is the root of my disk problems, anyway. Right now I'm using two of these (find image attached).

On one of them all 5 ports are taken, on the other one 3 ports. These are connected via sata to a pci sata controller (with 4 ports). 
On top of that I have 3 hdds connected to the regular sata ports on my motherboard.  Which makes a total of 11 hdd's that have to be powered.

At the time I only had one of these backplanes, to which 5 hdds were hooked up. All was fine until 2 drives actually went belly up (Seagate.. not known for being reliable in NAS..). I replaced the two drives and while I was at it, I added the second backplane with three additional hdds. From then on it was troublesome, a lot of ticking, repowering of the backplanes automatically, spinning up of drives all the times.  I even got disk errors (I/O errors trying to do an 'ls', unable to mount them on restart). Last night I decided to disconnect the second backplane (the one with three drives), and lo and behold, the drives that had given me I/O errors came back online.  Everything was dandy again.. until this morning, when 2 of the drives in the remaining backplane no longer wanted to be mounted (I/O error).  So, I'm really betting on the power supply to be the culprit and all problems to magically disappear when I install the Corsair. 

If you happen to know of another way of safely hooking up 12-15 drives (I'm planning to add a few more drives if possible) without using the backplanes (recommendation for an extra sata controller card maybe), I'm all ears. Right now I'm not saving any expenses.. I just want my server to run reliable again and if that means forking out some extra cash, so be it.

---

### Post by dogatedog on 2015-10-27
> **weatherman2 said:**
> Not necessarily.  I recently used True Image Home 2012 to clone a larger partition to a smaller one, automatically.  I used the rescue disk, booted from USB, not a Windows install of True Image.

Of course, my source disk - 750GB - had only about 150GB used, so it fit easily on a 500GB destination SSD.  Obviously, no matter what software you use, you can't clone a partition that uses more space than your destination partition.

Hmm. might be an option then. It had no trouble recognizing ext4 partitions and you could boot of the SSD afterwards ? I would imagine you'd have to edit /etc/fstab wrt the UUID of course ?

---

### Post by weatherman2 on 2015-10-27
I didn't use it on ext4 partitions so I don't know.  True Image Rescue CD is Linux-based and has recognized ext3 partitions for me in the past but I have mostly used it for Windows.

I was just pointing out that True Image has the capability to clone to smaller partitions.  I wasn't suggesting you buy it, but if you already have it, try it.

If you are cloning Linux partitions, you could use dump or rsync (use the -x option to skip anything outside of the partition in the file system) to clone file systems.  That's how I have "cloned" Linux disks many times.  Create the new partitions on the new disk first, then "clone" each one at a time.  After that, yes you would need to edit your new fstab file and install Grub on the new disk.  I prefer the "chroot" method of installing Grub on a new disk.  Do a web search for "ubuntu grub chroot" to find the official documentation.  The one trick is to mount some system partitions (listed in the docs) prior to doing the chroot.  But it's pretty easy.  Then, yes, the target disk should just boot.

---

