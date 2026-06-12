---
title: "Advice Unscrambling Partitions with gparted"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by convert_mrta on 2009-09-02
Over a series of attempts to reallocate space away from my NTFS partitions in favor of my ext3 linux partitions I have created a mess.  Go ahead, get your laughs out. :redface:  This was/is a newbie, trying stuff out, so give me a *little* credit for trying. This is a dual boot system but I haven't booted Vista in I can't remember when.  It will go away entirely someday soon.

Here's my current situation in gparted:[http://67.205.40.186/images/gparted_shot.png]("http://75.119.205.254/images/gparted_shot.png")

Here's the current line-up:
sda1 - Acer recovery partion.
sda2 - Primary Vista OS partion
sda3 - Extended partition
sda4 - Linux swap
   sda5 - where I have my Vista NTFS data
   sda6 - small partition where I installed my experimental Ubuntu.  I have adopted Ubuntu full time, so this needs expanding

Unallocated - I lopped some disk off of sda5, intending to give it to sda6.  But because of limitation on number of partitions, could not complete this, action and the space is stranded unallocated.

I have sda2 and sda5 mounted and access them regularly from Linux.

I do not want to reinstall, as I've got my ubuntu just the way I like it, and don't want to reinstall all of the apps I've collected over time and love.

I have 1.5 GB of RAM.  I think swap is right for that amt of RAM from what I've read.

What input can wiser Linux-heads give me on allocating the unallocated space to sda6 and actually taking more from sda2 and sda5 and giving it to sda6. 

Thanks very much!

---

### Post by starcraft.man on 2009-09-02
I preface comments with the #1 rule of partition editting:
Backup ANYTHING you can't live without to somewhere other than partitions being edited.

Could be much worse, you tried and that's good. If you want documentation on using gparted, see the documentation [here]("http://gparted.sourceforge.net/documentation.php"). Read through especially resize and move on the old section.

Next, your post gives me impression your doing this while booted to HDD. Best tip I can give, do all partitioning from a live CD, saves trouble. Boot to any live CD then System > Admin > Gparted. Now comments, I personally would use a smaller swap, that's a lot. Maybe half that, at 750MB. To move the free space to sda6, first move it into the extended partition then next to sda6, then resize, for more details see documentation.

I assume your resizing root (/) to get more space for home. I'd advise you instead take time to create a /home partition to store your configuration files and personal files separate from your / partition where your OS system files are stored (the same difference between C: and documents folder in Windows). [See here on how and why to do it.]("http://www.psychocats.net/ubuntu/separatehome") / partition doesn't need to be more than 5-8 GB for average user, home is as large as you want to store. If ya want to move lots of media files and such, more the better.

For the record, we aren't called linux-heads. We might happen to have giant beyond belief sized heads, but that is besides point! :)

I think that answers your questions, if any remain, reply.

---

