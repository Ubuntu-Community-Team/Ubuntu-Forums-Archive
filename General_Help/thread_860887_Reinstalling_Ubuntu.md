---
title: "Reinstalling Ubuntu"
date: 2008-07-16
forum: General Help
---

### Post by Shunsuke_01 on 2008-07-16
I have the 8.04 ISO file needed to install Ubuntu, but I have formatted my whole HDD which has completely removed Windows. I'm happy using Ubuntu, but is there anyway to reinstall it using a live CD?

Also, how could I reinstall Windows?


Thanks, 

Chris

---

### Post by NikoC on 2008-07-16
First I would reinstall windows and then ubuntu via the available livecd.
This way ubuntu gives you the option to start windows at bootup, a so called dual boot option.

Cheers.

---

### Post by Shunsuke_01 on 2008-07-16
> **NikoC said:**
> First I would reinstall windows and then ubuntu via the available livecd.
This way ubuntu gives you the option to start windows at bootup, a so called dual boot option.

Cheers.

That is what I was thinking, but how can I install Windows using the CD?

Do I need to boot straight off it or something?

---

### Post by NikoC on 2008-07-16
You don't have a windows cd laying around there?

---

### Post by Shunsuke_01 on 2008-07-16
> **NikoC said:**
> You don't have a windows cd laying around there?

I do, but I am unsure how I go about installing it. :confused:

I've never installed a version of Windows before. :)

Edit: OK, I'll try to boot off the CD. I'll be back with my results in a few hours.

---

### Post by Kigresyl on 2008-07-16
Dual booting is pretty easy now.

1. Get your Windows CD and burn the Ubunutu ISO to a CD(or DVD if you're having problems with the CD working properly)

2. Install Windows like normal, except make sure you leave at least a few GB of free space for Linux.

3. Boot from the Ubuntu CD into live mode.

4. If your non-Windows partition is not formatted, skip to step 9.

5. If your non-Windows partition is already formatted, open a terminal(Applications > Accessories > Terminal) and type in
```
sudo gparted
```

6. Select the non-Windows partition(Be Careful!), choose to delete the non-Windows partition.

7. Once you've verified that you're deleting the appropriate partition, hit Apply.

8. If everything was successful, close out gparted.

9. Run the installation, and when it gets to the partitioning section, choose to use the largest contiguous free space.

10. Finish the installation like normal, Ubuntu is great about dual-booting and configuring GRUB to boot properly.

---

### Post by WRDN on 2008-07-16
The Windows installation is pretty simple.Just boot the disk, press Enter and press F8 to accept the License Agreement. Now you have to choose the partition you want to install Windows on. You could make the partition at this point, or you may want to use a program such as GParted, with a GUI. So, just select the partition, format to NTFS (Full) and let it to its thing. You may want to consider having 2 NTFS Partitions, one for data and one for the Windows Operating System. Consequently, if you ever want to/ have to wipe the partition to reinstall or completely remove the OS, you still have your data. Ubuntu could also access this partition, as it can both read and write to NTFS. For Ubuntu, you should have a root (/) and swap partition, and you may also want a small /home partition where all your settings can be kept. Again, this would allow for Ubuntu to be wiped/ reinstalled and you wouldn't loose your settings.

---

