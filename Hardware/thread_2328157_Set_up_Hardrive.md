---
title: "Set up Hardrive"
date: 2016-06-17
forum: Hardware
---

### Post by aaron50 on 2016-06-17
All,

I am working with Ubuntu 14.04 and have installed lubuntu, for gui purposes. I have just bought a hard drive enclosure, that uses 4 hard drives. When i login to lubuntu, and go to "disks" i see that the drives are all there sbd, sdc,sdd, sde. I am trying to format the drives as ext4, but don't even know how to get started. I read some places that i should use fdisk /dev/sdb then choose "n", and go from there. I am very new to formating new hard drives, so i have no idea what this is doing. I also read that i should use mkfs.ext4 /dev/sdb. My issues are that when i format the disk, using fdisk, the "disks" program says partitioning - GUID Partition Table, but the contents says unallocated space. When i use the mkfs, it does not have a partitioning section, and says contents is Ext4. Can someone one walk me through step by step on how i should format and set up my hard drive, then i can repeat the process for the other 3. Thanks for any help you can offer.

Edit: each drive is 4TB inside the enclosure.

---

### Post by weatherman2 on 2016-06-17
Use Gparted.

---

### Post by yancek on 2016-06-17
The GParted manual is at the link below which explains everything you would need to know about partitioning

[http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by Bucky Ball on 2016-06-18
> **weatherman2 said:**
> Use Gparted.

Easiest. Right click the drive, 'New', create a partition. All outlined in yancek's link.

---

### Post by xen3 on 2016-06-18
> **aaron50 said:**
> All,

Can someone one walk me through step by step on how i should format and set up my hard drive, then i can repeat the process for the other 3. Thanks for any help you can offer.

A partition is a division on disk in which parts of the disk are accessible as their own "volume". In Linux, these volumes are normally called /dev/sda1, etc. where "1" is the number of the volume on disk "sda". In the past people used "MS-DOS" style partition (tables) also called "MBR", but these days on Linux there is not *much* reason to prefer them over the newer "GPT" or "GUID Partition Table" standard.

This is mostly because Windows cannot boot GPT disks unless you use "UEFI" for booting, but Linux can boot GPT disks just fine with a little knowhow.

If you don't care about subdividing your disks, that means you will end up with e.g. 4 disks that each have just a single partition, which will then be called sdb1, sdc1, sdd1, sde1, for example.

A more advances technique is to use the "Logical Volume Manager" but that is outside the scope of what I can write here. And I have no other material for this ;-). Presently.

But just saying: with the LVM, you could create a single large volume group (VG) for example called "external" (or whatever you like) and then you could add all the disks to that volume group. Then you could do a number of things, but mostly what you get is the ability to subdivide your disks any way you like. Instead of having partitions that would be called

"/dev/sdc1" -- you would now have partitions being called "/dev/external/name" and the next one "/dev/external/othername". This complicates matters, but if you need it, it is a very convenient system.

However, just saying that you would create a single regular partition on a GPT partition table for these disks, you would end up with 4 distinct partitions a mentioned, one for each disk.

The "mkfs" program has nothing to do with partitions, but it uses them to create a filesystem on them, or on top of them. This filesystem is what you know as "ext4". For this filesystem, it is irrelevant what "block device" is underneath it, so once you have those "block devices" (your partitions) and you have created filesystems on top of them (on them) you will next decide where you want those filesystems (partitions) to be "mounted". You will need a place to access them.

What I wanted to write about, but my head goes mayhem, is that you also need to decide where to access your data.

One example is to put everything under a directory of your choice such as /mnt, or /external. Then all of your drives would be /mnt/sdb, /mnt/sdc, /mnt/sdd, and /mnt/sde, if everything is equivalent to you. You would then have a fixed subdivision of 4x 4TB. Each accessible under its own subdirectory.

It does mean you need to constantly decide what data goes where. Maybe you will put video on them, I don't know. What if you have more than 4TB of video? Now you need to decide what part goes on what disk. It is also possible to combine multiple drives such that you have one 16TB volume, or two of 8TB, for example one for main, and one for backup.

But in any case (particularly if it has four drives):

- mounting fixed drives (even if they are external) means accessing them from a location defined in /etc/fstab
- if your home directory is not encrypted, you can access them even from your home directory (mount them there)
- otherwise you will need a fixed location as mentioned, such as /external, or even /store.

Just giving some pointers here.

Having combined volumes means that you can access the whole combined space through one path (or directory, or mount point) which means it acts as one big whole, and you can use it as that. At this point I suggest you think about combining them into two 8TB volumes, one for main, and one for backup, and then to mount them under /storage and /backup, for example, or otherwise /external/data and /external/backup, or something of the kind. But it's entirely up to you, up to anyone.

Pardon my bad writing here. Regards.

---

### Post by xen3 on 2016-06-18
I immediately want to add something here, even if it is too much information.

As long as your drives are always connected first (after your main disk) they will be sdb, sdc, sdd and sde. If not, for example because some USB stick gets in the way, all of these "numbers" (letters) will be displaced. The solution that is often advocated is using UUID, but this is not necessary:

- all LVM volumes have a name, and are always accessible under /dev/volumegroup-name/logicalvolume-name such as /dev/external/main.

- all GUID partitions can have a label, and are always accessible under /dev/disk/by-partlabel, such as "/dev/disk/by-partlabel/firstdisk", if you wanted that.
- all filesystems can have a label also, and are always accessible under /dev/disk/by-label, such as "/dev/disk/by-label/video", if you wanted that.

- the GParted program can set GUID labels (names)
- tune2fs -L /dev/sdb1 can set filesystem labels
- LVM labels are automatically set when created.

If using GUID labels, and not using LVM, and having 4 disks of 4 TB each, with a single partition, all mounted under /external/1st, /external/2nd, /external/3rd, and /external/4th, then you would have an fstab that looked like:

```
/dev/disk/by-partlabel/firstdisk   /external/1st   ext4   nofail   0 0            <-- nofail means that booting your system will not fail
/dev/disk/by-partlabel/seconddisk  /external/2nd   ext4   nofail   0 0            <-- if the disks are not present, which is important
/dev/disk/by-partlabel/thirddisk   /external/3rd   ext4   nofail   0 0
/dev/disk/by-partlabel/fourthdisk  /external/4th   ext4   nofail   0 0            <-- they will get automatically mounted at boot though
```

Just giving an example of what it would look like. On the other hand, if you used LVM, and you had 2 divisions of 8TB, it could be something like this:

```
/dev/external/main    /external/main     ext4   nofail   0 0
/dev/external/backup  /external/backup   ext4   nofail   0 0
```

or simply

```
/dev/external/main    /data     ext4   nofail   0 0
/dev/external/backup  /backup   ext4   nofail   0 0
```

Using the LVM solution, a setup procedure would look like:

```
pvcreate /dev/sd{b,c,d,e}
vgcreate external /dev/sd{b,c,d,e}
lvcreate external -n main -l 100%pvs /dev/sd{b,c}     <-- now 8TB
lvcreate external -n backup -l 100%pvs /dev/sd{d,e}   <-- now the remaining 8TB

mkfs.ext4 /dev/external/main -L "main"                   <-- -L adds a filesystem label
mkfs.ext4 /dev/external/backup -L "backup"               <-- same

mkdir /external
mkdir /external/main
mkdir /external/backup

echo "/dev/external/main   /external/main   ext4 nofail 0 0" >> /etc/fstab
echo "/dev/external/backup /external/backup ext4 nofail 0 0" >> /etc/fstab

mount -a
```

Would basically be the entire setup procedure. You would now have two mounted partitions of 8TB each, that you can add stuff to by writing to /external/main and /external/backup. The choice for names may be confusing: the first part, "/dev/external/main" means a device called "main" (as a logical volume) part of the volume group "external" that happens to span 4 disks. The second part "/external/main" is just the location we have chosen on our filesystem which is rather arbitrary. It could equally have been /home/myuser/video and /home/myuser/backup-video.

Now in your GUI you can ensure that these locations (and hence, these disks) are easily accessible to you.

---

### Post by TheFu on 2016-06-18
Lots of info above.

Just want to add a caution about using LVM to span across multiple disks. If 1 disk fails, that can make data loss happen across all the disks included in that LV.  I use LVM always on physical disks, but NEVER span volumes (LVs) across more than 1 disk at home due to recovery and backup ease of use.  My backups are limited to 4TB in size, so I don't allow any volume (LV) to be larger than that.  There are some great reasons to use LVM - flexibility, performance, snapshotting. But with those things comes extra complexity.  If you are new to Linux, that complexity can be overwhelming, so staying with simple GPT and ext4 partitions would be smarter.

If the intent is to store media on these disks, it might be worth looking into ZFS.  ZFS validates that data written to the disk is actually there correctly.  It is a newer generation of disk management with roots in Solaris.  ZFS merges volume management (like LVM) with RAID (like mdadm) with file systems (like ext4 ...) with block replication via zsend (like DBRD) with NAS services (like NFS, iSCSI, Samba/CIFS) all provided by native ZFS.  If you have lots and lots of RAM, you can enable ZFS deduplication, but I've never had enough RAM in any of my machines to support that. I know that some other distros have allowed booting from ZFS, but don't recall if Ubuntu does.  At this point, I'd only deploy ZFS for data storage until you get more comfortable with the "pool" management commands in ZFS.  

I really need to move my media storage over to ZFS to reduce bit corruption.  Just need to take the time to do a little more hands-on research then just do it.  I have excellent backups, so it really is just a time-to-do-it thing.

Please be certain that some backup techniques are included with the storage plan.  Also, RAID does not replace backups. RAID is for very high performance and for high availability. It is also a good way to write corrupt data to multiple places concurrently. ;(

Still - lots of good info above.  There are guides for LVM and ZFS over at help.ubuntu.com and wiki.ubuntu.com. Be sure to check those out. 
[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)
[https://wiki.ubuntu.com/Kernel/Reference/ZFS](https://wiki.ubuntu.com/Kernel/Reference/ZFS)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[http://www.tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://www.tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html) - The Linux Documentation Project has great, but likely older, information. For administrators and non-GUI tools, it is probably still valuable.
[http://www.howtogeek.com/211937/how-to-use-lvm-on-ubuntu-for-easy-partition-resizing-and-snapshots/](http://www.howtogeek.com/211937/how-to-use-lvm-on-ubuntu-for-easy-partition-resizing-and-snapshots/) - clear, if simplified, how-to guides.

Don't feel like you **need** to use LVM or ZFS if you aren't ready for those tools. Most of the extra features provided aren't needed for home users.

And don't forget that this stuff is supposed to be fun. ;)

---

### Post by aaron50 on 2016-06-19
Thank you everyone for the help. I have decided to go the gparted route and stay away from LVM at this time.

---

### Post by xen3 on 2016-06-19
Says LVM is complex and then mentions ZFS ;-).

But it is true what you say of course.

Personally? I would try to use mdadm (RAID) but this is a very bad command line tool from my perspective, and I thought the previously existing tools were actually better. If using LVM, I would try to use striping. Personally, if I didn't have the time (or the balls) to use "mdadm RAID" I would simply stripe my data across 2 hard-disks and hope it doesn't fail, but also ensure that my second set of disks is a backup for that. Even though having both sets in the same volume group (VG) is a bit of a liability, in practice that would probably work out fine for anyone, but more help is always available on the forums if you need it.

(Sometimes a solution is only as good as the level of support available in case you need more help, or something goes wrong).

This was just the simplest LVM setup I could imagine (and that exists, I guess) that demonstrates combining of two harddrives.

The question is whether the user wants the advantage of bigger volumes (filesystems) at the cost of a little bit more complexity, or stick to simplest-solution having-four-disks-with-four-different-filesystems.

So the choice here is between:

[LIST]
[*]volumes of 8TB in size, allowing you to use that as a whole
[*]both harddisks of each set need to be operational at all times
[*]to compensate you need a good backup strategy, which basically means using the other 2 disks as backup.
[/LIST]

And:
[LIST]
[*]volumes of 4TB in size, having 4 separate volumes and filesystems
[*]all disks function on their own, and can only fail individually
[*]requires 4 mount points in your filesystem tree
[*]backup is slightly less important, but in the end still quite mandatory
[/LIST]

I just didn't want to make it more complex than that.

I think I have failed my goal of not overloading this person though.... ;-).

And I guess I'm too late with this answer. I was trying to see if there is any possibility in this day and age of actually having an instant messenger account somewhere.

I guess it is not really possible. Regards.

---

### Post by xen3 on 2016-06-19
By the way

> [COLOR=#000000]Most of the extra features provided aren't needed for home users.[/COLOR][COLOR=#000000]

I would disagree with that. You can't compare ZFS to LVM. LVM is much easier than most other systems I know in Linux. Its command line options and parameters, its tools, are actually useful and user friendly for a change.

I don't think you should dissuade users from using LVM, it doesn't do it justice.

LVM is easier than creating manual "real" partitions, for example, because it automatically rounds it up to 4MB sizes, whereas with regular partitioning tools you always have to take care of what kind of boundary you are going to end up with in the sense of never knowing whether the tool is using real MBs/GBs or the powers-of-ten sizes that are these days considered MB/GB. That usually makes it rather hard to decide on any division (such as using a certain percentage of the disk) that makes sense in the sense of "real" MB/GB units.

LVM takes that concern away from you because it is always rounded to 4MB extents, by default. You don't have to deal with UUIDs, or worry about what partition table you are using. I would say LVM can actually replace partition tables if its support was better developed.

You get snapshot functionality even though that is not all that useful to everyone, but you can also delete, and add, and rename, and basically also move, partitions on the fly. That is a risk, if it becomes too easy. And it is very easy to delete stuff. But it is not as easy to target the wrong logical volume (LV) using tools such as "dd" or "shred".

Mostly the graphical tools for it don't exist. But with sufficient aid, it is already pretty usable today, and I think more usable than the utterly insane way of doing business with UUIDs that is so prevalent everywhere. I mean, even Grub uses UUIDs for LVM partitions. What for? They have a unique name. Unless you rename them and then don't run update-grub, nothing can ever happen to it.

I would say it is too easy to remove and rename and displace LVM volumes. It is too easy to create and destroy snapshots, in that sense, and destroy planets.

But that is really the nature of a software-only solution. You can't really help that.

I would prefer myself to have something BIOS/firmware based. But perchance a day may come that all Linux disks start with a PV (header) (or alternatively a LUKS header) and that BIOSes could read volume group information, I don't know. It is pretty awesome the way it is and personally I try to stay away from any form of regular partitions these days.

Also don't forget that LVM striping would also increase performance.

And it is much much easier and user-friendlier than Linux software RAID via mdadm. Even the lower level tools like dmsetup <status> and dmsetup <table> are just more friendly to a user than that awful mdadm program.

I guess that also uses the device mapper. Yet I would rather work with dmsetup than mdadm, myself. I had a system running for months, years, and to this day I still don't know how to administer it (or I have forgotten all the commands I used before). Mdadm is not for newbies, it is for people with printed manuals right next to them.

And if you have 4 4TB disks in your system, I don't think you really qualify for being a regular home user, and you might very well think about the organisation you want it to have, but that's just me. Of course, video professionals usually have a lot of disks, or even amateurs, sometimes desks littered with external drives. Yet if you are on Linux you have the option to give just a little bit more organisation to it.

If I was this user I would follow the advice of combining those disks and then depending on forum availability (or the one advizing it) for further support. LVM has a hint of stuff going wrong, particularly if you used more advanced stuff such as thin LVM, (thinly-provisioned-LVM) as the maintainers and developers do not seem to care much about data safety or precautions against mis-use.

Yet using regular partitions is not of this day and age, and the difficulty you have if you ever want to change anything to it (add a new partition, shrink one) are just outstanding. I will use the soft wrapper of LVM, thank you very much ;-).

Any case, perhaps that is just personal. But I don't like fighting either the difficulties of GPT (needs an extra partition to boot, which can be un-nice) or MBR (always have to worry about how many you have, and when you start an extended partition, and how to divide your partitions among them, particularly if you also want or need to use LVM). In the end, since a PV allows for booting, I have chosen to do away with partitions altogether for this system.

That is a novel thing and the Grub people are apparently quite unwilling to facilitate its inclusion, but I am running a patched version of Grub that allows booting an unencrypted PV :p.

LVM had allowed for the inclusion of a boot loader into its areas for the longest time, and still, Grub does not support it. I do not know why. They won't do it. The patch is ready, and needs a little more work. It needs a little feedback and some choices made, and then a little extra safety, and then it is ready for prime time (it already is). They could have it done within 2 weeks if they wanted, but yeah.

Next up my ladder and my agenda is doing the same for LUKS. We could have bootable LUKS systems without partitions within a month, if people wanted it.[/COLOR]

---

### Post by aaron50 on 2016-06-20
All,

Thank you for your responses. If anyone is still following this thread, i am having trouble understanding something. I have used gparted to format my disks and used ext4. Now i have used samba to create a share directory from 2 of the disks, my two non backup disks. When I am in my windows computer, and right click on properties of the disk, it is showing a total capacity of 3.58TB, i understand that portion of things, the whole 1000 to 1024 scale the manufacturers use. The thing i don't quite get is that the file system says NTFS, which i guess samba is relaying because windows can't read ext4, but the used space says 186GB and free space of 3.39TB. The drives are completely empty and i think i used the whole drive as a partition, I cannot think of anything that could be using that much space. Did i do something wrong? Thanks for the help.

---

### Post by TheFu on 2016-06-20
Many file systems reserve some storage for root, since having a 100% file system can be really, really bad. Only root can write to this reserved space. I think it is usually 5%.  For purely data partitions, you can alter the reserved storage with tune2fs for the specific file system type, though I wouldn't make it zero, since it is used to fix file system fragmentation.  The manpage has more info.

Plus formatting a file system uses a little storage and there has to be some reserved space for journals.

I didn't run the numbers. You should.

---

### Post by aaron50 on 2016-06-20
So nothing's seems too out of the ordinary I guess.

---

### Post by xen3 on 2016-06-20
Here's running the numbers :p.

```
resblocks=$(tune2fs -l /dev/sdb1 | grep "Reserved block count" | sed "s/.* \(.*\)/\1/")
blocksize=$(tune2fs -l /dev/sdb1 | grep "Block size" | sed "s/.* \(.*\)/\1/")
echo $(( resblocks * blocksize / 1024 / 1024 / 1024 ))
```

Will give you the total reserved space on /dev/sdb1 in rounded gigabytes :p.

ps where did you end up mounting the drives? Just personal interest.

---

### Post by aaron50 on 2016-06-20
for the time being, as i am playing with them i mounted them at External1, External2, External3, and External4. I will be changing the naming convention though, probably to something like /External/Main/Public and /External/Main/Private, then /External/Backup/Public and /External/Backup/Private

---

### Post by TheFu on 2016-06-20
There is a limit to how long a file system object can be, so I'd encourage you to shorten things, if you can.  I've run into this at work before - out solution was to compile a special kernel and libc to support longer filenames than the default. We had to recompile about 500 other software projects, some commercial, due to this as well.  For commercial products, paying for source licenses gets expensive, just sayin'.  Saving a few characters now could make a difference later.

For example, the Plex Media Server guys use 71 characters when 14 would have worked just as well.
"**/var/lib/plexmediaserver/Library/Application Support/Plex Media Server**" is the first level where anything happens.  Everything starting from the 3rd level is useless, at least on Windows and Linux. Can't speak to OSX. /var/lib/plex would have been just a good.

Sorry - just a pet peeve to me. Wasted characters that don't add anything for understanding or readability is just that, a waste.  You aren't anywhere near this, but perhaps .... /Ex/ would be sufficient and putting the backups on /Backups/ would be more expedient?  Then you don't need "Main" at all.  I'd shorten public/private too - actually I have to "pub" and "priv" - since Unix is case sensitive, I use lowercase for directories, almost always.  Not important, until it is important.

Anyway, just some thoughts based on 20+ yrs of experience.

---

### Post by aaron50 on 2016-06-20
Fu and Xen3, i genuinely appreciate all of your help. I have very little knowledge of all of this, and can really appreciate anything that you have to offer.

Fu, your point makes a lot of sense, i have had this problem at work occasionally, so i will be shortening my directory names and putting my backups in a completely seperate directory to get rid of the main and backup sub directories. 

Thanks again!

---

### Post by xen3 on 2016-06-21
Typically that is not a very good idea unless you run into trouble, but I guess the limit is something like 256 characters? The tersity of the Linux system makes it utterly incomprehensible for anyone who has not already vested a huge amount of time in it. "/etc" is wholly meaningless as a word. "/usr" could better have been "/user" if that meant anything. "umount" is just an abbreviation of "unmount" but creates issues because you cannot actually "speak" of "umounting" as if that was a verb, it's not. If the Linux system is limited to such short paths, then that is a problem with Linux, not with long paths.

Even something like "Users" is much more user friendly than "home". "/sys" and "/proc" are by themselves pretty incomprehensible. You say something about readability mr. Fu, but readability also implies comprehensibility and we are not computers unless we have already spent 20+ years in this system ;-).

On my shell server somewhere my home directory starts at "/nfs/vsp/host.nl/x/xen/" and that is just the way it is. Then the place where I work most of the time is at /public_html/hideout/wp-content/themes/motion which makes the entire "URL" something like /nfs/vsp/host.nl/x/xen/public_html/hideout/wp-content/themes/motion/ and there's no changing that, unless you wanted to shorten "public_html" (but I cannot do so).

Good organisation actually makes for a more proficient worker. That's all I can say. And I know the Linux system is the most badly organized thing I have ever come across in my life.

Just stick to what you want, mr. Aaron. Don't do what others tell you to do, just because it is supposed to be "better". Unless you entertain deep hierarchies of stuff, which you won't if it is just your own user generated content, in that sense (and not programs or applications with deep trees) you are never going to run into this problem, ever.

What if you had another backup directory on this system? Now /backup doesn't make sense anymore and become incomprehensible. That is the purpose of good naming. You made an excellent choice from my perspective (except with the uppercase names (initial caps)) and now you change your opinion because someone says so (like you've done before, here, in that sense).

For example, the Java Maven system puts java source files in this tree:

project/src/main/org/domain/package/subpackage/sourcefile.java.

And there is no other way to organize that unless you go and mess things up. For, it also needs a "test" tree:

project/src/test/org/domain/package/subpackage/sourcefile.java --- to separate unit tests from the main sources.

What you generally do on Linux is to create symlinks to access the deeper trees, but shortening the trees themselves as much as you can is not best practice at all.

That is throwing away your organisation just for the sake of short pathnames. By the way, perhaps a nice hint:

If you set in your .bashrc the following:

set -p

Then when you follow symlinks, the location gets replaced (in the console) with the real path. For me much preferable in a general sense.

/ex/ is not sufficient at all, at least not when you want anyone to know what it means. If you go about your business like this, you are going to run into regular occasions where you don't remember what was what. And now you have to spend time re-acquaintancing yourself with your own system, because you chose incomprehensible names. Typically I would recommend anyone to choose names that are about 8 characters in length (max) for individual filenames. For path components.

On that shell-server I use very short symlinks to make it easier to upload stuff etc. So "files" is shortened to "f". "images" is shortened to "i". So I can upload stuff with :p/f/i and this links to public_html/files/images, but that is of course not the actual path. There is a reason for having short names, but there is also a reason for having proper names. I wish I could replace public_html with just www, but that is not my choice to make :p.

The only thing you can possible gain from shortening names like that is confusion. These days the root of the FHS (file system hierarchy) is littered with more and more componenents. Previously it was half of what it is now. It is a mess and getting worse every year.

Now we have 3 library directories: /lib, /lib32 and /lib64. Great. One of those only contains a single file. Great organisation there, absolutely. You create a top-level directory for a single file, outstanding organisational capability. Hats off. The other one contains a very limited number of files as well.

/proc and /sys serve basically almost the same purpose. They are two filesystems with a more or less identical purpose, but they cannot be combined because it would require organisation and break backward compatibility, and now we have a /proc/sys/dev, and a /sys/dev, and a /sys/devices, and does it still make sense this? Of course not.

If there is one thing Linux people can't do, it is organize stuff.

And "udev" makes so much sense (I have no idea what the u stands for) and dbus makes so much sense (no clue either, really) you would think dbus meant "device bus" but it is an interprocess communication system, so I don't know.... Strangely enough, the only project that really breaks away from this, is NetworkManager, but they are also the only one I've seen that actually asks their users for their opinion.

Linux developers generally do not ask the actual userbase for their opinions. Their opinions are not catalogued or... inventorized. So Linux developers think they know what is best for everyone, without ever having asked anyone.

Then, if you are a person with an opinion, they treat you like scum, even though many users would feel the same way if only they were asked for their opinion.

And all of this just to get around a technical limitation that has no basis in actual computer capability or memory availability? Something that could be changed within a month across the globe?

By the way, the current package of PlexMediaServer doesn't have that library hierarchy. But it has others, for instance

./usr/lib/plexmediaserver/Resources/Python/lib/python2.7/site-packages/lxml/isoschematron/resources/xsl/RNG2Schtrn.xsl

The first part is Linux dependent. The middle part is the program's structure. The latter part is Linux's structure embedded in something that doesn't agree with it, or rather, it is an application program packaging embedded in something that doesn't agree with self-contained application packages.

Normally you would have something like (on a Windows computer, for instance (or DOS)):

C:\Library\PlexMediaServer\Resources\Python\.......... but Python expects a full hierarchy starting from some root, and it won't work unless it can reference itself as /lib/python2.7/ starting from that root, adding two more unnecessary components. This is because it also has a reference to /include/python2.7/, meaning that it is packaged starting from the regular /usr. Because Linux packages are not self-contained, they require the full damn FHS hierarchy (at times) to be present the moment you want to put it somewhere else, which is really the biggest reason we still don't have the ability to run applications from USB stick (for example) and we won't for years to come, even though the technical hinderings can be solved, but no one is actually doing it that has any say over the matter. One such problem, and pardon me if I am mistaken, is that many applications actually link using absolute paths, and they won't work if they are not in the exact right spot in the FHS. It would be dead easy to fix that, but no one has done so.

The result is incessant dependency on the entire system, and if you then want to "concatenate" different such programs together (include one in the other, and in another, and in another) you get a path in which the FHS is repeated endlessly ;-).

So this python library is now dependent on the path leading up to it. The path leading up to it is actually part of the package. That's like a computer that will only work if it is in the right country, or a chair you can only sit on if it is in the right building. It is incomprehensible that people make such choices, but they did, and they do. You see the same ludicracy in NFS, and now I will hold my waffle ;-).

---

### Post by TheFu on 2016-06-22
TL;DR ... but it isn't Linux, it is Unix and Unix has had something called "standards" which, once read and understood, make perfect sense.  If they don't, read them again and again and again until you see it.

For example, there are very good reasons for /usr, /bin, /boot, /etc, /var directories. There is a standards document which describes them. Linux has slightly different standards, but many were inherited from Unix.  Which is what the history of Linux demands.

/usr has ZERO to do with /user or /home.  [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

The great thing about Unix is all the flexibility it provides.  Do what you like on your systems, but then you get to live with the fallout.
I appreciate the discussion. Different views on things keeps a health dialog going. We each get to decide what we will do or not do based on our experiences.

For long paths, I use environment variables or cdpath, whichever makes more sense.  When it comes to scripting languages, the best practice is to use an environment management tool - perlbrew or rvm or rbenv - certainly python has something similar (I don't do python).  BTW, if you are writing cross-platform code, always use '/', not '\\'.  Windows does the right thing. Thankfully, I haven't had to program anything on Windows in years, though I did make a living doing it for about a decade, along with OSX, and 12 other OSes.

---

### Post by xen3 on 2016-06-23
That's being called a Dinosaur ;-).

We can also go back to the Victorian age and try to make those standards work for us today. It won't work, but Linux (Unix) people would have you do it.

If /usr has zero to do with /user, then maybe they shouldn't have made it an abbreviation of /user.

The only "environment management tool" I have yet used is ant and maven for Java ;-).

Both programs, especially Maven, with some of the worst documentation websites you have ever seen, a wiki that is almost completely unorganized, and in the end it is so simple, but the documentation makes it so very hard that I had to buy books on them in order to get up to speed soon enough.

And maybe /etc (I am sure it is just an abbreviation of /etcetera, as in, "all of the other things") -- would have been better called /conf or something, but that is too long to type, obviously.

Yes the only reason for these things being so short is that you have to type them so much as a system administrator the way it is. I never said there were no reasons for it. I am saying those reasons exist within other design choices that are equally bad, but that make sense as a whole provided you don't actually want to have a good time in it.

In Windows, if given an equal shell to bash with all the tools, I would probably still do at least 50% of my file management in the GUI. In Linux, with the bad systems we have, I do at most 30% in the GUI. Linux is for me the challenge of automating as much as possible because:

a) The GUI is poor
b) Scripts are powerful
c) Scripting is fun
d) Setting everything up once and for all might take the "negative dependence" away on those GUI tools AND, if your solution works for you from the shell, you  then have the ability to start "GUIizing" it. Mostly it means you are writing libraries as shell scripts (in the beginning) and those "libraries" can be called from other places as well.

So there is a progress and there is a path forward but it takes a vast amount of work. I basically spend almost all of my time trying to configure Linux.

Today Bash bit me again. It took me an hour or two, almost, to realize that I had again fallen into the trap of trying to change a variable from something that was being executed in a sub-shell.

Another time which I haven't solved is that a call that worked in the shell (tr [:upper:] [:lower:]) didn't work when invoked from a script. I gave up and used Awk for it.

---

