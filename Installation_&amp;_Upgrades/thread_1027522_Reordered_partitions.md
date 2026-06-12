---
title: "Reordered partitions"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by doglover56 on 2009-01-01
Hello all. Happy New Year. That partition magic has a mind of its own, I tell you. My Grub won't boot now, gives a #15 error. Grub starts, loads stage 1.5, then says something like "Starting GRUB", then #15. 

I have a multiboot PC with numerous windows and linux installations on it. I had used cfdisk to make the partitions as I needed them, and in the extended partition they were in a jumbled order ie sda6 then sda5 then sda8, 10, 9, etc.
I was in windows and added a partition sda14 at the end using Partition magic, and it went ahead and changed the order by renaming all the partitions in the partition table and now they are in the same physical order but cfdisk now shows them to be sda5 through 14 in order. 

Using Knoppix, I see that all the partitions are still there, appear to be intact, but the menu.lst in the most recent GRUB now has all the wrong device numbers. (I assume this is the menu.lst GRUB is using, it looks like the one I was seeing on the menu page, though each of the older linuxes also has its own grub and menu.lst)

So, as in prior posts I researched, I went in and edited the file so that all the (hd0,x) point to the correct places, and assumed all would be fine. The "default" file which has a single "9" in it I left alone, though I am not sure what that does, though I think that is the old default not the new one.

I assumed that would work, but it doesn't. Given that the partitions are all named differently now, how do I make sure that the GRUB is pointing at the correct menu.lstor can even find it? Is there something else I have to do?

I am reading about update-grub and grub-install, but the instructions don't seem clear to me. Please let me know what I am missing.

Thanks,
Irwin

---

### Post by logos34 on 2009-01-01
> **doglover56 said:**
> I assumed that would work, but it doesn't. Given that the partitions are all named differently now, how do I make sure that the GRUB is pointing at the correct menu.lstor can even find it? Is there something else I have to do?

You can correct the menu.lst 'root' lines all you want, but if you don't also reinstall grub to the MBR so that it points to the right / location, then grub stage1 can't find it, hence the error message.

The 'default 9' option means that grub will automatically boot the tenth OS/kernel entry listed below (grub starts counting at '0')

So restore grub as described in the link in my signature below.  

If you should have any problems, post the output of 

sudo fdisk -l

indicating which is ubuntu / partition

---

