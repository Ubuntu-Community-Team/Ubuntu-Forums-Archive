---
title: "Ext2 Installable File System, xp claims needs formating?"
date: 2008-10-14
forum: General Help
---

### Post by sdowney717 on 2008-10-14
[http://www.fs-driver.org/](http://www.fs-driver.org/)

It works well mostly. On my main drive holding ubuntu, windows picks this up fine, view files, etc...
On my second drive, windows sees the drive as a drive letter, but claims drive not formatted, and then wants to format the drive.

Any one familiar with this ?

---

### Post by justleen on 2008-10-14
is it your swap partition by any chance?

---

### Post by sdowney717 on 2008-10-14
no, this is another ext3 partition on a separate ide drive.

I read the ifs documentation and it says if it was not cleanly dismounted or something, it will be a problem. How would I check it for errors?

I was wondering if when I used gparted partition editor under system menu to set it up, that maybe something should have happened that did not happen like a setting?
My ubuntu can work fine with the drive.

both my drives are ext3 drives.

If I selected the swap partiton of the first drive, windows will claim it needs formating, so I know what you mean.

---

### Post by justleen on 2008-10-14
strange.. did you select that disc to be avaible when you installed the ext2 driver?

Maybe try a windows-solution: reinstall the driver...?

---

### Post by meganox on 2008-10-14
Did you try this?  What's the output?

[http://www.fs-driver.org/troubleshoot.html](http://www.fs-driver.org/troubleshoot.html)

> **I have installed the Ext2 IFS software and was able to create a drive letter for a desired volume of Linux. But when I try to access that volume I get an error message "The disk in drive X: is not formatted. Do you want to format it now?" (Of course I don't want to!) Or the content of the volume appears, but when I attempt to write something I get an error message "Access denied". **

                              The ext2fs.sys driver did not mount that volume for some reason, or it mounted it read-only.             
                              Please run the mountdiag diagnosis tool, which you can download here: [mountdiag.exe]("http://www.fs-driver.org/download/mountdiag.exe") (updated, 07-19-2008).             
                              Please run it at the command prompt and give it the letter of the drive you want to examine, for example:
                mountdiag G:
The tool will give you a hint on how to resolve the problem. (Note: The mountdiag tool reads data only; it does not attempt to modify anything.)

---

### Post by sdowney717 on 2008-10-14
I rebooted linux and it reported it needed to check the drive.

So I need to reboot xp and see what happens.

---

### Post by meganox on 2008-10-14
Ubuntu will always check the drive if it is not cleanly dismounted from Windows (where it is mounted as ext2 i.e. journaling is turned off) - [http://www.fs-driver.org/faq.html#acc_ext3](http://www.fs-driver.org/faq.html#acc_ext3) - this might happen when Windows does not correctly recognise the drive through the IFS driver.

The IFS driver will also refuse to mount an ext3 drive in Windows if it has data in the journal, i.e. it was not cleanly dismounted in Ubuntu.

So let Ubuntu check the drive and restore the journal if necessary.  mountdiag.exe is still probably going to be the most help at this stage.

---

### Post by sdowney717 on 2008-10-14
What do you think?

C:\scanmodem>mountdiag m:
The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not
mount it because the file system has an inode size unequal to 128 bytes (inode
size: 256 bytes).
The only way to solve it is to back up the volume's files and format the file
system: give the mkfs.ext3 utility the -I 128 switch. Finally, restore all
backed-up files.
After that, the Ext2 IFS software should be able to access the volume.

C:\scanmodem>

a quick google brought up this discussion. Is there a way to resize without moving data?
Also, seems ext4 default will be inode size 256, so really ifs drives software needs to be changed.
[http://newsgroups.derkeiler.com/Archive/Uk/uk.comp.os.linux/2008-02/msg00041.html](http://newsgroups.derkeiler.com/Archive/Uk/uk.comp.os.linux/2008-02/msg00041.html)

[http://manpages.ubuntu.com/manpages/feisty/man8/mke2fs.html](http://manpages.ubuntu.com/manpages/feisty/man8/mke2fs.html)
quess not! Looks like they may have changed default to 256 inode size.

        -I inode-size
               Specify the  size  of  each  inode  in  bytes.   mke2fs  creates
               128-byte  inodes  by  default.  In kernels after 2.6.10 and some
               earlier vendor kernels it is possible to utilize  larger  inodes
               to  store  extended  attributes  for  improved performance.  The
               inode-size value must be a power of two larger or equal to  128.
               The  larger  the  inode-size the more space the inode table will
               consume, and this reduces the usable space in the filesystem and
               can also negatively impact performance.  Using the default value
               is always safe, though it  may  be  desirable  to  use  256-byte
               inodes   if  full  backward  compatibility  is  not  a  concern.
               Extended attributes stored in large inodes are not visible  with
               older  kernels,  and such filesystems will not be mountable with
               2.4 kernels at all.  It is not possible  to  change  this  value
               after the filesystem is created.
 

will partition editor have an inode size setting or will I have to manually run this?

---

### Post by justleen on 2008-10-14
no, no way to resize without data lose, since your resizing the actual block size..

---

### Post by meganox on 2008-10-14
Yes, until IFS is updated you will have to reformat.  If the drives main use is as a shared drive then just format it ext2 and try not to crash either OS too often.

---

### Post by go_beep_yourself on 2008-11-11
I had the same problem. How do you change the default inode size when using the Ubuntu installer to create the partitions?

---

### Post by go_beep_yourself on 2008-11-11
I'm reformatting my drives with this command. It should be usable in Linux with the driver when this is done.

$ sudo mkfs -t ext3 -I 128 /dev/sdb1

---

### Post by go_beep_yourself on 2008-11-11
After reformatting, I ran mountdiag.exe again, now I get this. It says nothing is wrong, but I get "write protected" when I try to copy or move anything to it (see screenshot attachment).

C:\>mountdiag.exe Z:
The volume has been mounted and has the type of file system: EXT3.
There does not seem to be any problem with it.

C:\>

---

### Post by dakira on 2008-11-11
This is really really sad. IFS-Drives has not been in development for quite some time so we shouldn't expect any updates from them. Are there any other tools that are as convenient to use?

I am not willing to change the inode-size and I can't use NTFS because I need ext3 filesystem features (like hardlinks) which are not supported by NTFS.

I just wrote the author.. if I get a reply I'll of course post it here.

dakira

---

### Post by go_beep_yourself on 2008-11-11
The last problem is solved now after reinstalling the driver without the read-only support. I thought that was a feature I could enable/disable after I had the driver installed but wasn't. So I'm now copying over files to the new 1.5 tb drive and then I will install 64-bit Ubuntu in raid 0 and use the new drive for rsync backups.

---

### Post by go_beep_yourself on 2008-11-11
There is another ext3 driver that is supposed to work with the 256 inode size. I didn't like it as much, not so user friendly. Google it. The name is Ext2Fsd.

---

### Post by kabaiz on 2009-01-08
I've tested: Ext2Fsd doesn't work with it.

---

### Post by dakira on 2009-01-08
So the author replied to me. He said he's working to fix the problem but it will take some time.

---

### Post by go_beep_yourself on 2009-01-10
I've got two 320 gb sata2 segates running Ubuntu 64-bit in Raid 0. Since they are running in Raid 0, there's no way I could read them in Windows. I also have a 1.5 tb drive formatted with ext3 with 128 bit Inode size. I passed that as a parameter to mkfs.ext3, and I can read it from Windows using the IFS driver. Once in a while, I can't access it from Windows getting the message "would I like to format the drive" The solution is to reboot to Linux and let it to a filesystem check on the drive. Then I can use it from windows again. Everytime windows crashes, the partitions need a disk check.

---

### Post by dakira on 2009-01-11
It is usually a very bad idea to use these RAID modes that come with your motherboard. RAID 0 gives you nothing but a minor speed boost. But when your motherboard is broken you usually have no way to get back your data. These motherboard RAID modes are so peculiar that you need exactly the same motherboard to be able to read your data again.

And regarding Windows wanting to format your ext3 partition: Out of security reasons ifs-drives prohibits mounting an ext2/3-partition that has previously not been unmounted cleanly. That's why you have to reboot to Linux.

---

### Post by Mike090830 on 2009-08-30
> **sdowney717 said:**
> 
C:\scanmodem>mountdiag m:
The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not 
mount it because the file system has an inode size unequal to 128 bytes (inode
size: 256 bytes).
The only way to solve it is to back up the volume's files and format the file
system: give the mkfs.ext3 utility the -I 128 switch. Finally, restore all
backed-up files.
After that, the Ext2 IFS software should be able to access the volume.


I have tried that and it worked, see here: [http://ubuntuforums.org/showthread.php?p=7870122#post7870122](http://ubuntuforums.org/showthread.php?p=7870122#post7870122)

---

### Post by dakira on 2009-09-01
> **Mike090830 said:**
> I have tried that and it worked, see here: [http://ubuntuforums.org/showthread.php?p=7870122#post7870122](http://ubuntuforums.org/showthread.php?p=7870122#post7870122)

Yeah.. of course it works. But nobody wants a small inode size. And neither would I want to "reformat" my partitions.

Anyway. You can just use the program [ext2fsd]("http://www.ext2fsd.com/") which even supports ext4 and all inode sizes you can think of.

---

