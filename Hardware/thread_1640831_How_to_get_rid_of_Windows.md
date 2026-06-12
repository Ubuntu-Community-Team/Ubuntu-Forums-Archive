---
title: "How to get rid of Windows??"
date: 2010-12-08
forum: Hardware
---

### Post by Skopuningurin on 2010-12-08
Hi

I got a Acer 6930G which has two 500gb harddrives.
I have Windows on one, and Ubuntu on the other. My question is : How do I delete the windows harddrive ( Or windows on the harddrive ?? )? Can I use Disctools in Ubuntu, and delete the Windows partition from there even if it is on the other harddrive? Or is there another option?

I am running on Ubuntu 10.04

---

### Post by matt_symes on 2010-12-08
Hi

You can use gparted to remove the windows partition and repartition as you want. You can also format each new partition you create. You can get it from synaptic package manager.

Just make sure the partition is not mounted when using gparted.

Kind regards

---

### Post by slick666 on 2010-12-08
If you're looking to put ubuntu on both you're going to have to set up mount points for the other HD or use software raid.

[https://help.ubuntu.com/community/Installation/SoftwareRAID#Installing]("https://help.ubuntu.com/community/Installation/SoftwareRAID#Installing")

If you're thinking of raid then I suggest a fresh install. It was just easier for me to do it that way.

---

### Post by marko.games on 2010-12-08
just format that partition :P

---

### Post by Skopuningurin on 2010-12-08
So you are saying that, If i follow those instructions, my two harddrives will act as one?
I am a noob at Ubuntu..

---

### Post by matt_symes on 2010-12-08
Hi

> So you are saying that, If i follow those instructions, my two harddrives will act as one?
 I am a noob at Ubuntu..

No we are not. What you can do is format the hard drive to ext3, ext4 or ntfs and then add an entry into your fstab file. 

You will then be able to access both hard drives and store information on both but they will be considered separate. I.E. They will have separate mount points, but you will be able to use them both.

There is a technology called logical volume management (LVM) that allows you to treat multiple hard drive as one single drive, but as i have never used it i cannot advise on it. Maybe someone else here how has used it can shed some light on it.

Kind regards.

---

### Post by Fafler on 2010-12-08
Using stuff like LVM or RAID0 on several drivers without any kind of redundancy is *always* a bad idea. One drive dies and all your data is lost.

Format the drive and mount it at /home/you username/Desktop/Data or something like that.

---

### Post by Skopuningurin on 2010-12-11
[I]Well. To be honest with you guys ; I don't understand what you all talk about. I'm a complete noob at this.

Let me try something else.

If I install fx _Maverick Meercat or Karmic Koala   _on the windows harddrive, can I then still access both the drives? In other words, If I have Ubuntu on both HDD, am I able to access one drive from another if I have Ubuntu on both?


[/I]

---

### Post by amsterdamharu on 2010-12-11
> If I install fx _Maverick Meercat or Karmic Koala   _on the  windows harddrive, can I then still access both the drives? In other  words, If I have Ubuntu on both HDD, am I able to access one drive from  another if I have Ubuntu on both?[I]

yes you should be able to acces both drives (mount them by clicking on them in the file browser). You have to make sure your user of both ubuntu's have the same ID or you might not be able to delete or change files on the other harddisk. But you can cross that bridge when you come to it.

More importaintly is that you haven't seem to be using Ubuntu that long and already want to get rid of Windows. I am happy with Ubuntu for 1.5 years now but still won't get rid of Windows. You might find yourself in a situation where you need it and then have a total fit about Ubuntu not being able to do it, worse even is that you got rid of windows. I would advice you to keep windows for a while, if the partition is too big then you can use gparted to resize it (risky but you wanted to get rid of it anyway).


[/I]

---

### Post by WinRiddance on 2010-12-11
YES ... if you simply install Ubuntu on any of the existing drive volumes you'll be able to access both drives once you're logged into your Ubuntu system. If the second hard drive was previously already formatted either as NTFS (for Windows) or EXT3 or EXT4 (Linux Ubuntu) then you'll be able to access that second drive volume immediately because normally the latest versions of Ubuntu recognize and mount such drives automatically, thereby providing accessibility right from the beginning.

However, if that second drive volume had not been formatted at all for whatever reason, then you'll need to open up the **Disk Utility**, located from the MAIN MENU in SYSTEM and then ADMINISTRATION. The Disk Utility (prettier, and easier to use than Gparted, for newcomers) will recognize all of your attached hard disks. You can then select a disk and format a drive with the click of a button. Afterwards, if you like, you can easily create and adjust partitions on that drive too. Good luck! ;)

---

