---
title: "Unable to resize and move partitions with gparted"
date: 2007-06-22
forum: Hardware &amp; Laptops
---

### Post by motoperpetuo on 2007-06-22
Please see my attachment. What I would like to do is allocate half of my 39.31gb of unallocated space to my 46.68gb Windows XP parition (/dev/sda1) and half to my 23.84gb Ubuntu partition (/dev/sda2). 

Is this possible with gparted? So far I'm only able to shrink the XP and Ubuntu partitions which produced the small amount of unallocated space between them). I gather that I may need to move my partitions around so that the 39.31gb of unallocated space borders the XP and Ubuntu partitions that I want to grow, I just can't figure out how to do this.

If this isn't possible with gparted, is there any other way to allocate this unallocated space to my XP and Ubuntu partitions without reformatting?

---

### Post by diatribe on 2007-06-22
you can not run gparted on mounted paritions, you will have to boot from either the livecd or a gparted livecd to resize your linux paritions

---

### Post by stchman on 2007-06-22
> **motoperpetuo said:**
> Please see my attachment. What I would like to do is allocate half of my 39.31gb of unallocated space to my 46.68gb Windows XP parition (/dev/sda1) and half to my 23.84gb Ubuntu partition (/dev/sda2). 

Is this possible with gparted? So far I'm only able to shrink the XP and Ubuntu partitions which produced the small amount of unallocated space between them). I gather that I may need to move my partitions around so that the 39.31gb of unallocated space borders the XP and Ubuntu partitions that I want to grow, I just can't figure out how to do this.

If this isn't possible with gparted, is there any other way to allocate this unallocated space to my XP and Ubuntu partitions without reformatting?

It would be best to boot up using the LiveCD then use gparted.  Gparted supports NTFS resizing.  If you are using Feisty LiveCD disable automount.

The 27G you have for Ubuntu is PLENTY enough space.  I would recommend leaving sda2 at its present size, format and mount the unallocated part to EXT3.  You can then grow sda1 to fill the small unallocated space between sda1 and sda2.

---

### Post by motoperpetuo on 2007-06-22
I should have specified that I am trying to do this from the gparted live CD (although my attachment is from a screenshot I took after booting into Ubuntu). It's my understanding that when you boot to the gparted live CD, the partitions on your hard drive are not mounted, and I am able to shrink my existing partitions, so I don't think the problem is that I need to unmount my partitions. 

What I really want to know is whether it's possible to do what I described in gparted (split up the unallocated 39.1gb of hard drive space and allocate it to my existing ntfs and ext3 partitions). Gparted just doesn't seem to give me the option to move partitions or make my existing ntfs and ext3 partitions bigger, but maybe I'm not understanding how to do this for some reason.

For example, would it be possible to move my 1gb swap partition to the right of the 39.1gb of unallocated space?

---

