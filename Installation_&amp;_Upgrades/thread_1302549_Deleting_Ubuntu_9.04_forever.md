---
title: "Deleting Ubuntu 9.04 forever"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by irohaphoto on 2009-10-27
I am trying to delete Ubuntu 9.04 but having no luck in the 9.10 upgrade. too complex for a beginner
Please let me know how to delete 9.04 forever. thanks

---

### Post by jheaton5 on 2009-10-27
Did you upgrade 9.04 to 9.10 or did you do a fresh install of 9.10 in a separate partition from 9.04?

---

### Post by fancypiper on 2009-10-27
Are you wishing to return to Windows?

[How to Remove Linux and Install Windows on Your Computer]("http://support.microsoft.com/kb/247804")

---

### Post by irohaphoto on 2009-10-27
> **fancypiper said:**
> Are you wishing to return to Windows?



no I don't want to return to windows I just want to get 9.04 off forever so I can start again with 9.10

---

### Post by ShapeShiftme on 2009-10-27
When installing and you get to partitioning you will see options somewhere. (Cant remeber out of my head) so set the partition 

You must select e entire hard disk Then select /dev/sda

That is of course if your 9.04 was on dev/sda.

if somone knowes the exact place to do that perhaps they can post aswell.. but that is roughly what you are looking for

---

### Post by irohaphoto on 2009-10-27
> **jheaton5 said:**
> Did you upgrade 9.04 to 9.10 or did you do a fresh install of 9.10 in a separate partition from 9.04?

If I put the 9.10 disk in and install it will install 9.40 and 9.10 side by side and give it a ext4 partition which I do not want I want to leave it as is in the ext3

to make things easy I just want to delete 9.04, why does this seem to be difficult?

---

### Post by jheaton5 on 2009-10-27
> **ShapeShiftme said:**
> When installing and you get to partitioning you will see options somewhere. (Cant remeber out of my head) so set the partition 

You must select e entire hard disk Then select /dev/sda

That is of course if your 9.04 was on dev/sda.

if somone knowes the exact place to do that perhaps they can post aswell.. but that is roughly what you are looking for

This is the correct procedure.  The installer gives you the option to install sise by side or use the entire drive.

---

### Post by fancypiper on 2009-10-27
Only if you choose the automatic wizard.  Try this:

Boot with your install disk and when the partitioner starts, choose the manual partitioning.

Delete your existing partitions and create 3 partitions. I suggest:

/ - from 5 to 20 GB depending on amount of software you want to install, choose ext3 for your filesystem
swap - 2 X memory or 2 GB whichever is less
/home - the rest of the disk. Again, choose ext3 for your filesystem
If you have any other drives, choose to mount them in something like /pub or /storage or some such.

Proceed with the rest of the install.

---

### Post by jimbo99 on 2009-10-27
In my experience, even someone that's been using Linux for a long time and has 25 years in the industry, I don't advise giving new users advice on creating partitions as the above post states.  What you should do is just use the partition manager to delete your current partitions, then reboot again with the live CD and run a normal install.  This takes out of it any hint of confusion about which partitions of which size and what file system to put on them.

Before you do this, you should consider that you might loose your personal data and should consider backing it up first.

---

### Post by fancypiper on 2009-10-27
jimbo99, Linux isn't 25 years old, is it? I seem to remember 1991 as it's start.

The OP wanted ext3, will the "normal install" do that for him?

---

### Post by irohaphoto on 2009-10-28
> **fancypiper said:**
> Are you wishing to return to Windows?

[How to Remove Linux and Install Windows on Your Computer]("http://support.microsoft.com/kb/247804")


I don't think this is a very good reply to the question. whether someone wants to return to windows or whatever OS it is up to them and definitely none of anyones business.

not really a solved thread but temporarily solved as I have 9.10 but still 9.04 exists on another partition

---

### Post by dvlchd3 on 2009-10-28
Hi irohaphoto,

It really seems no one wanted to answer your question, they probably just opened this thread because they didn't want you to go back to Windows. (Hey, its why I read it...)

Anyway, to sum everything up, you have both Ubuntu 9.04 and 9.10 installed on your system.  You want to remove 9.04 so you can use only 9.10, if that is correct, proceed:

While in 9.10, click, install the package 'gparted' by your favorite method.  I.E. - 

```

sudo apt-get -y install gparted

```

After it is done installing, click System -> Administration -> Partition Editor.

You should now see all the partitions on your system.  Since 9.04 is partitioned with ext3, and 9.10 with ext4, find the EXT3 partition.  Select it, and then click "Delete" at the top, then click "Apply".  This will delete 9.04 from your system.

If you would like to resize the partition so your new 9.10 can make use of this space, you will have to use a live CD.  Once you boot up in the live CD, you will have to make sure you have Internet connectivity and install gparted.

Now you can "resize" the ext4 partition to take up the space from your old 9.04 install.  To do this, simply select the ext4 partition, and click "Resize/Move" at the top.  This will bring up a dialog box with all the options for moving and resizing the partition.  You can simply drag the arrow at the top so it takes up the entire box.  Then click "Resize/Move" at the bottom of the dialog box.

After all this is done, click "Apply".  This will apply all your changes.

Since all this does not change the bootloader, you will have to modify the grub menu.lst file so 9.04 will no longer show up when you start the computer.

```

gksu gedit /boot/grub/menu.lst

```

Scroll down to the bottom, you will see a line that looks something like this:

```

## ## End Default Options ##

```

After this line are all of the entries for GRUB.  Simply add a '#' infront of the blocks that include 9.04.  I.E. -

```

#title		Ubuntu 9.04, kernel 2.6.28-16-generic
#uuid		e68322b4-2d37-46a5-8c64-4d5c1038d678
#kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=e68322b4-2d37-46a5-8c64-4d5c1038d678 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-16-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
#uuid		e68322b4-2d37-46a5-8c64-4d5c1038d678
#kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=e68322b4-2d37-46a5-8c64-4d5c1038d678 ro  single
#initrd		/boot/initrd.img-2.6.28-16-generic

#title		Ubuntu 9.04, memtest86+
#uuid		e68322b4-2d37-46a5-8c64-4d5c1038d678
#kernel		/boot/memtest86+.bin
#quiet

```

Hope this helps.  Be aware, playing with partitions is EXTREMELY dangerous.  It could break your system.  If you accidentally delete the wrong partition, you will not be able to get it back easily (sometimes never)...you have been warned!

---

### Post by Dougie187 on 2009-10-28
> **irohaphoto said:**
> I don't think this is a very good reply to the question. whether someone wants to return to windows or whatever OS it is up to them and definitely none of anyones business.

not really a solved thread but temporarily solved as I have 9.10 but still 9.04 exists on another partition

I don't agree with this post. I think fist off, it is a fair assumption based on your thread title that you had wished to return to windows. Granted, in your OP it says that you are looking to remove 9.04 and return to 9.10 but there are quite a few threads on here that have people wanting to return to windows.

If you want to keep your OS use to yourself, I would recommend not asking for help on a forum dedicated to helping with OSes, as your original intent and question might not come across to everyone the same. He was simply giving you the information he thought you were asking for and nothing else, I wouldn't read into it too much.

Either way, other people in this thread have previously stated how to fix your issue. When you go to do a clean installation of ubuntu 9.10, you can simply tell the installer to use the entire disk. This will wipe all of your disk before partitioning and installing a new version.

Also, if you don't find the answer to your question in this thread, you might try asking it again in the karmic testing forum, as they have a lot more experience installing karmic than other people do and the options between version may have changed names or something.

Also, there are instructions in here for wiping one of the two partitions to keep only the 9.10 one, but it seemed from your previous posts that you were looking to have 9.10 with an ext3 filesystem, which I believe can be done through the installer, but I am unsure as I haven't toyed with it enough to fully answer that question.

---

### Post by jmore9 on 2009-10-28
When i updated from 9.04 to 9.10 all i did was the following :

ALT + F2

then enter in the command box

update-manager -d

It should be straight forward from there

9.04 was gone and 9.10 took its place

---

### Post by leandromartinez98 on 2009-10-28
You can do a new install of 9.10 on the partition that had 9.04 before (of course, backup all you personal data before!).

To do that, during 9.10 install, select "manual partition". You then delete the partition marked as ext3 and create a new one, in what follows, and mount it as "/". By default it will be "ext4". 

The list of partitions will be exactly identical to what was listed before (suggestion: annotate it in a paper, to be sure), and the only difference will be that the "ext3" will be changed to "ext4".

This will erase the 9.04 installation and the 9.10 installation will take its place. Check twice if the "ntfs" partitions are still there and identical than before before applying the changes, these are the ones with, I suppose, your Windows (if you have one).

By the way, this must be done only if you have a dual boot with some other OS (Windows, for instance). If you have only Ubuntu, just backup your personal data and choose "use the entire hard drive".

---

