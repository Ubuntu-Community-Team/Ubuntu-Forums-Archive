---
title: "how to format a second HD within Ubuntu?"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by canale on 2007-07-06
Hi all,

I have Ubuntu installed on a 40GB HD and I also got a slave HD that I want to format with a Linux file system ( like ext3 ) because NTFS doesn't let me read and write files.
Does anybody knows how do I format my second slave HD without deleting Ubuntu?

many thanks

---

### Post by dreadlord_chris on 2007-07-06
> **canale said:**
> Hi all,

I have Ubuntu installed on a 40GB HD and I also got a slave HD that I want to format with a Linux file system ( like ext3 ) because NTFS doesn't let me read and write files.
Does anybody knows how do I format my second slave HD without deleting Ubuntu?

many thanks

Use gParted for all you partitioning & formatting needs. You will probably need to install it:
```

sudo apt-get install gparted

```
Once installed you'll need to run it with *admin* permissions so, press Alt-F2 to bring up the *Run* dialog:
```

gksudo gparted

```

---

### Post by canale on 2007-07-06
many thanks for your reply. it helped me a lot. I got success in everything except in the most important thing: formatting my HD. I have got 2 partitions on them. I can see them but I can't operate on that disk.
Any help, advice? What can I do to format this disk?
This is my Gparted screen
[IMG]http://www.piervi.com/download/gparted.JPG[/IMG]

---

### Post by dreadlord_chris on 2007-07-06
You should be able to delete those 2 NTFS partitions - then create a new ext3 partition.

---

### Post by canale on 2007-07-06
how do i delete them?

---

### Post by dabl on 2007-07-06
Highlight a ntfs partition with your mouse, then right-click.  I think one of the menu items is delete. If not, with the ntfs partition highlighted, open your "Edit" menu above, and there should be a "delete" item.

---

### Post by stchman on 2007-07-06
Don't forget to hit the apply button whenever you do gparted stuff.

---

### Post by louieb on 2007-07-07
You can't delete the old partitions because their mounted.  You can use the terminal and use the **umount** command   (yes thats right the 1st **n** is missing).
Or get the [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") or [SystemRescueCd]("http://www.sysresccd.org/Main_Page") (my favorite) and run GParted off of a live CD.

---

