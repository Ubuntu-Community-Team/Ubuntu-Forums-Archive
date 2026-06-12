---
title: "Reinstall for dual boot"
date: 2008-09-17
forum: General Help
---

### Post by nooob75 on 2008-09-17
Hi, I need some help. I installed ubuntu and did a full install wiping windows out. I now need to uninstall ubuntu and reinstall windows so later I can do a dual boot. I tried booting from my win xp home disk and after about 20 min. the blue screen said something in the system was corrupt, I didn't see it in time and when I did the screen went blank and computer shut down so I couldn't read it. But either way I am sure there is more I have to do to install windows again besides just boot the cd. It's an emachine and I need to get windows installed again asap as my daughter needs it for school work. Do I need to partition a space for windows to install(if so how?) for a dual boot or completely wipe ubuntu then install windows, then a dual boot? If so, HOW??? 
Any help is much appreciated. I am completely new at this ubuntu thing so please keep that in mind if and when you can answer my question, I'm confused enough! Thanks a bunch.

---

### Post by Kevanx on 2008-09-17
It would be enormously helpful if you could offer us the exact error message that windows gave you.

In the meantime, it is most likely that there is simply not an appropriate filesystem for windows to use. Put simply, windows and linux run off of different disk formatting -ext3 for linux, NTFS for [windows XP and beyond]("http://www.microsoft.com/windowsxp/using/setup/expert/russel_october01.mspx") so you will need to create a partition for windows to be installed on. This is actually very easy.

First of all, creating a partition can wipe out data, so I would back up anything and everything that you wouldn't want to vanish, particularly settings and documents in your /home/user/ directory (including hidden files and folders), when you reinstall ubuntu. Please don't hold me responsible for anything that goes wrong.

Once you're ready, here's what you do.

Boot up a Ubuntu Live CD (reboot, and press F12 or Shift, or whatever your boot screen tells you to get to BOOT OPTIONS). Choose your CD/DVD player, or the Ubuntu Live CD if it's indicated.
This will allow you to modify your hard drive as needed, because it won't be running the operating system!

Open up a terminal (ACCESSORIES > TERMINAL )
and enter:
```
gparted
```
Gparted is a graphical partition editor. You might need to write ```
sudo gparted
```
instead, but I don't think that's the case with a live CD.

Now, you can either RESIZE an existing partition to make room for a NEW partition for windows to go on, or you can delete all of the partitions you have (you can resize it later if you want to install Ubuntu). Right clicking on a partition will give you these options.

To resize: You have at least two partitions (ext3 and linux-swap).
Resize whatever partition is the LARGEST, including any other partitions, such as a partition with a mount point of /home. Reduce its size by whatever amount you want to donate to windows.

Once you have space (either by resizing or deleting), create a NEW partition. Choose an NTFS filesystem. Make it bootable, either in the wizard, or right click on the new partition, and click manage flags. Then make sure that the box that says "BOOT" is checked.

Click the APPLY button, and let it do its thing. When prompted, reboot, and stick in the WINDOWS install CD.

NOTE: If you have chosen to have DUAL BOOT, windows will overwrite grub, and you won't be able to boot into Ubuntu anymore. To fix that, just follow this guide:
[http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")

Hope this helps, and that you haven't given up on Ubuntu!

---

### Post by jazzcommunication on 2008-09-17
I don't know what you mainly do with your pc, you can run windows in ubuntu by installing vmware player, this works fine for normal applications (no games)

[http://ubuntuforums.org/showthread.php?t=832287](http://ubuntuforums.org/showthread.php?t=832287)
[http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html](http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html)

follow those 2 links, if you have questions,let me know

So you not realy need dual boot,to run windows
greetings from Vietnam

---

### Post by nooob75 on 2008-09-17
Kevanx,

I don't know if I did something wrong, I started to delete all partitions, only the first one would delete, the largest. The others won't delete so I moved onto next step, made it a ntfs and tried to click manage flags, no option to do this so I cannot make it bootable. Don't know what to do next, will wait for an answer...thanks!

---

### Post by Kevanx on 2008-09-17
That's strange. I'm booting up now with a live CD to see, but if you can tell me exactly what it says regarding the partition when you try to delete it, that would help. Is it simply greyed out? Is there an error message? Same with the results when trying to make the NTFS partition bootable.

EDIT: One possible cause is that [gparted requires an NTFS partition edit to reboot first]("http://gparted.sourceforge.net/larry/resize/resizing.htm") (see part 2 - What happens with NTFSD ...). Try installing windows now regardless, provided that the partition that you made is large enough. Hopefully then you should be able to delete the other partitions (and resize the NTFS partition) afterwards, if needed.

Please mark this thread as SOLVED if appropriate.

---

