---
title: "External USB hard drive as 'Primary partition'"
date: 2008-07-31
forum: General Help
---

### Post by Zeedok on 2008-07-31
I am trying to get a new 'media player' hard drive enclosure to work.  I have successfully installed the hard drive (which I had previously formatted with Gnome Partition Manager - all as Fat32) and it works fine as an external hard drive, BUT . . .

When I plug the 'media' player into the TV, it goes a little nuts!!

The instructions describe formatting the hard drive as 'primary' not 'extended' - I'm hoping that's the problem (and that it is easy to fix!!).  According to Gnome Partition Manager, my hard drive is 'extended'.

Can Gnome partition manager rectify this?  I am resigned to the fact that I will probably have to reformat - which is fine - is there another tool to use if Gnome Partition manager can't 'manage' it?

---

### Post by coffeecat on 2008-07-31
> **Zeedok said:**
> Can Gnome partition manager rectify this?  I am resigned to the fact that I will probably have to reformat

Yes and yes.

Go into Gnome partition editor, select the extended partition and delete. In fact I should think you'll find there is a logical partition within the extended partition and you will have to delete that first. An extended partition is simply a 'container' for logical partitions - you cannot use one directly for data storage.

Anyway, delete away until all space is unallocated. Highlight the unallocated space and click on new. From 'Create as' select 'Primary Partition' (this should be the default). Select filesystem type and ensure that the size is covering the whole HD. Now OK that and click on 'apply' and you should have yourself one single primary partition.

---

### Post by Zeedok on 2008-07-31
Thanks for your reply.  I looked on - shock horror - a windows forum site and found a discussion about primary and logical partitions, so I think I understand the concepts.

I only use Gnome partition manager every year or so, so I had forgotten about deleting partitions before making big changes.  Thanks again - I just hope re-formatting everything will fix the glitch the media player seems to have . . . (I've emailed the company's tech support to, so fingers crossed!!).

---

### Post by coffeecat on 2008-07-31
> **Zeedok said:**
> I looked on - shock horror - a windows forum site

[-X

:wink:

> **Zeedok said:**
> and found a discussion about primary and logical partitions, so I think I understand the concepts.

There are two important things to remember:

1 You are limited to only four primary and/or extended partitions. If you are going to need more than four, make sure you've made an extended partition big enough for enough logical partitions for future requirements. You can have quite a few logical partitions in one extended - I can't remember the limit. More than I've ever needed anyway. :)

2 Windows can only boot from a primary partition. Linux, however, can boot from either a primary or logical partition. :cool:

---

### Post by Zeedok on 2008-07-31
Yeah, I'm not sure what the media player software is able to read.  I guess I could try one 'Primary' and put all my media in there, and some extended ones for other files - hopefully the media player will not go nuts!!

---

### Post by Zeedok on 2008-08-02
Just an update.

I have formatted my hard drive as a primary partition (Fat32) and the media player works perfectly!!

---

