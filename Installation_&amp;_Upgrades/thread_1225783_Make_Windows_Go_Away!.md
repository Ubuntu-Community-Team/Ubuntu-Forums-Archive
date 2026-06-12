---
title: "Make Windows Go Away!"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by DrTaylor on 2009-07-28
I'm about to upgrade to Jaunty. Anyone know if it's easy to just redo your partitions at the same time and make the Windows that is taking up most of my hard drive go away?

---

### Post by presence1960 on 2009-07-28
> **DrTaylor said:**
> I'm about to upgrade to Jaunty. Anyone know if it's easy to just redo your partitions at the same time and make the Windows that is taking up most of my hard drive go away?

If that is what you want to do then yes, it is very easy. You have 2 choices : create a partition scheme with Gparted Live Cd or Ubuntu Live CD using Partition Editor. Then when you do the install choose the manual option.

Or the easiest way is to boot the Ubuntu Live CD and choose the "use entire disk option". Bye bye windows...your whole disk will be Ubuntu.

This is a clean install. Download the 9.04 iso and burn it as an image to CD. Back up all your data before partitioning or installing. Once your data is backed up off your hard disk proceed.

---

### Post by merlinus on 2009-07-28
If you have backed up your data, or have nothing of importance on the hdd, then simply select use entire disk at the partitioning screen.

OTOH, you can install 9.04 into your existing linux partitions, and format the windows one as ext3 with a mountpoint of /data, and use it for music, photos, docs, etc.

---

### Post by DrTaylor on 2009-07-28
> **merlinus said:**
> 
OTOH, you can install 9.04 into your existing linux partitions, and format the windows one as ext3 with a mountpoint of /data, and use it for music, photos, docs, etc.

That might be more feasible at this exact moment. Option 1 is a definite thing in the future, but I don't have a good way to back up right now. Is this fairly self-explanitory? I've never done it before.

---

### Post by merlinus on 2009-07-29
Make a note of your existing partitions, e.g. windows on sda1, linux / on sda5.  Choose manual at the partitioning screen, rightclick (or click and then edit) each existing partition, select use as ext3, tick format, and select a mountpoint.  IIRC you can type one in if not on the dropdown list, e.g. /data.

If you have an existing /home partition, do all of the above but DO NOT tick format, or all data will be lost.

No changes will be made until you click forward, or proceed, and even then you will receive a last-chance warning.  If not sure, use the back button to review your choices and options.

---

### Post by racerxnitro on 2009-07-30
okay i have a question dont mean to thread jack or anything. 

how would i take windows off once ive already installed ubuntu?

---

### Post by merlinus on 2009-07-30
Use gparted to format its partition to ext3, and either add it to existing partitions or mount it as /data (or something else) and use it for various files.

Then delete the windows stanzas from /boot/grub/menu.lst.

---

### Post by bert666 on 2009-07-30
i also am trying to delete windows but i am computer retarded (my buddy said to say that and it is quite apt). i couldn't understand the last post.

i backed up my files and i'm ready to get windows off my computer. it is taking up too much space to do anything with ubuntu.

---

