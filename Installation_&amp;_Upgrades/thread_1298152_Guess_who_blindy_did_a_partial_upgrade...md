---
title: "Guess who blindy did a partial upgrade.."
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by iamjfarrell on 2009-10-22
ME! I was wondering what the best way to fix this is? I did the partial assuming it would be ok. Guess what. It wasn't. Basically I get the same 31f video mode undefined error as before but the computer just freezes there and won't go any farther. Could I just run a Live CD and reinstall ubuntu? would I lose all my files? Like pictures and such? Thanks for the help.

---

### Post by earthpigg on 2009-10-22
yes you can run a livecd and reinstall.

first, use the live cd to grab all your important documents and data and back it up to a DVD or USB external hard drive or something.

if you back up the entire /home/yourusername/, that should grab everything -- including application settings.

then, once the reinstall is done, move your backed up /home/yourusername/ over the /home/yourusername/ on the fresh install.

restart, and your old settings for applications (how the gnome panels are set up, firefox bookmarks, etc) will be restored to how they where.

in the file manager, click view -> show hidden files. all the folders/files starting with a dot (.config, .mozilla, etc) are application settings that are read whenever a given program starts... you can take them, modify them, drop them in other systems, have multiple copies of them to use as 'themes' for a given app, etc etc. clever how that works, huh? :D

---

### Post by dkknight593 on 2009-10-22
When you installed Ubuntu or any Linux OS you should have chosen a seperate home partition.  All your settings will be in there and files too.  When reinstalling you chose custom and mount that partition as Home but not to format.  You'll have to reinstall programs though.

Now if you didn't set up a different home partition then I guess you could create one by resizing with gparted (available in livecd and no changes to drive option) and copying all your files into it. 

I also make sure to give my partitions descriptive labels like "home" so I can figure out what they are when I'm doing install.

---

### Post by iamjfarrell on 2009-10-23
I did actually partition my drive for home. I have 2 drives. One is just a media drive the other is for OS and OS storage. I have 51.2 for windows, 37.6 for ubuntu and 8.4 for swap. It seems if I say install them side by side it wants to use my media drive. If I click use entire disk I can pick between media and OS. Or I can specify partitions manually. What am I supposed to do at this point? Should I try to "unmount" the drives?

---

### Post by Albert Seminatore on 2009-10-23
What will happen, in summary, is you will be asked to define the Linux partitions.  You will have to unmount the "area" you want to designate to Linux.  It might be in an extended partition.  You should plan out how much space you want for Linux which will be formatted in ext3 and the mount will be /; Then define the space for a swap partition and format it with Linux swap.
  Its fairly easy if you sit down and plan it out and then be very careful what you do as you install Ubuntu.
  I would strongly advise getting a disk clone of your system BEFORE making changes.  Then when something goes wrong you can jump back to where you started.  The other alternative is a full backup.  I use Acronis to do this.

---

### Post by iamjfarrell on 2009-10-25
It's not letting me change the drive that I want. My media drive can not be partitioned for an OS. There is no boot order for it. I am stuck on this partition part of the re-install

---

### Post by iamjfarrell on 2009-10-25
k. I got this figured out. I had to delete the 9.10 ubuntu from the drive and then select "use continuous free space". Now I have a fresh 9.04 and I am currently downloading 256 packages haha.

---

