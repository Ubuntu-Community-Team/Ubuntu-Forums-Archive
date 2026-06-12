---
title: "Sorry for that: external USB HD... which filesystem?"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by pavallokazzo on 2008-03-11
Ok sorry for opening again a thread about this but all discussion seems too old and incomplete to me...

I want to have an help and people feedback about the "Choose a filesystem for USB HDs" topic and maybe enlarge it for internal partition for data exchange beetween linux and other OS...

Thanks

PS = This would really be a good article to put in the wiki as many people are looking for THE ANSWER on this "problem"

---

### Post by pavallokazzo on 2008-03-11
First feedback is mine, so you can see what I was thinking about (and what I know):

EXT2 is a very trusty filesystem, used from years by linux community offers a good protection against "bad blocks", however fact is it miss a journaling system so data recovery should (I'm not sure, plz correct me) be hard...
It also offers a good deal on storing capacity (250 GB HD formatted with this fs will result in circa 250 GB of free space to use)(***need to verify this!)... 
Biggest bump is it practically never needs defragmentation, as it is usually around 1-3%...
Biggest problem is it isn't supported natively in MS Windows family products. This can be achieved with external driver that however riduces its function as a portable storage device...

EXT3 points to cover the only problem (we can care about) of EXT2: journaling system. So is basically an ext2 fs with an extended function of journaling that will result in a probably easy data recovery due to erranous deletion / HD' failures.
EXT3 for this usually use the 5% of a partition space... on a 250GB HD the free space is usually 233GB

FAT is an old fs used by the time of DOS. It's not anymore developed by Microsoft but is widely used in the portable storage device as it is supported by almost all OS. 
It differs in FAT16 or FAT32, where the differences is the bits used by the File Allocation Table...
FAT32 can support till 4gb (2-3?) file size and till 512gb (1tb?) disk partition, but in Windows format is supported till 32gb(?), maybe for growing NTFS usage (I always like to spam dirty M$ market strategies ;) )...
It's highly sensitive to defragmentation, so it's highly reccomended to use thirdy party tools (as MS Defrag doesn't do well is job..........) to achieve this. 
Anybody knows about free and/or for linux software to work on fat32 defragmentation?
However it is reliable against bad blocks issues (does it?) and, again, the fact that is widely supported takes it as one of the top choice in portable storage devices.
It can't store user-bit identification so isn't recommended for sensible/system data
250 GB HD usually result in 240GB of free space

NTFS is the new MS fs. It offers support to 4gb> files size, 1tb (?) disk partitions, journaling (?) and bad blocks (?).
NTFS can store user-bit identification for NT systems (linux can use this?), support fs-level compression and cryptosimilsomething(!don't know the word!)
NTFS is supported natively in Windows NT, 2000, ME, XP and Vista while in Linux it's support is provided by NTFS-3g tools. Basic functionality are provided, however compression and crypto...(damn!) is still out of service. (what about Apple? and PS3/XBOX360?)
NTFS still soffers of data fragmentation, but as it's technical specific (gimme the word plz!) aren't released by MS it's support by 3rd party is still to be provided...
Again some tools to work on it with Linux and/or for free are very welcomed.
250 GB HD result in 233GB of free space

others dunno...

FEEDBACK:
EXT2 never tried
EXT3 never gived me a problem. When some errors occured on my HDs usally a fsck works good to restore the situation.
EXT3 drivers for linux used to give me some trouble... Both needs a restart so basically they aren't good to use this fs for a real portable device...
Plus:
[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm) 
this worked good for me (basic usage) but gived me problem removing the assigned drive letter...
basically after uninstalled this an L: (was my reference to the linux fs) remains in My Computer screen, pointing to the last assigned letter device (usually pointing to D: - a partition of my hd - and when using an usb storage device pointing to it). This resolved installing the others ext2 drivers...
This drivers offers a bad interface, you have to keep the binaries (.exe) plus the dll somewhere you know cause every time you want to assign a letter to a device you got to find'em, open'em up and do the job.
[http://www.fs-driver.org/](http://www.fs-driver.org/)
this worked good too, not any problems at all
it need a restart after the install, then you can easily configure the assignation by a tool in a control panel. Anyway most of the time it will work Plug&Play!
Only point is it doesn't allow to mount a fs that has been badly/not mounted (like when you put ubuntu in hibernation and restore windows! but you shouldn't!), so you have to mount and unmount that device from linux and then you can mount it on win

FAT32 has been a surprise. No problem at all (for a MS patent that's something new!), when problems occured fsck or MS scandisk worked well. 
After some months of use without giving a defragmentation I didn't noticed speed problems, but I didn't run any benchmark on it!
Still suffer of file length problem (till 2 or 4 gb???)

NTFS I'm trying it now. After 1 day (!) first problem: I unplugged the device from an hiberned (under windows) computer, taked out the hd from the usb box, putted in a new computer and while mounting I get an error that device hasn't been unmounted well, and that I should use the "safely remove" tool under win. So init 0, take the hd, put in the usb box, boot win, use the safely remove, take out the hd from the usb box, link to the computer, boot it and then mount it again went fine.

ReiserFS plz don't use it! At least the 3...
But if you don't care to loose data, it offers 247 GB of space on a 250GB HD

others FS dunno...

update on NTFS: I'm moving data (with kubuntu 7.10) to this new hd with NTFS partition on it and it's sloooooooooooow!
the other disk is a little corrupted (using Rieser FS- damn...) but speed it's stuck at 1-1.5 MB/s and there is this process in ps "mount /dev/hda1 hda" that  it'using 15-40% of processor!
but I'm using konqueror to do that (cause I've to check what to move!) and kioserver too it's stuck around 45% cpu usage

---

### Post by pavallokazzo on 2008-03-12
bump!

NTFS-3g seems extremely slowly...
I will get back to ext3 as soon as I can

---

