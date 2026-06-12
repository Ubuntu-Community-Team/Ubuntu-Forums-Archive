---
title: "[SOLVED] Hard Drive swap"
date: 2008-08-01
forum: General Help
---

### Post by Kain000 on 2008-08-01
Hey everyone,
Just discovered that a 40GB hard drive doesn't go very far for media hosting.   Wondering how I can copy my entire system as is and put it on the hard drive I just ordered (400GB) without having to re-install and re configure my server's settings.  Disk image?  Or just a back up?

---

### Post by crwmike on 2008-08-01
Partimage should do it.

---

### Post by Kain000 on 2008-08-01
> **crwmike said:**
> Partimage should do it.

so is that just a disk image app?

---

### Post by crwmike on 2008-08-01
> **Kain000 said:**
> so is that just a disk image app?

yes

You will need to run it from a bootable CD.

I've been using PING to backup my laptop.

[http://ping.windowsdream.com/](http://ping.windowsdream.com/)

---

### Post by jnw222 on 2008-08-01
gparted livecd has it with testdisk

---

### Post by mgmiller on 2008-08-01
I have the same problem.  I want to move from a 250 GB SATA to a 650 GB SATA drive.  I have the gparted live CD.  It shows 3 partitions on my disk. sda1,2 and 5.  2 & 5 are the swap and seem to be inside one another.  

Do I just copy the main partition sda1 and then the other 2?  

what about resizing to fill the new drive?  

Do I need to do anything to grub?  

I do not have any other OS's on the disk, just Ubuntu.

This should be simple, I may be making it more complex than it really is.

---

### Post by crwmike on 2008-08-01
Use gparted to create partitions of the same size or larger, in the same order on the new drive, (sda1 on the old drive is sda1 on the new drive ..). When backing up the old drive, partimage asks to backup the boot sector (mbr), make sure you say yes to that.

You don't need to copy the swap partitions, just create them in gparted and set its filesystem type to "Linux Swap".

---

### Post by mgmiller on 2008-08-02
Let me make sure I understand.  

I can create the new sda1 partition and make it larger, but with nothing in it.  

I then use gparted to copy the contents of my old sda1 to the new, larger sda1, saying yes to copy mbr?  

Or do I use partimage ( a different program?) to do the copy from old to new?

---

### Post by linfidel on 2008-08-02
You can use gparted (or the command-line dd) to copy the existing partitions to the new disk.  Either one will copy the guids, too, so you don't want to have both mounted at the same time.  After copying, you can resize whatever partitions you want, or even create a new partition for the media.

In gparted, it is simply a cut and paste operation.  The advantage to keeping the guids is that you don't need to edit your grub menu.lst at all.  

But you will probably need to install grub on the new disk, which you can do using any grub, from the command line of a live CD.  For example, to install grub on sda1, you would enter:
root (hd0,0)
setup (hd0)

I haven't gone into detail, as I don't know how familiar you are with various tools, but if you need more detail, feel free to ask.

The gparted cut and paste may not be the most efficient method, but it's probably the simplest, and easy see what is happening, and to undo if it's not right.

---

### Post by mgmiller on 2008-08-02
> But you will probably need to install grub on the new disk, which you can do using any grub, from the command line of a live CD. For example, to install grub on sda1, you would enter:
root (hd0,0)
setup (hd0)

Are those the actual commands at the command prompt, or are they lines edited into menu.lst  ?

Also, are you saying I should just use gparted to copy sda1 and then resize it?

---

### Post by linfidel on 2008-08-02
> **mgmiller said:**
> Are those the actual commands at the command prompt, or are they lines edited into menu.lst  ?

Also, are you saying I should just use gparted to copy sda1 and then resize it?
Those commands are actually grub commands, at the grub prompt.  You can just type grub at the command line, although I think I've read that it's safer to run grub from a live CD, although I've never had problems running it from the running system.  But running from a live CD lets you test things and fix it quicker.

If you're not familiar with grub, once you're on the command line, pressing tab will give a list of all commands (quit exits grub).

And yes, in gparted, you can select a partition, select the menu "partition", "copy", then paste to the other drive.  You will need to do this from a live CD, though, as the partition can't be mounted. 

Also, if both drives are installed at the same time, you would need to substitute hd1 where ever I said hd0 for installing grub.

---

### Post by mgmiller on 2008-08-02
OK, I think I have enough info to proceed once my new hdd arrives.  After I fumble through this, I may write a HowTo to simplify it for others.

This really should be a pretty straight forward thing to do, maximizing gui interfaces where ever possible to make it as noob friendly as possible.  

This is the sort of thing I used to do in Windows with very little drama, using free tools.  

There is no reason, given clear instructions, why this can't also be reasonably easy for an Ubuntu user.

Thank you all for your help.

---

### Post by linfidel on 2008-08-02
> **mgmiller said:**
> OK, I think I have enough info to proceed once my new hdd arrives.  After I fumble through this, I may write a HowTo to simplify it for others.

This really should be a pretty straight forward thing to do, maximizing gui interfaces where ever possible to make it as noob friendly as possible.  

This is the sort of thing I used to do in Windows with very little drama, using free tools.  

There is no reason, given clear instructions, why this can't also be reasonably easy for an Ubuntu user.

Thank you all for your help.
You're welcome.:)

It would be a good idea to document what you do - when I was doing similar things, I didn't, so I don't remember all the details, just the lessons learned - especially the one about the UUIDs.  I had both drives in, and there were duplicate UUIDs, so it was hard to determine which partition was actually booting for a while.  If you want to have both available in the future, there is an easy command to generate new UUIDs.

But, I can tell you as a long-time Windows user, that I now feel much more confident with linux than windows, and it's much easier to do with Linux.  Try copy and paste with Windows fdisk!:lolflag:

And grub is actually pretty easy once you get the hang of it.  Try setting up multiple Windows partitions using Windows itself.  But grub could do it.

I'll try to check back regularly in case you have questions.

---

