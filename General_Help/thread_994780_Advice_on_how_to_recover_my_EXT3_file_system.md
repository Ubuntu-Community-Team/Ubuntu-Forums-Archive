---
title: "Advice on how to recover my EXT3 file system"
date: 2008-11-27
forum: General Help
---

### Post by stack_ on 2008-11-27
Hello

I have had my 500gb HDD split into 2 partitions for a while. Windows (NTFS) residing on the 1st partition, Linux (EXT3) residing on the 2nd. 

I recently took the very poor decision to use a Windows utility supplied on a magazine coverdisk (Paragon Partition Manager) to resize the EXT3 partion from within Windows. I first decreased the size of the windows partition down to 250gb and then increased the size of the ext3 partition to 250gb (from 90gb). The operation completed successfully.

However, the system would then not boot! complaining of a bad superblock. I booted into Ubuntu with the live CD and reinstalled grub to the disk's MBR. This allowed me to begin the boot process from the EXT3 filesystem. The Ubuntu logo came up and there was some progress, however there was a serious error (I did not note it down, unfortunately) and I was dumped into a maintenance mode shell and advised to run a manual fsck.

I booted the system with the live CD again and ran an fsck -y ... this ran for 3 solid days, complaining of inode issues. I eventually Ctrl-C'd the process as I imagined it was broken.

Now, I am stuck ! I cannot boot into my EXT3 partition !

I need the advice of a guru on how to recover my file system ! Help is invaluable and appreciated beyond measure as this partition contained 4 years worth of non-backed up photos and my wife's entire university course ! :-(

I have learned a lesson here, however I am willing to go to absolutely any length to recover the data. Incidently, the one file I need to recover from the partition is a 27gb VMDK (VMWare virtual disk image) file. 

Many Thanks
Chris

---

### Post by Herman on 2008-11-27
I think TestDisk - [COLOR=#c0c0c0][TestDisk - CG Security]("http://www.cgsecurity.org/wiki/TestDisk") [/COLOR]will be your best chance.

You can install TestDisk in your Ubuntu Live CD, 
```
sudo apt-get install testdisk
```It will disappear as soon as you shut down the Live CD sessions of course, but if it has done it's job then you're finished with it anyway.

TestDisk is also available already installed in [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/").[GParted -- LiveCD]("http://gparted.sourceforge.net/"),  [System Rescue CD]("http://www.sysresccd.org/Main_Page") or [Knoppix]("http://www.knoppix.net/").

You can use TestDisk to scan your hard disk and find the starting blocks of your old file system as long as it hasn't been overwritten already and restore the information that points to them to your partition table.
With luck that will restore your access to your files again.
If successful, you should be able to mount the old file system in your Live CD and take a look around and see if your files are okay.
You will need to restore GRUB again to get it to boot if the files are still okay. Otherwise, maybe you'll be able to at least rescue some of your files using the Live CD and a USB hard disk or flash memory stick.

In case it's helpful, here's my link about TestDisk, which itself includes further links, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html").

Good luck, 
Regards, Herman :)

You may wish to take this post with a grain of salt and wait for a second opinion about that or a confirmation.

---

### Post by hyper_ch on 2008-11-27
as it sounds, ext3 just didn't get setup properly... my advice would be

(1) get another harddisk same size or larger than then mirror the contents of the current one onto the new one

(2) work on the mirrored harddisk (unplug the real one) for recovery.

you can do the mirroring simply by booting the live cd and then issue:

```

sudo dd if=/dev/sda of=/dev/sdb

```
where SDA is your original disk and SDB is your new one.

That will do a 1:1 copy of it.

---

