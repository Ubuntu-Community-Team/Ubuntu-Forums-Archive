---
title: "How can I access my 9.04 partition from 64-Bit Vista?"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by Zachs Kappler on 2009-06-10
After installing 9.04 to replace 8.04, I noticed that many of my EXT reading programs for windows stopped working. The way I have my partitioning is in this order... 

(Vista)(Wolvix2b)(Ubuntu 9.04)[(Home for 9.04)(Swap)]

Any advice or ways to access them from Vista? I wish to not have to boot Ubuntu just to move a file I missed while syncing the User and Home sections.

I've tried Linux Reader and EXT2IFS. The latter asked me if I wanted to reformat the Home partition.

---

### Post by presence1960 on 2009-06-10
if you went with ext4 I don't think that is possible.

---

### Post by spees on 2009-06-15
> **presence1960 said:**
> if you went with ext4 I don't think that is possible.

If this is true, I am screwed... I have the same question as the OP. I was going off this tutorial ([http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)) and I forgot to backup the menu.lst file...Now I have Vista installed an I'm unable to access my Ubuntu partition (at least I think, I'm a linux noob). And I did go with ext4 and jaunty. Anyone have any ideas?

---

### Post by Mark Phelps on 2009-06-15
> **spees said:**
> If this is true, I am screwed... I have the same question as the OP. I was going off this tutorial ([http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)) and I forgot to backup the menu.lst file...Now I have Vista installed an I'm unable to access my Ubuntu partition (at least I think, I'm a linux noob). And I did go with ext4 and jaunty. Anyone have any ideas?

If you're simply unable to boot into Vista, that is not the same problem as the OP.  That problem was trying to read Ubuntu files from inside Vista.

You would do better starting your own thread about not being able to boot into Vista.  Also, you should try searching the forum.  There a lots of posts that deal with the problem you're describing.

---

### Post by Timtro on 2009-06-15
> **spees said:**
> If this is true, I am screwed... I have the same question as the OP. I was going off this tutorial ([http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)) and I forgot to backup the menu.lst file...Now I have Vista installed an I'm unable to access my Ubuntu partition (at least I think, I'm a linux noob). And I did go with ext4 and jaunty. Anyone have any ideas?

I think you're fine. You can fix that. The problem this user has is that the ext3 driver emulators (or whatever) that allow you to see ext3 partitions in Windows, won't work with ext4. Someone needs to write those.

That's the problem with new filesystems: it takes time for them to be fully supported.

---

### Post by Zachs Kappler on 2009-07-12
... I'm using EXT3 on the two Linux partitions...
EXT4 is too new for me to risk using... Maybe later I'll switch...

---

### Post by Zachs Kappler on 2009-08-12
Okay, after using a tool which i found [here]("http://www.fs-driver.org/troubleshoot.html") that can tell what is causing the drive to not be detected. It said the inode size is too big and has to be smaller for it to work. 

The bad news is to change that... I must reformat that partition, a 126Gb partition. Is this really the only way to change the inode size? Or will Ubuntu still consider this partition as the /Home partition after the format?:confused:

---

