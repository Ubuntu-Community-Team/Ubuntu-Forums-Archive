---
title: "Need Help Setting Up Partitions"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by jeremyj on 2009-01-27
Hey, all, I have some questions as to how to set up a partition specifically for Ubuntu with Vista pre-installed, as well as how to set up a shared partition so both Ubuntu and Vista can access the same documents?

For the record, I'd posted some general questions here:  [http://ubuntuforums.org/showthread.php?t=1050595]("http://ubuntuforums.org/showthread.php?t=1050595"), but I thought it might be more beneficial to future readers/forum searchers if my questions were in separate threads.  However, the above thread wasn't asking HOW to partition, just if there would be any problems between Vista and Ubuntu, as well as a couple odds and ends.

First, I'm concerned about creating a partition in either Vista, during the Ubuntu install, or using GParted (I assume it's on the 8.10 Live CD) from the Live CD.  Either way I have read, the only option is to install Ubuntu, then use my Vista Repair DVD to keep Vista operable.  So my first question is, would there be a SAFE way to install Ubuntu into a new partition WITHOUT having to repair Vista using its DVD?  My second question is, if I do wind up having to use the Repair DVD, will this erase my programs, documents, and media files, or just repair the OS WITHOUT touching my documents and programs?

Secondly, I would like to create a way to have my documents and media files on a separate partition so both Vista and Ubuntu can access them.  In the past, I experimented with Ubuntu on my old laptop, and it didn't have room on the HDD for my music on XP's partition AND Ubuntu's partition.  I wound up using Ubuntu solely on my laptop, and using my iPod to transfer my music from my desktop to my Ubuntu laptop.  So my question for this is, is there a way to create a partition (I believe the term is shared partition) solely for my documents so I can access them from either OS that I've booted into?

It's been a while since I've used Linux (I know, shame on me), so I've forgotten most of the terminology and command lines.  Just thought I'd throw that in there in case I wind up asking, "Huh?"  :)

I think that's all.  If I have any more questions, I'll be sure to ask.  Thanks for the help!

---

### Post by sumit.kalra999 on 2009-01-27
answer for first question:

Yes, there is way to safely install ubuntu without reparing your Vista/Xp
1. Install Windows first
2. Create non-windows partition using Disk Management
3. boot system to install ubuntu

---

### Post by sumit.kalra999 on 2009-01-27
answer of second question:

Repairing your OS will not harm to your data unless there is no critical situation

---

### Post by sumit.kalra999 on 2009-01-27
answer of third question:

To access whole disk with both Windows and Ubuntu, i suggest you to install Ubuntu inside windows

To install Ubuntu inside windows, perform the following steps:
1. Start your Windows
2. Insert bootable cd of Ubuntu while Windows is running
3. Start autorun.exe or play the cd
4. A choice will be prompted on screen providing option to install Ubuntu inside Windows
5. Its not necessary to install Ubuntu in your C:\ drive, you can use other partitions also to install Ubuntu
6. Follow the instruction during boot and reboot
7. By doing so, you will be able to access your whole hard disk from both of your OSs.

---

### Post by vanadium on 2009-01-27
I do not support the last suggestion. Installing Ubuntu within Windows is technically an inferior solution, which makes the system more vulnerable.

You'd better create about 10 Gb free space for installing Ubuntu. You need no more. Then, you have a robust Linux installation on its own partition and you can easily store, access and share your data on the Windows partition.

Depending on the size of your hard disk, I would not do the trouble of creating a separate partition for your data. Just store it on your Windows partition. You can easily and safely access it from within your Ubuntu home directory using links.

The easiest way is to reduce the size of the Windows partition to free some 10 GB of space on the drive. In the Ubuntu installer, you can then choose "Use largest free space" and the installer will automatically take care of partitioning the free space.

---

### Post by jeremyj on 2009-01-27
> **vanadium said:**
> 
You'd better create about 10 Gb free space for installing Ubuntu. You need no more. Then, you have a robust Linux installation on its own partition and you can easily store, access and share your data on the Windows partition.

Depending on the size of your hard disk, I would not do the trouble of creating a separate partition for your data. Just store it on your Windows partition. You can easily and safely access it from within your Ubuntu home directory using links.

Thanks, Vanadium.  I created a 12 Gb partition (12 just for some extra room as I have a 500 Gb HDD), and formatted it to NTFS using Vista's Disk Management.  However, once I booted the Live CD and got the Partitioner, it didn't detect my 12 Gb partition until I used the Manual setting.  I'm stuck there, because when I double-click that partition, I'm not sure what file system to use.  NTFS, FAT32, etc.?  Also, do I check the "Format" checkbox and/or worry about the dropdown menu (I forget now what it was titled) that gives me the choices "/dos" and "/windows?"  All 3 of the other partitions were automatically set to "Do Not Use Partition."  These would most likely be my Vista OS, my Backup partition, and whatever the 63 Mb EISA Configuration is.

Also, if I don't change any of the settings for the other partitions listed above, they won't be touched by Partitioner, correct?

How would I go about creating links to my files so I could access them from Ubuntu?


> **sumit.kalra999 said:**
> answer of second question:

Repairing your OS will not harm to your data unless there is no critical situation

Thanks for your clarification on that as well.  I was hoping this was the case!

---

### Post by jeremyj on 2009-01-27
Bump to first page.

---

### Post by mmitt on 2009-01-27
> **jeremyj said:**
> Bump to first page.
I have the same problem as you. Except i would make your partition 20GB for games and other stuff.

---

### Post by jeremyj on 2009-01-28
> **mmitt said:**
> I have the same problem as you. Except i would make your partition 20GB for games and other stuff.

I can always resize it later.  :)  I just need some advice on how to install Ubuntu into the partition I made.  ;)

---

### Post by ranch hand on 2009-01-28
Run your install disk and follow the directions.  When you get to the partioning part just piont at the partition you made and designate the mount piont as / and go on. That will put it all in that partition.

Heck, if I can do something like that you sure can.

---

### Post by Elfy on 2009-01-28
If you have made only one partition then you will be without swap - better to do as vandium suggests -

Before you start the install procedure go to Partition Editor in the System Admin menu and delete the partition you made in vista - so that it is empty space again.

Then follow vanadium's post to use the free space.

---

### Post by jeremyj on 2009-01-28
> **forestpixie said:**
> If you have made only one partition then you will be without swap - better to do as vandium suggests -

Before you start the install procedure go to Partition Editor in the System Admin menu and delete the partition you made in vista - so that it is empty space again.

Then follow vanadium's post to use the free space.

I've done as you suggested, and followed Valadium's post, however, the Installer is telling me to create a swap partition once I click Forward after selecting the unallocated space.

I'm extremely confused, so let me start over.  ](*,)

Assuming I can access my music, documents, and movies inside my Windows partition from Ubuntu, I would like to create a partition to boot into Ubuntu.

I've used Vista's Disk Management tool and created a 20 Gb unallocated space specifically for Ubuntu.  No file system is on this space.  I boot the Live CD of 8.10, get to the Partitioner, and every option on the first window shows Ubuntu will either be installed on the whole 500 Gb HHD, or it will take up the 60%+ empty space that Vista has yet to fill with my documents, music, and movies.

I select Manual.  I see my 3 partitions of my EISA Configuration (or whatever that is using 63 megabytes), my Vista OS, my 10 Gb backup partition, and, finally, my newly created 20 Gb unallocated free space.  I right click on the free space, select "create new partition," set the mount point to "/", select the Format option, select Ext3, leave the "Logical" and "Beginning" radio buttons alone, and double-check to make sure the other 3 partitions listed above are set to "Do not use partition" assuming this will keep Ubuntu from touching them during installation.

I click Forward, and a window pops up saying, "You have not selected any swap partitions for use as swap space...." and it goes on into further detail as to why I need a swap partition.  **I am not sure where to go from here, OR if the settings I've chosen for the unallocated space/new partition are correct/safe/optimal.  From this window, should I click "Go Back" or "Continue?"  If I select "Go Back," how do I set a swap partition?  If I select "Continue," will this slow down Ubuntu or mess with my other partitions in any way shape or form?**

Searching the forums, I found the Terminal code to print out my HDD info.  I used the Live CD to get to the Terminal to do this.  I've posted it below in case it's needed:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      128519       64228+  de  Dell Utility
/dev/sda2          129024    21100543    10485760    7  HPFS/NTFS
/dev/sda3   *    21100544   934828015   456863736    7  HPFS/NTFS
```

As you can see above, the sad1 63 Mb is part of my Dell.  The sda2 10Gb is my backup partition.  And the sda3 boot partition is my Vista installation.  I assume the 20 Gb unallocated free space won't show up in fdisk when it's not associated with any file system.  Correct me if I'm wrong.  I hope the above info clarifies my questions.

---

### Post by Elfy on 2009-01-28
> In the Ubuntu installer, you can then choose "Use largest free space" and the installer will automatically take care of partitioning the free space.

If you want to use manual - then you need to have 2 partitions as you have discovered, one / and one swap.

Using the largest free space the installer will use the empty 20Gb and make what's needed.
> 
Correct me if I'm wrong. I hope the above info clarifies my questions.You are correct - there is no partition yet.


If you want to use manual and need a hand then post back.

---

### Post by jeremyj on 2009-01-29
> In the Ubuntu installer, you can then choose "Use largest free space" and the installer will automatically take care of partitioning the free space.

This is the part that I'm stuck on.  I apologize if I seem like I'm being difficult, but the Ubuntu installer seems to be showing me something completely different than the steps I've been given.  The partitioner is telling me that Ubuntu will either use 63% of the HDD, or it will use 100%.

I took a screenshot of the installation process, and put it on my flash drive to post here.  Maybe this will clear things up?

As you can see from the screenshot, the partitioner is showing that Ubuntu will be installed on the entire hard drive, and NOT in a partition by itself.  I'm about at that point where I give up and forget Ubuntu altogether, but I'd like to give this one last try.

---

### Post by Elfy on 2009-01-29
mmm - looks odd - but then I rarely use the guided options. If you want to be sure of what is going to happen then make the partitions.

Open the partition editor from the sys admin menu of the livecd.

Select the empy space and create an extended partition.

Decide how big to make your swap partition - below 1Gb I would do 2XRAM - above I would do 512MB - UNLESS you want to hibernate in which case then swap should be a bit more than RAM.

Make a swap partition inside the extended partition
Make a patrition in the remaining space - ext3 is default

Start the install when you reach the partition part - choose manual

Select the ext3 partition you just created - Edit partition - from the Use As dropdown pick - ext3, from the Mountpoint dropdown - pick /

Close that and you are back where you started - pick the ext3 partition again and make sure there is a tick in the format - now carry on with the install

---

### Post by jeremyj on 2009-01-29
> **forestpixie said:**
> Decide how big to make your swap partition - below 1Gb I would do 2XRAM - above I would do 512MB

By this, if I have 3 Gb of RAM, then a 512 Mb swap partition is ok?

---

### Post by Elfy on 2009-01-29
if you don't want hibernate or suspend then yes - I have 1.3Gb Ram and 512Mb swap

---

### Post by vanadium on 2009-01-29
The screenshot you show is confusing indeed. The choice you indicated would normally imply that the gray free space at the end would be used. The automated installer might not be able to handle your specific situation, though. Indeed, it is not possible to create an additional primary partition *and* a swap. In your case, both / and swap must be created in an extended partition (this is not a problem for linux, it is only a problem of the Ubuntu installer).

I therefore support the suggestion of forestpixie, to go for manual partitioning instead.

---

### Post by jeremyj on 2009-01-29
> **vanadium said:**
> The screenshot you show is confusing indeed. The choice you indicated would normally imply that the gray free space at the end would be used. The automated installer might not be able to handle your specific situation, though.

FHEW!  For a while there I thought I was going insane choosing between forum advice and what the installer was telling me!  ;)

A BIG thank you to both Vanadium and ForestPixie for their advice.  =D>  I am now posting from within Ubuntu.  Installation complete!  I used GParted from the Live CD to create a 512 Mb swap partition (didn't worry about having to use a different size for hibernating since my computer is only on while in use), then created an ext3 partition for Ubuntu in the rest of the space.  Thanks, guys!

---

### Post by vanadium on 2009-01-29
Congratulations! The approach was slightly more difficult, but from your reactions and what you already realized, I knew you were up to the task.

---

### Post by jeremyj on 2009-01-29
> **vanadium said:**
> Congratulations! The approach was slightly more difficult, but from your reactions and what you already realized, I knew you were up to the task.

Thanks.  :)  Now if I can only figure out how to access my files from Ubuntu that are in Vista...  I'm still doing research on that.  I may wind up shrinking the Vista partition again, and copying my music, movies, and documents to a FAT32 partition or NTFS partition to access from both OS's.

I found this thread:  [http://ubuntuforums.org/showthread.php?t=1053545&highlight=sharing+files+windows]("http://ubuntuforums.org/showthread.php?t=1053545&highlight=sharing+files+windows") and I like mb_webguy's setup.

> Most people who dual-boot keep their data on a separate partition that is accessible by both operating systems.  For example, I'm dual-booting Vista and Ubuntu.  I have Vista on a 25GB partition that just contains Vista and its applications.  I have Ubuntu on a 12GB partition that just contains Ubuntu and its applications.  I have a separate 2GB /home partition to keep my user settings separate from Ubuntu in case I want to reinstall, but to also hide them from Vista so I don't accidentally break something in Ubuntu while using Vista.  I have a 2GB swap partition for Ubuntu.  And then the rest of the drive is used for my files, and is mounted in both Vista and Ubuntu.

My Documents, Pictures, Video, and other data folders are located on this partition.  In Vista, I went to the Properties dialog to change the location of each of these folders to the corresponding folder on the shared partition.  In Ubuntu, I'm using soft links to point to the same folder.  That way, if I put a photo in my Pictures folder in Vista, it's also there when I boot into Ubuntu.

If it's not too much trouble to ask, maybe I could go one step further and ask for advice on how to accomplish this?

---

### Post by Elfy on 2009-01-29
The really simple way is to install ntfs-config

From a terminal ```
sudo apt-get install ntfs-config
```

Once it has installed it will be in system tools - open it and you will see your ntfs drives - give it a name and apply - on reboot the drive will be available

Or you need to make it available yourself in fstab - generally like this

make a folder
mount the drive to the folder

Quite happy to help if you want - give us

```
sudo fdisk -l
```

You might be interested in this [https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Education/Events](https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Education/Events)

Keep an eye on it, different ones are planned - the last on that page will deal with exactly what you need - but obviously you'll have done this by then ...

---

### Post by jeremyj on 2009-01-29
> **forestpixie said:**
> Quite happy to help if you want - give us

```
sudo fdisk -l
```

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1314       58126   456339444    7  HPFS/NTFS
/dev/sda4           58127       60801    21486937+   5  Extended
/dev/sda5           58127       58191      522081   82  Linux swap / Solaris
/dev/sda6           58192       60801    20964793+  83  Linux
```


Hope this helps.  Although, I thought it was kind of odd that I now have ```
/dev/sda4           58127       60801    21486937+   5  Extended
/dev/sda5           58127       58191      522081   82  Linux swap / Solaris
/dev/sda6           58192       60801    20964793+  83  Linux
```

instead of just the swap and extended partition.  I haven't created any more since the install today.  Did I create another by accident?

I've got the Wiki bookmarked as well.  I'll definitely keep an eye on it for more tutorials and help.  It's been a while since I've used Linux, and even then I barely got used to it before my laptop died, and I had to stick with XP on my old desktop.  But I'm starting to get the hang of what I once knew.  :D

---

### Post by Elfy on 2009-01-29
The extended - has both the swap and your install in it - check the start and ends for them

Anyway - you can do this with the /dev/ information or with UUIDs - which you can get with the blkid command

So for each partition that you wish to mount - I will assume that sda3 is your win install as it has boot flag and sda2 a seperate ntfs partition - I will work through for sda3 - change it to suit you, same goes for the mkdir command - change the name to suit

Also - if you want the partition to show on the desktop - change /mnt/ to /media/

Backup and open fstab to edit

```
sudo cp /etc/fstab /etc/fstab.2901
gksu gedit /etc/fstab
```

Add this line

```
/dev/sda3 /mnt/vista ntfs-3g auto,users,uid=&#8236;1000,gid=&#8236;100,utf8,dmask=&#8236;027,fmask=&#8236;1 &#8236;37 &#8236;0 &#8236;0
```

Close the file, then 
```
sudo mkdir /mnt/vista
sudo mount -a
```

Folder should now be accessible in the /mnt/vista - get at it through file system in nautilus, you can drag a shortcut to the left pane as a bookmark.

If you get an error with the mount command along the lines of /dev/sda3 already mounted - it should be ok on reboot.

---

### Post by jeremyj on 2009-01-29
> **forestpixie said:**
> Once it has installed it will be in system tools - open it and you will see your ntfs drives - give it a name and apply - on reboot the drive will be available

```
Mounting /media/Vista failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda3': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda3 /media/Vista -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda3 /media/Vista ntfs-3g force 0 0
```

This is the error message I was given when trying to mount my Vista partition.  ("Vista" is the name I gave it in ntfs-config since the default was just "OS.")  

Someone in the thread I linked about accessing documents from the Vista partition said forcing Windows to shut down with that command line above can be dangerous.  I'd rather not risk anything with my installation, because, as everyone knows, Windows is always a **_PAIN_** to re-install...

I'm not sure why it gave me this error, because before I booted into Ubuntu again (hopped onto Vista to read the Disk Manager), I selected Restart in Vista, then it booted my computer, and brought me to the boot menu.  I would think that was a clean shutdown.

---

### Post by Elfy on 2009-01-29
Sometimes you need to boot into it a couple of times I think, sure I seen similar - don't force it at the moment.

It has to, I believe fix it's thing and be booted again, but I'm probably wrong - long time ago now and never Vista ;)


Edit - you do know you don't have to use ntfs-config and do post #24 - one or the other only.

---

### Post by jeremyj on 2009-01-29
Whoops.  You beat me to the punch on your last reply.  Here's where I am so far, but it doesn't look like ntfs-config is seeing my Vista partition anymore when I open it.

> **forestpixie said:**
> Add this line

```
/dev/sda3 /mnt/vista ntfs-3g auto,users,uid=&#8236;1000,gid=&#8236;100,utf8,dmask=&#8236;027,fmask=&#8236;1 &#8236;37 &#8236;0 &#8236;0
```

Close the file, then 
```
sudo mkdir /mnt/vista
sudo mount -a
```

fstab reads:```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=57850ed1-adab-456f-b932-f72157c01a5c / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=c2b69025-ed47-4420-8220-51e029a56fb9 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda3 /media/Vista ntfs umask=222,utf8 0 0
```

Do I delete that last line and enter the line you gave?

```
/dev/sda3 /mnt/vista ntfs-3g auto,users,uid=&#8236;1000,gid=&#8236;100,utf8,dmask=&#8236;027,fmask=&#8236;1 &#8236;37 &#8236;0 &#8236;0
```

Also, I'm not sure what the mkdir command is.  I don't believe I've seen that before.  How do I know what to change it to?

---

### Post by Elfy on 2009-01-29
ok the mkdir command makes a directory/folder - you can leave it as vista if you want - _just has to match _

/dev/sda3 [COLOR="Red"]/mnt/vista[/COLOR] ntfs-3g auto,users,uid=&#8236;1000,gid=&#8236;100,utf8,dmask=&#8236;027,fmask=&#8236;1 &#8236;37 &#8236;0 &#8236;0

sudo mkdir [COLOR="Red"]/mnt/vista[/COLOR]

Yes you can delete the line that ntfs-config added and replace it with the other one if you want.

---

### Post by jeremyj on 2009-01-29
> **forestpixie said:**
> ok the mkdir command makes a directory/folder - you can leave it as vista if you want - _just has to match _

/dev/sda3 [COLOR="Red"]/mnt/vista[/COLOR] ntfs-3g auto,users,uid=&#8236;1000,gid=&#8236;100,utf8,dmask=&#8236;027,fmask=&#8236;1 &#8236;37 &#8236;0 &#8236;0

sudo mkdir [COLOR="Red"]/mnt/vista[/COLOR]

Yes you can delete the line that ntfs-config added and replace it with the other one if you want.

Not sure if I screwed something up, but when I was copying and pasting, I expected to have the ability to hit "Enter" in the Terminal after pasting the line into fstab and saving, but I made the directory "Vista" instead of "OS" by accident...  I then typed it in by hand and changed "Vista" to "OS," and when I typed "sudo mount -a" I got an error saying it was an invalid command.  Did I mess this whole thing up?

***EDIT:  I can't find my Vista partition in the Computer folder either.***

---

### Post by Elfy on 2009-01-29
run these - copy and paste them to make sure

```
sudo mount -a
df -h
```

Then paste the whole lot from the first pasted command here please

---

### Post by jeremyj on 2009-01-29
> **forestpixie said:**
> run these - copy and paste them to make sure

```
sudo mount -a
df -h
```

Then paste the whole lot from the first pasted command here please


```
[mntent]: line 13 in /etc/fstab is bad

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              20G  3.1G   16G  17% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  208K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.9M  1.5G   1% /dev
tmpfs                 1.5G  104K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-11-generic/volatile

```

---

### Post by Elfy on 2009-01-29
Ok - something wrong with fstab 

```
cat /etc/fstab
``` and paste it please :)

---

### Post by jeremyj on 2009-01-29
> **forestpixie said:**
> Ok - something wrong with fstab 

```
cat /etc/fstab
``` and paste it please :)

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=57850ed1-adab-456f-b932-f72157c01a5c / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=c2b69025-ed47-4420-8220-51e029a56fb9 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda3 /mnt/OS ntfs umask=222,utf8 0 0
```

---

### Post by Elfy on 2009-01-29
right that is the line that ntfs-config added causing the problem - I thought you were deleting it and adding my one?

Open the file again ```
gksudo gedit /etc/fstab
```

Delete the last line and add

```
/dev/sda3 /mnt/OS ntfs-3g auto,users,uid=&#8236;1000,gid=&#8236;100,utf8,dmask=&#8236;027,fmask=&#8236;1 &#8236;37 &#8236;0 &#8236;0
``` enter once it's pasted to get new line and save.

Then try sudo mount -a again - this assumes that you have also at some point made the folder with sudo mkdir /mnt/OS

---

### Post by jeremyj on 2009-01-29
> **forestpixie said:**
> right that is the line that ntfs-config added causing the problem - I thought you were deleting it and adding my one?

Open the file again ```
gksudo gedit /etc/fstab
```

Delete the last line and add

```
/dev/sda3 /mnt/OS ntfs-3g auto,users,uid=&#8236;1000,gid=&#8236;100,utf8,dmask=&#8236;027,fmask=&#8236;1 &#8236;37 &#8236;0 &#8236;0
``` enter once it's pasted to get new line and save.

Then try sudo mount -a again - this assumes that you have also at some point made the folder with sudo mkdir /mnt/OS

Terminal is still saying [mntent]: line 13 in /etc/fstab is bad

:(

---

### Post by Elfy on 2009-01-29
assuming that you have made the /mnt/OS folder then I Can't think of anything other than it needing an end of line - ie when the file is open for editing the cursor stats a new line below the /dev/sda3 line

---

### Post by vanadium on 2009-01-29
I should remark that your new line contains an error: in "fmask=&#8236;1 &#8236;37", you should remove the space. Even then, I wonder why the error was there also with the previous line, the one inserted by ntfsconfig. It looks correct to me.

---

### Post by Elfy on 2009-01-29
mm - I've used exactly the same line befgore - just lifted from bodhi's how to fstab - I've also used the same line myself without issue - seems odd that it causes an issue here

It's certainly a lot of posts for what should be a quick job :(

As you the original line written by ntfs-config looks ok to me too ...

---

### Post by jeremyj on 2009-01-29
> **vanadium said:**
> I should remark that your new line contains an error: in "fmask=&#8236;1 &#8236;37", you should remove the space. Even then, I wonder why the error was there also with the previous line, the one inserted by ntfsconfig. It looks correct to me.

I removed the space, saved, then used sudo mount -a in the Terminal, but it gave me same error that line 13 was bad.

I've rebooted once since adding the line in gedit, but should I try rebooting a couple times?  I guess it wouldn't hurt.


**EDIT:  Also, in the Nautilus file browser, am I going to the right place to look for it?  Places > Computer > Filesystem > mnt > OS ??  I also checked the media folder here as well.  But they're both empty along with the Vista folder I created by accident in mnt.  I hope I'm looking in the right place, or I'm going to feel pretty dumb....  The Vista partition is also no longer in the computer:/// directory either.**

---

### Post by jeremyj on 2009-01-29
> **jeremyj said:**
> I removed the space, saved, then used sudo mount -a in the Terminal, but it gave me same error that line 13 was bad.

I've rebooted once since adding the line in gedit, but should I try rebooting a couple times?  I guess it wouldn't hurt.


**EDIT:  Also, in the Nautilus file browser, am I going to the right place to look for it?  Places > Computer > Filesystem > mnt > OS ??  I also checked the media folder here as well.  But they're both empty along with the Vista folder I created by accident in mnt.  I hope I'm looking in the right place, or I'm going to feel pretty dumb....  The Vista partition is also no longer in the computer:/// directory either.**

Well, I went back in to fstab, deleted line 13, restarted, tried ntfs-config again, and my Vista partition is now on my desktop.  So that's solved.  The only problem I've run into so far is Amarok not keeping a Collection.  I right-clicked my iTunes folder, opened with Amarok, and it created a playlist of my billion songs.  :)  If I select a folder to create a Collection, I assume it will copy every song file to my Ubuntu partition, which doesn't have room for it all.

On the bright side, however, I've found that Amarok is now playing my DRM files (files downloaded through iTunes including podcast videos' audio).  That's definitely a plus.  :D  I remember it not being able to do that a couple years ago.

I'll worry about situating Amarok and my music and movie collection in the meantime.  Thanks a ton, guys!

---

### Post by Elfy on 2009-01-30
Open amarok - settings - configure amarok - collection and add the folder and it will have it as the library

That though is as far as I could go with itunes - never used it ;)

---

### Post by jeremyj on 2009-01-30
> **forestpixie said:**
> Open amarok - settings - configure amarok - collection and add the folder and it will have it as the library

That though is as far as I could go with itunes - never used it ;)

I had tried that yesterday, but couldn't find my Vista partition for some reason.  I think my eyes were probably too tired from all the installing/partitioning, so I gave up on it for a while.  I found it this morning though.  :)  Thanks!

---

