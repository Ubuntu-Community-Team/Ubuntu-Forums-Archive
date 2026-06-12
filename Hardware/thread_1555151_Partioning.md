---
title: "Partioning"
date: 2010-08-17
forum: Hardware
---

### Post by GaryReggae on 2010-08-17
Not sure if this is the best forum but here goes anyway.

I have recently migrated my laptop from Windoze to Ubuntu and I have been very impressed - so much so that I have deleted all the Windoze program files. 

Ideally, I want my entire HDD to be one partition with Ubuntu and my files on, however I am having some problems with resizing the partitions. I have removed most of what I want from my old Windoze partition to my Ubuntu 'home' folder. However, this has now become full and I need to create more space for it. I shrunk the original Windoze FAT32 partition by half using GParted but cannot figure out how to enlarge the Ubuntu partition to use the space. 

I then tried to create a temporary partition that I could move my stuff to and then try to enlarge and this worked but is unusable, as it appears to be read only. There doesn't appear to be any option to change the permissions so I can use the temporary store and it is also not possible to change my main Ubuntu partition size.

I have tried 'unmounting' the temporary partition but it doesn't make any difference. The main Ubuntu partition doesn't appear to be resizable (probably because it is in use) but I would happily settle for two partitions - one with the Ubuntu system files on and the other with my documents on, but as I said, it won't let me create partitions that are writable. If I had know, I would have left everything on the FAT 32 partition and put up with it!

Another question, now I have got rid of Windoze, can I get rid of the bootup menu that asks me what OS I want to run? I want it to boot to Ubuntu every time.

Anyway, thanks in advance for your help, I'm sure I'm just having 'teething problems', but it certainly feels good to be running this machine without Windoze - my mobile broadband dongle kept causing crashes under Windoze but it installed very easily and works very well under Ubuntu.

---

### Post by Naitsirhc Hsem on 2010-08-17
For the first part, you can't edit the partition you have booted from so get out the live cd you used to install ubuntu and boot your computer from it in try ubuntu mode.  this will allow you to use gparted to resize your partitions.  I am not an expert on grub, I can get by, so I will let someone else help you on that.  if no one helps in a day or so, I will be happy to give some advice.  I will tell you that it is possible to remove windoze from the grub boot loader.  Have Fun!

---

### Post by dcollier on 2010-08-17
Try using gparted, meaning download a copy of the application, delete the old windows partition and resize it.  It sounds like you are trying to resize the partition while you are using it.  As far as the boot menu, edit your grub file and delete the windows entry. /boot/grub/menu.lst

---

### Post by ajgreeny on 2010-08-17
> **dcollier said:**
> Try using gparted, meaning download a copy of the application, delete the old windows partition and resize it.  It sounds like you are trying to resize the partition while you are using it.  As far as the boot menu, edit your grub file and delete the windows entry. /boot/grub/menu.lst
Probably not!.
If you are on 10.04 there will not be a **/boot/grub/menu.lst** file to edit, as it will be using grub2.  All that is needed after deleting the windows partition and enlarging the ubuntu to fill the space, is to run ```
sudo update-grub
``` in terminal, which will remove the windows entry automatically.

The rest of the info about using gparted is correct, but you do not need to download **gparted live CD** if you already have a ubuntu live CD, as gparted is on that already.

---

### Post by GaryReggae on 2010-08-23
Thanks for the replies, I think I am getting somewhere now. I have ran GParted off the live CD and managed to create a '19 Gb File System'. This looks like a good place to shove my files so I can bin the Windows partition but it appears to be read only. Pasting items into it and making new folders etc is greyed out. I have had a look around the menu system in GParted and in the general file system but cannot see any way of setting the permissions so I can write to the 19Gb file system and haven't found anything of use under Help either.

Any ideas? I am sure it must be something simple I am missing.

Thanks,

Gary

---

