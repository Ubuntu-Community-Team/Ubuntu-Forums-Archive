---
title: "[SOLVED] Help, can't boot into Windows"
date: 2008-07-18
forum: General Help
---

### Post by rudedoggx on 2008-07-18
Hey, I've been dual-booting between Windows XP Media Center and Ubuntu using Wubi, but I recently ran into a problem. I changed some settings in Windows so that Wubi is the default on the list of OS's you choose from at boot. I also unchecked the box that allows a timer, so it automatically boots into Ubuntu. From here, I thought I'd be able to boot into windows by pressing ESC when it says "Press 'ESC' to enter menu, but when I select Windows XP to boot, it says:

error occured while savedefault

can anyone help, please?

---

### Post by jimv on 2008-07-18
Can you post the contents of hte boot.ini file on your windows drive?  You should be able to access it from Ubuntu.

---

### Post by rudedoggx on 2008-07-18
I have my Disk partitioned into C and D, and Ubuntu is in C. Will I still be able to view Windows system files?

Thanks for your response, too :)

---

### Post by jimv on 2008-07-18
Yeah, you should be able to see them.  If you go to Places > Computer, you should see all the drives on your computer.  Just look through them until you see your Windows drive.  Then open the boot.ini file and copy/paste it here.

---

### Post by rudedoggx on 2008-07-18
Hm, I just got another weird problem. When I clicked on that green running man in the top corner, the bar on top disappeared.

---

### Post by jimv on 2008-07-18
Yeah, weird.  Press control+alt+backspace to restart the xserver.  That *should* fix that.

---

### Post by rudedoggx on 2008-07-18
Ok, I found the boot.ini 

Well, it's pretty obvious what to do now that I've found it. Thanks, I'm marking this as solved.

---

### Post by Mgiacchetti on 2008-07-18
Post your /boot/grub/menu.lst

you may also want to forget wubi and do a clean install straight from the cd, if you have to edit your partition(s)  SCANDISK DEFRAG SCANDISK RESTART to make sure everything is clean b4 hand.  Also may wish to look into [BootPart]("http://www.winimage.com/bootpart.htm") for using NTLDR (boot.ini) for your bootloader and [Fix-Mbr]("http://askbobrankin.com/fix_mbr.html") if you accidentally fudge up your mbr.

If you do go this route, you will definately need to know how to manually partition your ntfs drive if you only have one disk/part, however if you already have ubuntu installed, you should already have a partition made just be sure to select it and the swap.  

Next is the tricky part, I have found if you rely on grub for all your booting needs, windows gets lost.   The solution to this is to go with our buddy above, BootPart.  Its freeware and it grabs the boot sector of your linux partition and saves it to the windows drive, then adds an entry to the Boot.ini and voila, you have saved headache with windows getting lost.  The thing you have to remember is to hit the advanced button near the end of ubuntu setup (the page where it outlines all your previous settings before actually installing ubuntu)  in the window that pops up you want to make sure grub is installed to the ubuntu partition and not the swap or windows partitions,  then when thats done, and setup is finished, restart...  you will notice that it went back to windows, no worries, just make sure bootpart is in the root of c:\ and 
```

Start > run > CMD 

cd \

bootpart

```at this point it will tell you all your disks and partitions, something similar to this:
```

Physical number of disk 0 : 89799
 0 : C:* type=83  (Linux native), size= 19535008 KB, Lba Pos=63
 1 : C:  type=b  (Win95 Fat32), size= 19792080 KB, Lba Pos=39070080
 2 : C:  type=5  (Extended), size= 875542 KB, Lba Pos=78654240
 3 : C:  type=82   (Linux swap), size= 875511 KB, Lba Pos=78654303
Physical number of disk 1 : d1e0d1e0
 4 : D:* type=7  (HPFS/NTFS), size= 120053713 KB, Lba Pos=63
Physical number of disk 2 : ffffffff
 5 : E:* type=7  (HPFS/NTFS), size= 312568641 KB, Lba Pos=63

```as you will notice here the linux partition is partition "0" so:
```

Bootpart 0 LBA ubuntu.lnx "Ubuntu"

```This will automatically take the bootsect from the Ubuntu Partition and save it to C:\ubuntu.lnx, then add the corresponding line in the Boot.ini and NTLDR is now your main boot loader.

Just to see it in action, go ahead and restart.  you will notice that windows is the default here, but this can easily be changed by just editing the boot.ini file's default line.


I know i made you walk a thousand miles to go ten feet, but hey, at least you're learning something. :)

And now the main point of doing it this way...   YOU CAN NOW REMOVE ALL INSTANCES OF WINDOWS FROM YOUR /boot/grub/menu.lst, plus make it 5 timeout and hidden. so you only have one bootloader (virtually) to deal with... and if you run into problems just hit esc and load your previous kernel.

---

### Post by Mgiacchetti on 2008-07-18
wow all that time writing a solution and its already fixed.....  :(

---

