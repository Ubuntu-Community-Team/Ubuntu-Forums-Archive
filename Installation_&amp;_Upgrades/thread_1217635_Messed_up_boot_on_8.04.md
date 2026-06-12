---
title: "Messed up boot on 8.04"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by landon420 on 2009-07-19
Hello everyone! I am fairly new to ubuntu. I originally had Windows Xp on my computer on a SATA 80 GIG, I installed Ubuntu 9.04 on my IDE 60 GIG. I decided that it was to buggy and installed 8.04 overtop the 9.04 on my IDE 60 GIG. When I restarted my system and I tried loading 8.04 from the Grub selection menu it said: cannot mount image. Windows Xp would not load either. So what I did was, I went into my Bios and changed the harddisk order. I set it to boot my 60 gig IDE first, and my 80 gig SATA second. Both windows and Ubuntu 8.04 will load now.

What I think the problem is, is that I have two versions of Grub loader; one on each harddrive. What I am unsure of is how to correct that problem if that is the problem. 

If anyone can help me I would appreciate it! Please talk to me as if I am a complete Newb.

Thanks:D

---

### Post by stlsaint on 2009-07-19
my experience with hardy have gone funny as well but the best way would be to completely erase the ubuntu hdd and do a fresh re-install...had you had different partitions on your hdd you could use a boot loader like easybcd and change up your partition boot options but since you did an install over your original install that caused the multiple grubs you see...

---

### Post by presence1960 on 2009-07-20
let's see exactly what you have right now. Download the Boot Info Script 0.32 to your desktop from here: [http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/)

Once downloaded to desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on your desktop. Paste the entire contents of that file back here. Highlight all text when pasted here and click # on the toolbar to place code tags around text.

This will show us your set up, boot info and where GRUB is installed and where GRUB looks to.

Don't go erasing a perfectly good OS. You have it booting now. All you may need is a few tweaks! I would leave the boot order the way it is and probably  restore windows bootloader to MBR of the sata drive, but we'll see what the script says you have. **DON'T ERASE YOUR uBUNTU INSTALL-THAT IS NOT THE EASIEST  OR THE PATH OF LEAST RESISTANCE. THERE IS A SIMPLER WAY!**

I would stay away from Easy BCD for two reasons: GRUB is way more versatile & configurable and does a great job and 2. if you want to learn Linux why use a bootloader which is in the windows OS. You are not going to learn about the most important thing in Linux, whch is how to get your OSs to boot.

---

### Post by landon420 on 2009-07-20
Ok I have fixed my problem. I deleted my 60 GIG IDE data, started my ubuntu live cd, downloaded super grub, burned ISO image to CD, ran super grub boot disc after restart, restored MBR, reinstalled 8.04 back on to me 60 GIG. I can boot Windows or Ubuntu no problem.  

[stlsaint]("http://ubuntuforums.org/member.php?u=814785"):  Deleting the data on the partition and doing fresh install does not work, you will just get get a grub loader error 22. So you are back to square one and now you cannot boot windows period.

[presence1960]("http://ubuntuforums.org/member.php?u=657448"):  Sorry I fixed my own problem before I seen your post, your suggestion looks like it would be ideal for someone who had ubuntu installed and had a lot of time, programs, files, etc; invested into it.


Thanks for all of your suggestions and willingness to help:D

---

### Post by presence1960 on 2009-07-20
> **landon420 said:**
> Ok I have fixed my problem. I deleted my 60 GIG IDE data, started my ubuntu live cd, downloaded super grub, burned ISO image to CD, ran super grub boot disc after restart, restored MBR, reinstalled 8.04 back on to me 60 GIG. I can boot Windows or Ubuntu no problem.  

[stlsaint]("http://ubuntuforums.org/member.php?u=814785"):  Deleting the data on the partition and doing fresh install does not work, you will just get get a grub loader error 22. So you are back to square one and now you cannot boot windows period.

[presence1960]("http://ubuntuforums.org/member.php?u=657448"):  Sorry I fixed my own problem before I seen your post, your suggestion looks like it would be ideal for someone who had ubuntu installed and had a lot of time, programs, files, etc; invested into it.


Thanks for all of your suggestions and willingness to help:D

For future reference you can restore the windows bootloader by doing this: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) provided you have a windows disk, not a recovery partition.

---

### Post by landon420 on 2009-07-20
> **presence1960 said:**
> For future reference you can restore the windows bootloader by doing this: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) provided you have a windows disk, not a recovery partition.


Yepperz I knew about that, would have been my first option. I hope someone else that has the same problem can benefit from these posts.

Peace

---

