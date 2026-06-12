---
title: "partition editor will not let me format unallocated space"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by shateredsoul on 2009-02-15
Hi,

I have 61 gigs of unalllocated space that I want to give to ubuntu... but it won't let me. When I right click or click on the partition on the list the options to do this are dimmed.. The only option it gives me is "new" (it's a little paper with a plus icon).


Ahhhhh!  ok... i'm good now.  Is anyone familiar with this?

---

### Post by shateredsoul on 2009-02-15
It may help to know that I had a dual boot before.. with xp.  I deleted it...

---

### Post by Pumalite on 2009-02-15
Unmounted first. Or use Gparted Live CD.

---

### Post by shateredsoul on 2009-02-15
ok ok.. so made it to a new partition and now I can reformat it..but one question 

i have /dev/sda4 - extended 
then under that /dev/sda5 -ext3 and /dev/sda6-linux swap

Where do i put this so linux can use it?  I only have two options linux-swap or 3xt-3



I

---

### Post by Pumalite on 2009-02-15
Install using 'Greater Free Space'. That will put Ubuntu in your new partition and the installer will create 2 logical partitions: '/' and /swap.

---

### Post by ugm6hr on 2009-02-15
> **shateredsoul said:**
> Where do i put this so linux can use it?  I only have two options linux-swap or 3xt-3

Not entirely sure what you're trying to do.

But ext3 is the most appropriate format for Ubuntu.

---

### Post by shateredsoul on 2009-02-15
Where do i get to the greater free space option?

in gpartition I right clicked and I don't see that option.


Just to be clear.. instead of saying "unallocated" my partition now reads "new partition # 1.

---

### Post by shateredsoul on 2009-02-15
> **ugm6hr said:**
> Not entirely sure what you're trying to do.

But ext3 is the most appropriate format for Ubuntu.

I'm trying to give space on my hdd (that i used for xp originally when i dual booted) to ubuntu.  I erased the partition for windows.. when it was unallocated I couldn't do anything with it.  So I decided to format it as a new partition.. now it gives me the options to reformat.  

Also, I don't know how to run gparted from the live cd 0_o

---

### Post by redroad55 on 2009-02-15
boot live cd not install > applications > system > amin. > partition editor ... Then delete the unallocated space  partition > this will make it free space > and on the partition next to it make it bigger by including the free space..

---

### Post by shateredsoul on 2009-02-15
oh ok.. i think I get what I was confused about.  So I need to use a gparted live cd, not the ubuntu install cd.  Yeah?  I know.. I know.. sorry.

Let me try that

---

### Post by redroad55 on 2009-02-15
No the ubuntu cd is a live cd when you boot it  .. it gives you the choice to install or just boot it to preview that is the choice you want > then follow post above

---

### Post by Pumalite on 2009-02-15
If you have formatted your drive; all you have to do is boot your Ubuntu Live CD and install using 'Use Entire Disk' option.

---

### Post by shateredsoul on 2009-02-15
If I install using entire disk.. will it erease what I already have done on Ubuntu?  It took me hours to make some programs work.. I don't want to do that all over again  (I was a dual boot before, so I already have a normal install of ubuntu)

---

### Post by shateredsoul on 2009-02-15
in other words.. if I boot from the live cd, and do a full install again (remember I already have ubuntu installed), I will be able to keep the programs I have installed on Ubuntu?

I deleted the windows xp partition ust gparted while using Ubuntu, so I already have that space free.  I just want to make sure that I don't accidentally dual install ubuntu, or erase what I already have done.

I still have the option of using gparted to format the unloccated space to sda5 (where linux is installed), but not sure if that is a good idea.

---

### Post by redroad55 on 2009-02-15
so if the space is designated free the partition to the right is your only choice for making it bigger by using that free space

---

### Post by ugm6hr on 2009-02-15
I'm still a bit confused.  I assume you had a dual boot Ubuntu / Windows, and now want a single boot Ubuntu to use all the HD space.

If you reinstall, you will not be able to keep your programs.

You could just use the newly formatted partition as storage.

I would actually suggest reformatting the partition and using it as a separate /home partition:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) (skip the making a new partition part - you already have a spare partition - just format to ext3)

PS: Deleting the previous XP partition may cause Grub to error, since it is possible you have changed the order of partitions.

EDIT: It might help if you post the output from:
```
sudo fdisk -l
```

---

### Post by redroad55 on 2009-02-15
so if I under stand you correctly you had this before windows / ubuntu or ubuntu / windows  in terms of partition layout ??

---

### Post by shateredsoul on 2009-02-15
yes, dual installed. While in ubuntu (not from the live cd) In gparted when i right click sda5 (where linux is) there is no resize option.  I have this huge unallocated space of about 60 gigs that I want to allocated to ubuntu now that I have deleted windows xp.  

but i right click and have almost no options for the unallocated space or the sda5 either

I have done most of this while running ubuntu.  I'm about to try running the live cd and running ubuntu (the options that says, without any changes to your current system) to see if I can make changes in gparted through there..

---

### Post by shateredsoul on 2009-02-15
actually i just started reformatting the unallocated space to ext3 (the same
as ubuntu) hoping that it will let me resize if it's in the same format. This was done while running ubuntu through the os install i have, not the cd.

---

### Post by shateredsoul on 2009-02-15
nevermind.. it didn't let me resize sda5.. grr

---

### Post by Pumalite on 2009-02-15
sda5 is a logical partition inside of an extended one. You cannot resize it without erasing the extended partition.

---

### Post by shateredsoul on 2009-02-15
even after making the unallocated into ext3 format

---

### Post by shateredsoul on 2009-02-15
oh, so if i want to allocate that space to ubuntu should I resize the extended one?

....

---

### Post by Pumalite on 2009-02-15
Post a screenshot of Gparted showing your drive.

---

### Post by shateredsoul on 2009-02-15
nevermind.. that's not possible either.  So, ok, how do i give this space to the Ubuntu OS?

---

### Post by shateredsoul on 2009-02-15
[IMG]http://img.photobucket.com/albums/v295/indigo2k1us/desktop.jpg[/IMG]

---

### Post by shateredsoul on 2009-02-15
I found this..would this accomplish what I need to do?

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

I don't know how to do that... If I decide to just completely wipe my hdd clean and do a new install ( including removing the option that still asks me if I want to dual boot).  How can I do that?

This is taking longer than it probably would take to just install everything over again.

=(

---

### Post by logos34 on 2009-02-15
Gparted says at the bottom 'operation pending'...try completing it.  Click 'Apply' to delete it, then go back and try to format it.

---

