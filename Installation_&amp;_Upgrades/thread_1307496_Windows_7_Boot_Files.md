---
title: "Windows 7 Boot Files"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by OpenTangent on 2009-10-31
This one goes a bit beyond the call of duty for Ubuntu Forums but quite frankly if i'm going to find a solution for this, this is where i'll find it.

I've partitioned an 80GiB drive into 1 ntfs partition, 1 ext4 partition and a bit of swap at the end. I have a second 250GiB drive in the PC which i use for storage. Normally when doing a reformat and repartition i remove the storage drive to avoid any accidental data loss (which embarrassingly, has happened before).

This time i decided i could trust myself so i left the storage drive in and the repartitioning completed without any problems. I proceeded to install Windows 7 (purely for gaming) on the ntfs partition and thereafter i installed Ubuntu Karmic on the ext4.

Only once Ubuntu was nicely configured did i notice that Windows 7 had installed all it's boot files on my storage drive. The problem is that i need to be able to remove that drive if necessary without having an impact on the boot process. I found [this thread]("http://www.sevenforums.com/general-discussion/11294-moving-boot-manager-different-drive.html") which describes how to fix this from the windows 7 side but i need to make sure that grub also points to the right place once the files are moved.
[]("http://www.sevenforums.com/general-discussion/11294-moving-boot-manager-different-drive.html")

---

### Post by Herman on 2009-10-31
Once you get your Windows 7 boot loader files safely copied over into your Windows 7 and have them set up properly, (with the boot sector installed), try running the following command to make sure GRUB 2 will detect your Windows 7 as a bootable Operating System and add it to your GRUB Menu,
```
sudo grub-mkconfig 
```That command doesn't really do anything, it's just a test to show you what GRUB can detect and how it would have written your grub.cfg if you really want to write a new one.

If all went well you'll probably see two entrys there for Windows Vista or Windows7.
Assuming you do, then it should be asfe to go ahead and delete the unwanted extra copies of the Windows boot files if you like. (Or just leave them there if they're not hurting anything, you never know, they might come in handy some day).

When ready, run 'sudo grub-mkconfig -o /boot/grub/grub.cfg' to make you a new grub.cfg file with your Windows entry (or entries) included.
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

---

### Post by OpenTangent on 2009-10-31
Thanks Herman, i appreciate the help. I'll let you know how it goes.

---

### Post by Mark Phelps on 2009-10-31
> **OpenTangent said:**
> ..I found [this thread]("http://www.sevenforums.com/general-discussion/11294-moving-boot-manager-different-drive.html") which describes how to fix this from the windows 7 side[/URL] ... 

Have you actually tried the steps in that thread and found them to work?  Saw the phrase "show stopper" mentioned several times, so I couldn't really tell from that thread whether or not that approach worked.

I'm asking because another method would be to burn a Recovery CD (using the built-in Windows 7 capability), shutdown the machine, disconnect the external drive, reboot from the CD, and run Startup Repair -- which will install the Win 7 files to the internal drive.

After that boots OK, you could then reconnect the external drive and remove the Win7 boot files from it's partition.

---

### Post by OpenTangent on 2009-10-31
Thanks for the help, but i ended up reformatting and starting over. Everything is configured nicely.

---

