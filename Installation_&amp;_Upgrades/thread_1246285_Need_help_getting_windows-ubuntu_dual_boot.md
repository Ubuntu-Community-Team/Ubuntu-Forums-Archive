---
title: "Need help getting windows-ubuntu dual boot"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by adam93 on 2009-08-21
So, I read somewhere that you should install ubuntu first because it will be quicker if it's on the outside of the hard drive, and then to install windows after. So, apparently it's hard/impossible to create a windows partition from ubuntu (???) without deleting stuff. So what I would like to do is back up ALL of my ubuntu partition so I can install windows, then ubuntu but still have ubuntu just how I left it. I would like to back it up to my 8gb usb flash drive, can anyone help???
I've only used 3gb of memory (I just installed ubuntu a couple of weeks ago), so there is no memory space issue here. 
Or, what would be even better is if someone could tell me how to create a windows partition from my installed ubuntu OS without damaging anything. That would be much more preferred than backing up then restoring.
If you haven't guessed, I'm new to ubuntu.

I know this is a mouthful, but could someone help please? It would be greatly appreciated, I hate windows. I will need it on occasion unfortunately though =[

---

### Post by waltmanno on 2009-08-21
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

This should help you out.  Let me know if this works.

---

### Post by Herman on 2009-08-21
> So, I read somewhere that you should install ubuntu first because it will be quicker if it's on the outside of the hard drive, and then to install windows after.  Yes, I have read that too, there might be some truth in it, but it's not probably a big enough difference for most people to notice unless we take measurements by timing the transfer rates of large files. For small files it probably doesn't matter because most hard disks have a small 'cache' memory. The cache memory is a space where incoming data can wait (like a waiting room for data) until the hard disks's read/write heads catch up. So most of the time you won't notice much difference. 
However, that's not to say it isn't still a good idea. If you ever want to resize your partitions, it will be a lot easier with Ubuntu at the start of your disk so you won't need to move the start of the Ubuntu file system. The end of the Ubuntu partition is easy to resize, (shrink or extend) with a partition editor like GParted. Windows is also easy to move. The start point of your Ubuntu partition doesn't like to be moved, so by having that at the beginning of your disk, you'll end up with a more flexible setup.
> So, apparently it's hard/impossible to create a windows partition from ubuntu (???) without deleting stuff. So what I would like to do is back up ALL of my ubuntu partition so I can install windows, then ubuntu but still have ubuntu just how I left it. I would like to back it up to my 8gb usb flash drive, can anyone help???
Well it's always a good idea to make a regular backup of all of your files and a backup of at least your important files before any partitioning operations. In practice you'll probably never need it but it's still important to make the backup anyway. 
I don't believe it's hard to resize the Ubuntu partition, but if it's absolutely full of files you'll need to make some room first of course. If it's nearly empty then you'll have no problem, just boot your Ubuntu live cd open GParted and resize your partition.
> I've only used 3gb of memory (I just installed ubuntu a couple of weeks ago), so there is no memory space issue here. Okay, I'm guessing by 'memory' you mean hard disk space, Yup, that should easily fit in your 8 GB flash memory stick.
> Or, what would be even better is if someone could tell me how to create a windows partition from my installed ubuntu OS without damaging anything. That would be much more preferred than backing up then restoring.Okay, tell you what, we'll start by making you a backup and then resize your Ubuntu and create an empty partition step by step with your Ubuntu Live CD.
 1. Boot your computer with your Ubuntu 'Desktop' Live/Install CD.
 2. Click 'Places'-->'Removable Media'-->' (and click the icon for your Ubuntu partition) '
 3. A new icon should appear in your Ubuntu CD desktop for your hard disk installed Ubuntu file system. 
 4. A folder should open, (we call it a 'directory' in Linux). This directory will show you the 'root' (top layer) of your Ubuntu file system on your hard disk.
 5. Click on your 'home' folder to open it.
 6. You'll see another directory (folder) inside it with your name on it. That's your /home/username directory that contains all your personal files and settings. If you share your computer with other people, there could be a /home/username folder for every person who has an account in this computer. Probably though, you only have your own to make a backup of.
 7. Right-click on your /home/username folder and click 'properties'
Read the 'basic' tab in the properties window to see how many GB of files this folder contains.
8. Insert your 8 GB USB flash memory stick
9. An icon should appear for it and another window will open on your desktop showing you the contents of your flash drive.
10. Right-click on your flash drive icon and click 'Properties.
You should see a pie graph showing you if you have enough room in your flash drive to fit all your files from your /home directory in or not. Hopefully you do.
11. Close the two 'properites' windows.
12. Create a new folder in your flash memory drive and name it something like '09.10.22_ubuntubackup'. (The numbers are the date backwards, beginning with the year, followed by the month and then the day last, that way if you end up with a lot of backups they'll appear in chronological order all the time naturally, so it'll be easier to look things up some day if you ever need to).
13. Open your new '09.10.22_ubuntubackup' folder, (empty).

-- Now there are two ways you can do this ---

14. Just drag 'n drop your old /home/username folder into your empty backup folder.
Just click 'Skip all' if you see an error message about some file(s) that you don't have permission for and proceed with the copying anyway, at this stage those won't matter.
or, 
open your terminal and use a linux command, (probably a little advanced for you at this stage),
 ```
sudo cp -Rav /media/JAUNTY/home/herman /media/disk/09.10.22_ubuntubackup/
``` If you're copying to a disk that's formatted with the FAT32 file system, which is most common, you may see a message complaining that it can't 'preserve the ownership', of your files. That's okay for now, just make your backup regardless. It's better to use disk that's formatted with a Linux file system when you get more advanced, but the main thing for now is to get your important files copied.

15. Take a look and check to be sure your most important files are there in your backup, and don't forget to click 'View',-->'Show Hidden Files', there should be some files there with a dot in front of their file names, those are invisible files and they contain your user settings. You may be interested in those at a later date or maybe they won't matter but at least if you have a copy of them you can decide later.
16. That's it for the backup, now right-click on those two icons and click 'unmount volume' for both of them and they should disappear.
17. Open 'System'-->'Administration'-->'Partition Editor'.
18. Right-click on your Ubuntu partition and click 'Resize/move'.
19. Grab the right-hand edge of the partition with your mouse and drag it to the left and adjust it to the size you want.
20. Click 'Resize/Move.
21. Click 'Apply', (on the toobar).
22. Click 'Apply' (in the confirmation window that will pop up)
23. Wait until the operations are completed before closing that 'pending operations' window.
24. Right-click on the area of unallocted space you just made and select 'New'
25. Create a new primary partition for Windows and have it formatted with the NTFS file system, you can type a label for it in the 'label' field if you like, like 'WINDOWS' for example. Click 'Add', and 'apply, apply', (again).
26. Reboot and spit out your Ubuntu CD, replace it with your Windows CD and Install Windows.
> If you haven't guessed, I'm new to ubuntu.That's okay, stick around kid, there's lots to learn, and the more you learn the more you'll realize you have left to learn, but it's interesting and fun.

---

### Post by adam93 on 2009-08-21
Wow, thank you so much!
I'm gonna try to do it tomorrow, I'm a little busy tonight.
You are by far the most helpful person I have ever ran into on these forums.
But yeah, I'm somewhat familiar with the terminal, I would just never be able to do something like shell scripting. I basically need commands spoon fed lol.
But I just have one question, because this almost sounds too easy. (spent hours on google trying to find the answer), 
So this will leave my settings exactly as I left them? (things like compiz settings, firefox bookmarks, avant, etc..)

---

### Post by Herman on 2009-08-21
Yes, if you just resize (shrink) your Ubuntu partition and install Windows after it you'll still be able to reboot -

Oops, I forogt one thing, Windows will probably overwrite GRUB in your MBR, so you'll need to restore GRUB to your MBR, or rather, some code in your MBR which points to GRUB in your Ubuntu partition. There are lots of ways to do that. Here's the most popular link,  [**How to restore Grub from a live Ubuntu cd**]("http://ubuntuforums.org/showthread.php?t=224351")  - Ubuntu Web Forums - catlett.

 - (continued), you'll still be able to reboot Ubuntu and all of your files and settings will still be the same. Resizing your partition won't have any effect on the performance of your operating system or cause any problems with any of your files.

As long as you don't do anything drastic like delete your partition or something like that, (obviously), everything should be fine. 
Just make sure you never work on a file system while it's still mounted, that's why it's best to use your Ubuntu Live CD and not your hard disk installed Ubuntu for partitioning work. Your hard disk installed Ubuntu can't work on itself. If it could it'd be working on itself working on itself working ... something like holding two mirrors together and trying to look into them.

If you make a backup of your home folder the way I said, you'd probably be able to restore it pretty near exactly as it was (including your settings)  if you made a Linux file system in your flash memory stick first so the file permissions can be retained. The way I explained is an easy way. There are other good commands and programs for making backups in Ubuntu, sbackup and srestore are good, other people use partimage, which in turn uses tar and dd commands. Or there's rsync, aysiu has the best web pages about those [Backing up Ubuntu]("http://www.psychocats.net/ubuntu/backup"). and [Using Partimage in Ubuntu]("http://www.psychocats.net/ubuntu/partimage").
My own web page about backing up and restoring is here, [Back Up and Restore]("http://members.iinet.net.au/%7Eherman546/p13.html").
As long as you make a backup somehow you'll be giving yourself some protection in case a disaster happens, but probably you won't need to use it. I'm sure your Ubuntu files and setting will be perfectly preserved during your partition resize.

---

