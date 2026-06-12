---
title: "Best way to clone/copy a hard drive?"
date: 2015-12-20
forum: Hardware
---

### Post by Telxonator on 2015-12-20
I have recently run a SMART scan on my 1TB Seagate drive, and found some pending sector counts and offline uncorrectable were both showing raw values of 1. From what I read, this is a sign of more trouble to come, so I ran one of the tools on the Ultimate Boot CD to scan and fix it, it appears to have been a success, and those errors are gone, but I want to have a good backup in case it comes back.

I had to go through hell to get this GPU to work (seems to always be the case), and I have a few other custom hardware settings too, plus my files and software, of course. What is the best/easiest way to move all this to a new HDD so I can just plug it in and go? I was contemplating going from the 1Tb SATA drive currently in the system to a 320Gb, being there is only 90Gb used on the 1Tb, but it looks like that is going to be a pain in the ass to do, so I'll likely just go with another 1TB from a more reputable brand, like WD. (heard too many people say Seagate is prone to this type of thing)

I know there are quite a few good cloning tools on the UBCD, but I've never done this before and want to make sure I don't screw it up. 

To sum up, I just want to move my programs (with their settings intact), files, and the OS with it's custom settings intact to a new drive with a minimal amount of fuss. System is Kubuntu 14.04 x64.

---

### Post by sudodus on 2015-12-20
If you want to do a simple cloning, you should make sure that the target drive is at least a big as the source drive. The cloning will fail if the target is one single byte smaller, and the size can vary (is not exactly 1 TB) in drives that are nominally 1 TB. To be sure you should get a drive of 1.5 TB or bigger. I would use ***Clonezilla*** for the cloning.

If you want a reliable drive you should get one that is designed for it. Such drives are more expensive, but they will usually last much longer. You should also make sure that it is well cooled, and not subject to vibrations.

If you want to move your system to a smaller drive, it can be fairly easily done if it is a pure linux system, but more difficult if Windows or MacOS is involved.

A pure linux system can be moved without cloning. You can create the new partitions with file systems (and 'linux-swap'), copy the files including the permissions with ***sudo rsync*** to the corresponding partition(s), and finally install the bootloader into the new drive.

---

### Post by RobGoss on 2015-12-20
Great advice Clonezilla does a good job of backing up the whole drive. Here's the link [http://clonezilla.org/](http://clonezilla.org/)

---

### Post by weatherman2 on 2015-12-20
I also use Clonezilla as well.  It has a clunky user interface but seems reliable - and is always free.  It has handled some pretty tricky clones for me, including a dual boot Windows 8 + Ubuntu LVM.

You can also use Clonezilla to make image backups.  That is, you can use say an external drive or even a NAS to store a copy of the image of your whole drive, without devoting a whole hard drive to being your backup.  Obviously this has big practical benefits.  If you already have a big backup drive, you can simply use it to save backups.  The downside is, you have to take time to restore the image backup if your original fails.

I also use True Image from Acronis - paid software that is a lot easier to use than Clonezilla.  Sometimes it is on sale for pretty cheap.  I use the "rescue CD" (booted from USB) most of the time these days which has all of the functionality I need  to clone or do image backups - this is a Linux-based boot version that doesn't need Windows at all.  True Image can also make incremental or differential backups so you can have snapshots over time of your disk and save only the differences.

---

### Post by weatherman2 on 2015-12-20
But both Clonezilla and True Image require you to shut down the OS and boot something else to make your clone or image backup (because if you simply backup the OS while you are booted you could wind up with an inconsistent backup).  If you want to make "live" backups of your Linux OS over time, you might look at using LVM at least for the root / partition.  LVM supports snapshotting of the partition, so you can make a snapshot and backup the snapshot without shutting down the OS.  Then you can use rsync to backup your partitions on the fly.  I like to separate my root / partition (and keep it smaller, maybe 20GB or 30GB tops) from my data partitions to make them easier to back up.

Here's a nice article about how to use rsync to do an Apple Time machine-like backup of Linux:

[https://blog.interlinked.org/tutorials/rsync_time_machine.html](https://blog.interlinked.org/tutorials/rsync_time_machine.html)

If you use LVM, you can make live backups of everything as often as you like using rsync -link-dest to save only the changes.

---

### Post by Telxonator on 2015-12-20
The main thing is I don't want to have to reinstall/reconfigure my software and hardware settings, just move it to the new drive. This install is pure Linux, no dual boot, no other OSes, just Kubuntu, and no encryption on the drive or special partitioning, it was all automatically done at install. It took me 2 days to get the GPU working, and firefox has a bunch of custom settings I'd rather not redo, plus various tweaks, etc. The pics/docs/etc are backed up already, so I could move them separately if needed.

Remember too, I have never done this, so just saying "do this thing" without pointing to a tutorial or instructions is like a surgeon telling Joe Blow how to do an open heart surgery by simply saying "cut him open". (and I am  reading up on it as we speak, it's just something I've never done, but am willing to learn)

---

### Post by sudodus on 2015-12-20
- The easy way is to use a cloning tool, for example Clonezilla, and clone the whole drive to another drive of at least the same size.

- If you want to move to a smaller drive, it will be more complicated, but still possible with some help. (If you move all personal data before copying, it will be much faster (and easier)).

Please decide which way you want to go, and you can get more detailed instructions after that :-)

---

### Post by Telxonator on 2015-12-20
Looks like I'm going to clone it to either a 320GB or 500GB drive, depending on what the SMART tests return. I have only 90 so GB used on the current 1TB drive. UBCD has clonezilla on it, so I am good there.

---

### Post by sudodus on 2015-12-20
You can't clone from 1 TB to a 320GB or 500GB drive. You can only clone to a drive of the same size or bigger.

So you need another method, for example using rsync. Is that what you want?

---

### Post by Telxonator on 2015-12-20
Ok, that's what I'll have to do, can't afford a new drive now. SMART tests on the 500 and 320 GB drives came back good, no errors or signs of trouble.

---

### Post by weatherman2 on 2015-12-20
You CAN clone to a smaller drive...IF you aren't using the full amount of space.  If you have a 1TB drive and are using only 200GB of space, you can clone it to a 320GB drive.  But it may not be simple.  If you want to use Clonezilla, you'll have to shrink the original partition(s) to be smaller than 320GB total before cloning.  It will be easier if you can shrink down to 500GB and clone to the 500GB drive.

If your original Linux install was a simple root partition (/) with everything and a swap, then it should be fairly easy to shrink, but it *IS* dangerous - something could go wrong especially on a failing hard drive.  You can shrink - by booting a live Ubuntu - using the Gparted tool.  It may take a lot of time to shrink depending on how much data you have, and you CANNOT INTERRUPT the shrink!  Otherwise, you could hopelessly corrupt your partition.

I would rsync copy your important data somewhere first, then try Gparted to shrink the / (root or OS) partition, then try cloning.  At very worst, you can clone manually using Gparted (which can copy partitions) but then you will have a little extra work re-installing Grub and editing your fstab file on the clone.  If you have only a single root partition + swap, all you have to do is copy that one partition and make a new swap on the new drive.  You can re-install Grub on the new drive using a Ubuntu live boot and a few commands - do a web search for "ubuntu grub chroot ".  The chroot method works well for me, have done it many times.

True Image can clone to a smaller drive automatically if the use space is small enough to fit on the new drive, but I've only tried it with Windows disks, not Linux disks.

---

### Post by SuperFreak on 2015-12-20
I think [REDO]("http://redobackup.org/") will work for the smaller drive provided the actual partition(s) you are cloning are smaller than the smaller drive. It has a simple graphical interface that is easier to use than Clonezilla in my opinion

---

### Post by Telxonator on 2015-12-20
It is just a simple partition with swap, the total used space on the main partition is around 70 GB. as far as the drive failing, I have no clue now, it's not showing any errors or bad attributes in the smart info, and the program I ran from the boot cd tools seems to have fixed it. I could probably just keep an eye on it and make sure any irreplaceable files are saved to external drives or the NAS, which they already are.

---

### Post by sudodus on 2015-12-20
I'll try to give you a list of tasks.

***0. Backup***

 You can use ***Clonezilla*** to make a compressed image of the 1TB drive into the drive, that you do not intend to use as the new system drive. The image will be a directory with a number of files, where the data about partitions, file systems and files are stored. The free space (unused data blocks) will not be copied, and files will be compressed, so this image will be smaller than 90 GB.

***1. Decide how you want to use the drive***

Decide what you want, and then create partitions with file system(s) and swap. I suggest that you make it easy for you and use an MSDOS partition table, default in ***gparted***. Use **ext4** file system(s) a swap partition just a little bigger than the RAM (in Gibibytes) if you want to hibernate, otherwise you can use less swap, maybe only 1 GB.

***2. Boot from a 'third drive'***

All the partitioning and copying should be done, when you have booted the computer from a 'third drive', for example an Ubuntu install drive or some kind of linux rescue drive with a modern version of linux, so that you have good versions of gparted, rsync and grub.

***3. Partitioning***

[COLOR="#0000CD"]a. The easiest method is to make one big root **/** partition (and a small swap partition at the end of the drive)[/COLOR]

[COLOR="#696969"]b. It is a good idea to separate the system and the data.

b1. One way is the make a separate home partition **/home**. In that case the root partition can be 20-30 GB.

b2. Another way is to make a separate **data** partition (with the label **data**). In that case the root partition can be 25-40 GB, and you should be very active in storing your documents, pictures, music and videoclips in the data partition. (Otherwise the root partition with /home as a directory will soon be full.)
[/COLOR]
***4. Copying directory tree(s) with files and permissions***

Start by reading the manual page ```
man rsync
```

[COLOR="#696969"]a. If you intend to use a /home partition, you start by copying /home to the new home partition.

b. If you intend to use a data partition, you should start by copying the documents, pictures, music and videoclips to the data partition.

c. Then[/COLOR] copy the system to the root partition (and exclude the directories and or partitions that you have copied elsewhere)

Start with a dry run (the -n option). Notice the final / at the source-dir. It makes a difference in this case

```
sudo [COLOR="#696969"]--exclude=PATTERN[/COLOR] -Havn source-dir/ target-dir
```

[COLOR="#696969"]where PATTERN describes what you want to exclude, wild-cards are possible (*)[/COLOR]

If it looks good, you remove the n and run the real copying

```
sudo [COLOR="#696969"]--exclude=PATTERN[/COLOR] -Hav source-dir/ target-dir
```

***5. Install the boot-loader***

See the following link, which describes how to install the grub2 bootloader in different situations.

[Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by Telxonator on 2015-12-20
Ok, first off thanks for all the help, second, I know when I'm over my head, and this is it. If I continue, I'm going to ruin something or regret it. I have a friend that's really good with this, and I may have to call him over and have him help me, or bite the bullet and reinstall it from scratch. at least I know what the video driver is that is working, so that shouldn't be a big issue with what I learned from that fiasco. All of my pictures and documents are now on an external drive, and will soon be on the NAS once I get it booted up, so I will have 2 backups then. Plus, I want to see if the drive develops any more problems, since it is now showing no bad attributes and passed the self test. (It never failed the self tests)

Sudodus:, it's not that I don't understand your instructions, I'm not confident I can pull it off without messing something up. I am thankful for your help and appreciate the time you have taken in doing so. I just know my limits, and am still learning all of this.

---

### Post by sudodus on 2015-12-20
It might be a good idea to make a fresh installation. With your current experience it will probably be much easier and also better than what you did last time :-)

---

### Post by Telxonator on 2015-12-20
I agree, although if I had my friend help me, I could learn something new. Heck, when I was first using Linux, i was terrified of using the CLI, but now when I need to use it, I jump right in. In time I will be good with other stuff too, it's just learning as I go.
Thanks to places like this, the people in them who help out, as well as other Linux loving friends, I have learned quite a bit. 

I really do appreciate your time and patience with me on this endeavor, and look forward to learning more, and hopefully sharing what I know with others.

---

### Post by sudodus on 2015-12-20
It is a good idea to think twice and discuss with your friend before you decide what to do. As long as you have a good backup of all important files, you need not worry too much about damaging the system. So maybe it is a question of how much time and effort you and your friend want to spend on this project.

Whatever you decide and do, please keep us informed in this thread, and we are happy to help :-)

---

### Post by C.S.Cameron on 2015-12-21
I understand that with Clonezilla only the destination partition needs to be at least as large as the source partition, not the drive sizes as with dd.

If I recall correctly from the last time I used it, grub had to be reinstalled when only cloning partitions.

---

### Post by Bucky Ball on 2015-12-22
[fsarchiver is another option]("http://www.fsarchiver.org/Main_Page"). You can archive a partition from a running install! (i.e. you can archive the Ubuntu you want to use on the other drive while you are running it). Then you restore the archive to the partition you are wanting the identical copy on. And it is identical. This applies to OS partitions or data. Doesn't matter.

I'm currently using 14.04 install on my new SSD which is identical to the install on my hard drive. Did it with fsarchiver about a week ago and very happy with result. :)

Apologies if someone has already mentioned this option. I used to use Clonezilla but have recently swapped to fsarchiver.

---

### Post by kansasnoob on 2015-12-22
Can you post a screenshot of Gparted so we can see exactly what type of partitioning we're dealing with? I frequently copy a Linux OS from one drive to another using nothing but Gparted, then about the only thing left to do afterwards is to fix grub.

But really we should see what we're dealing with so we can give more specific suggestions.

---

### Post by Telxonator on 2015-12-22
I will consider these options, and will see what can be done. Right now the drive is still looking good, no failing attributes or tests so far. I will likely just reinstall the whole works if I need to, and continue to monitor the drive.

The fsarchiver looks like a good option, I will read more about it as well.

Thanks again to all who helped, and I will try to keep you updated as to my progress/results

Edit, here's the screencap of partition manager:
[http://i981.photobucket.com/albums/ae297/telxonmaster1/snapshot1_zpsrsxvy0am.png](http://i981.photobucket.com/albums/ae297/telxonmaster1/snapshot1_zpsrsxvy0am.png)

---

### Post by weatherman2 on 2015-12-22
> **Bucky Ball said:**
> [fsarchiver is another option]("http://www.fsarchiver.org/Main_Page"). You can archive a partition from a running install! (i.e. you can archive the Ubuntu you want to use on the other drive while you are running it).

If you use an LVM you can use rsync or dump (or other tools) to make an image of a snapshot of a live, mounted file system.  But you still need to use an LVM even with fsarchiver to make a reliable copy of a live, mounted filesystem, according to the fsarchiver Wiki you linked to:

*"FSArchiver is safe when it makes backups of partitions which are not mounted or mounted read-only. There is an option to force the backup of a read-write mounted volume, but there may be problems with the files that changed during the backup. If you want to backup partition which are in use, the best thing to do is to make an LVM snapshot of the partition using lvcreate -s, which is part of the LVM userland tools. Unfortunately you can only make snapshots of partitions which are LVM Logical Volumes."*

I have mostly switched to using rsync with LVM to backup live file systems.  The --link-dest option lets you do incremental backup with hard links to make snapshots-in-time backups without redundant disk space, just like Apple's Time Machine.

---

### Post by weatherman2 on 2015-12-22
> **kansasnoob said:**
> Can you post a screenshot of Gparted so we can see exactly what type of partitioning we're dealing with? I frequently copy a Linux OS from one drive to another using nothing but Gparted, then about the only thing left to do afterwards is to fix grub.

Yes, as I mentioned above, I clone the same way sometimes with Gparted.  Besides installing Grub on the new drive, you may also need to edit your new /etc/fstab file (e.g. new swap partition will have a new UUID on the new drive).  It's easy for me to do it this way now, but I can see how the steps might seem complicated to a novice user.

---

### Post by Bucky Ball on 2015-12-22
> **weatherman2 said:**
> If you use an LVM you can use rsync or dump (or other tools) to make an image of a snapshot of a live, mounted file system.  But you still need to use an LVM even with fsarchiver to make a reliable copy of a live, mounted filesystem, according to the fsarchiver Wiki you linked to:

Only ever heard of LVM. Wasn't using an LVM so didn't apply I guess. No idea what it is. I didn't do any of this. Archived the running Ubuntu OS and then restored to a partition on the SSD. Worked perfectly. Identical copy. Only issue I had was getting it to boot from the original grub. Easy. :D

Suffice to say, I didn't use an LVM, whatever that entails ...

---

### Post by weatherman2 on 2015-12-22
If you clone a live, booted OS partition with many files, you risk making incoherent or corrupt copies of certain files  After all, you can't copy all of the files at one time, and some files may be being written to while you are copying them; the copy you make wind up being corrupt, or two files that go together may be in different states when you are finished copying all the files.

The solution to this problem is to make a "snapshot" - that is, freeze all the files in one state (not being written).  Obviously you can do this by simply booting another OS like a live USB Ubuntu, so then your original OS files are not changing because the OS isn't running.  But if you use an LVM to install the OS in a logical volume, you can use the built-in LVM snapshot feature to make a snapshot while you are booted.  Then, you clone the snapshot.

Cloning a live OS without the snapshot is possible but risky, just like doing a "hard shutdown" by holding down the power button when your system freezes up.  Usually it works, but once in a while it will cause trouble, so it's best to avoid it unless you have no other choice.  To me, it's not worth the risk of making a corrupt copy of the operating system when LVM is available.   LVM has other benefits beside snapshotting.  It takes some initial time to setup an LVM for a Linux installation, but once you do it is worth the extra benefits.

[http://askubuntu.com/questions/3596/what-is-lvm-and-what-is-it-used-for](http://askubuntu.com/questions/3596/what-is-lvm-and-what-is-it-used-for)

---

### Post by Bucky Ball on 2015-12-22
Well, I must have got lucky. Mind you, I just let the machine do its thing. I wasn't sitting there working on the booted OS while this was going on. :)

Anyway, back to it. We have Clonezilla and fsarchiver. There is also dd I guess, but that is completely unforgiving if you make a mistake.

---

### Post by sudodus on 2015-12-22
Don't forget rsync :-) It is not really more difficult than the other tools for copying a system to a smaller drive. You probably need to install the bootloader separately in any case.

---

### Post by yoshii on 2015-12-22
> **sudodus said:**
> If you want to do a simple cloning, you should make sure that the target drive is at least a big as the source drive. The cloning will fail if the target is one single byte smaller, and the size can vary (is not exactly 1 TB) in drives that are nominally 1 TB. To be sure you should get a drive of 1.5 TB or bigger. I would use ***Clonezilla*** for the cloning.

If you want a reliable drive you should get one that is designed for it. Such drives are more expensive, but they will usually last much longer. You should also make sure that it is well cooled, and not subject to vibrations.

If you want to move your system to a smaller(?) drive, it can be fairly easily done if it is a pure linux system, but more difficult if Windows or MacOS is involved.

A pure linux system can be moved without cloning. You can create the new partitions with file systems (and 'linux-swap'), copy the files including the permissions with ***sudo rsync*** to the corresponding partition(s), and finally install the bootloader into the new drive.

I agree with this except I think there's a typo:  

"If you want to move your system to a smaller(?) drive, it can be fairly  easily done if it is a pure linux system, but more difficult if Windows  or MacOS is involved."
I don't think that is correct.  

I believe the correction is:  **If you want to move your system to a _larger_ drive, it can be fairly  easily done if it is a pure linux system, but more difficult if Windows  or MacOS is involved.**
He explained in the preceding paragraphs why a smaller drive is harder than a larger drive.  I have done this type of stuff before which is why I am confident about this correction.  

Also I just wanted to add that gParted can copy partitions and it will even copy the partitions unique UID number.  This can make things slightly tricky because each UID is supposed to be unique but it's helpful until you edit the fstab because the UID number will match and therefore will boot.  As stated above, the copied partition can only be pasted into a space greater than or equal to the source size.  It takes a long time, but it does work with the operating system partitions that I copied onto separate drives.  You can use gParted to set the boot flags and stuff like that also, and to check for errors.  So it's pretty handy.  

gParted is available on a lot of Linux LiveCD's such as Puppy Linux and some of the Ubuntu LiveCD's except for Lubuntu, for example.  

Check the gParted website to get a modern version of gParted on it's own LiveCD.

---

### Post by sudodus on 2015-12-23
> **yoshi2 said:**
> I agree with this except I think there's a typo:  

"If you want to move your system to a smaller(?) drive, it can be fairly  easily done if it is a pure linux system, but more difficult if Windows  or MacOS is involved."
I don't think that is correct.  

I believe the correction is:  **If you want to move your system to a _larger_ drive, it can be fairly  easily done if it is a pure linux system, but more difficult if Windows  or MacOS is involved.**
He explained in the preceding paragraphs why a smaller drive is harder than a larger drive.  I have done this type of stuff before which is why I am confident about this correction.  

...

Everything is relative ;-)

I understand what you mean, but it was no typing error, only a bad explanation. Let me try again to explain my thinking:

It is easy to clone to a larger drive. Then tools like Clonezilla can do the work for you, and it would work also if Windows  or MacOS is involved.

It is more difficult, but still fairly easily done to move a system to a smaller drive, if it is a pure linux system, but more difficult if Windows or MacOS is involved.

A linux system can be moved (copied, but not cloned) with for example rsync and the bootloader can be installed without too much problems.

---

### Post by yoshii on 2015-12-23
OK sorry Sudodus.

---

### Post by sudodus on 2015-12-23
> **yoshi2 said:**
> OK sorry Sudodus.

No need to be sorry, on the contrary, I'm glad that the bad explanation was questioned, so that it could be improved :-)

---

