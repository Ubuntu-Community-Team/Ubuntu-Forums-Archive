---
title: "Did something stupid, now badly need help"
date: 2012-03-04
forum: Hardware
---

### Post by SeanCly10 on 2012-03-04
A couple days ago, I got the bright idea to try and install Windows in an unused partition on my primary drive. I knew that trying to install Windows alongside an already established Ubuntu install was problematic, but I had no idea just what it would do.

The Windows CD got only as far as identifying the extant partitions and telling me it would have to wipe the disk to install, and then I canceled the install. Unfortunately, once I rebooted into my Ubuntu install, my secondary storage drive and all its' contents were gone.

I figured out pretty quick that the data was probably still there, just that the partition mapping had been altered or removed by Windows. But after lots of fruitless work, I'm no closer to getting it back than I was when I started. I've tried TestDisk, parted, fixparts, gpart, all to no effect.

There's pictures of my kids on that drive that exist no where else, so I've got to do everything possible to get it back. Does anyone have any ideas, anything I can do? I'm moving rapidly towards the desperate stage.

---

### Post by MG&amp;TL on 2012-03-04
> **SeanCly10 said:**
> Does anyone have any ideas, anything I can do? I'm moving rapidly towards the desperate stage.

No ideas I'm afraid, but whatever you do, do NOT use the hard disk in any way. That's likely to further damage your data.

---

### Post by winh8r on 2012-03-04
Boot up a Live CD and run testdisk again, when you get to the first screen how much is showing as used on the disk? It will say something like 200GB/123GB meaning that of 200 there is 123 free.
 

Then select proceed

select Intel

select Analyse

Quick search

it should show something here (written in green if it is untouched) or in red if it is deleted.

It should default to the largest partition it can find and highlight it.

whatever is highlighted will be a good start

hit the  P key on the keyboard and it will list all the files it can see.

then go down the list using the arrow keys and hit the C key to copy them.

you will need to specify where to copy them to so you should copy them to the desktop on the live cd, then you can transfer them to a USB drive before you shut down the Live session.

If you dont get what you want in the first run there is an option to do a deeper search, which will often locate more.

If there is no result with searching the disk using the Intel option above then try running it using the "None" option as this may be the case if Windows installer has deleted the partition but not formatted it.

Run it again from the live cd, but do not try to write anything to the hard drive.

If that still produces no result then you could try using the photorec utility which is part of testdisk, just make sure to set it to search the whole drive and only to look for image type files (jpg etc.)

This might at least get the family pictures off there for you, again try it a couple of times.



If testdisk/photorec is not doing it then have a look at this:

[http://extundelete.sourceforge.net/]("http://extundelete.sourceforge.net/")

Let us know how it goes, and if you need any more assistance with anything too.

---

### Post by ahallubuntu on 2012-03-04
If what winh8r suggests doesn't work, take it to a pro and have them get your data off.  (And I also agree: DO NOT use that disk in any way!!!)  Consider it an expensive lesson.  It's not worth risking the loss of these priceless pictures.

The lesson you should be learning from this isn't "don't try experiments" but *ALWAYS HAVE BACKUPS* of important data.  ALWAYS - and on a second device.  If you'd had a backup, you wouldn't be stressing over this.

Even WITHOUT trying to re-install Windows, you were playing with fire by not having a backup of these files.  Hard drives can and do fail (mechanically and otherwise) WITHOUT WARNING and you could have lost *EVERYTHING* one morning just because the hard drive suddenly failed.  But in that case, you'd be looking at $500+ to try to recover your data instead of probably $100 or so just to have someone recover data from an erased partition table where the drive hasn't failed.  So in some ways, this may be a pretty cheap lesson for you. Some people have to learn it more expensively.

Good luck!

---

### Post by SeanCly10 on 2012-03-05
Okay, photorec managed to get several photos off the drive; not all of them, but several. Progress!

I ran through the first several steps that you posted, down to pressing P to view the files in the highlighted entry of testdisk, but all I get is the message "No file found, filesystem seems damaged."

Now, running with the 'None' options gets me two filesystems, one of them actually bearing my original drive name ('Storage', imaginative eh?), but trying to list the files on it results in the program crashing back to prompt.

So, now to try e2undel. Running the following command:
```
sudo e2undel -d /dev/sdb -s /dev/sda5/home/sean/Recovered -a -t
```
where sdb is the Storage drive, results in:
```
/dev/sdb: Bad magic number in super-block while opening /dev/sdb
```

Argh. ](*,)

---

### Post by kurt18947 on 2012-03-06
SeanCly10 I hope you're able to recover your irreplacables intact.  I've sorta been where your are but the data in question was not that consequential.  Going forward,  perhaps consider some sort of boot manager.  I'm have XP, Win7 and 3 Linux flavors all on the same hard drive.  Each thinks it's the only O.S. on the drive so there's less risk of of one O.S. or file system 'stepping on' another.  Here is what I'm using.  I have no stake in the software or company, it just works pretty well for me. I'm certain there are other perhaps better choices to accomplish the same task.

www(dot)terabyteunlimited(dot)com/bootit-bare-metal.htm

It also bypasses the 4 partition limit.  Like you, I have a 'storage' partition.  I'm able to for for example permit Win 7 to access the storage partition and Ubuntu to access the storage partition.  Win 7 and Ubuntu are each unaware of the other.

---

### Post by winh8r on 2012-03-06
It would also be good idea if you could copy or clone that damaged drive to another device and work on the copy, that way if anything goes wrong you will still have the original data intact.


The limited success with photorec tells you that the data is still there, so there is still hope to get it back.


You could run the live cd again and try:


```
sudo e2fsck -C0 -p -f -v /dev/sdb
```

this will check and repair the filesystem, although I am uncertain as to whether it will manage to work efficiently on a partition that has been partially formatted by a Windows install.

Might be worth a try though even if it just gets the problem with mounting /dev/sdb solved to allow further recovery.

---

### Post by SeanCly10 on 2012-03-07
> **winh8r said:**
> It would also be good idea if you could copy or clone that damaged drive to another device and work on the copy, that way if anything goes wrong you will still have the original data intact.


The limited success with photorec tells you that the data is still there, so there is still hope to get it back.


You could run the live cd again and try:


```
sudo e2fsck -C0 -p -f -v /dev/sdb
```

this will check and repair the filesystem, although I am uncertain as to whether it will manage to work efficiently on a partition that has been partially formatted by a Windows install.

Might be worth a try though even if it just gets the problem with mounting /dev/sdb solved to allow further recovery.

Sounds good...here's what happened:

```
e2fsck: Bad magic number in super-block while trying to open /dev/sdb
/dev/sdb: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

What does this mean?

---

