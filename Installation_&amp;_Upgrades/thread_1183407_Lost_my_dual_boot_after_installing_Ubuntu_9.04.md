---
title: "Lost my dual boot after installing Ubuntu 9.04"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by kyleryner on 2009-06-10
Help! I had a dual boot system for Vista and XP. I used Vistapro as the boot manager. I also used wubi to install Ubuntu 8.10 so in effect i had a triple boot system wherein the boot menu used to look like this:

      Windows Vista
      Windows XP
      Ubuntu


When i found out the latest Ubuntu ver 9.04 was available I used it as an opportunity to upgrade to the latest ver, as well as to install it to a real partition instead of wubi in windows, so i deleted the old wubi install.

Ran the Live CD and installed from there.

Install detected I had Vista and XP and informed me that it can install Ubuntu alongside them and offer me the choice at boot.. which was exactly what i was hoping for.

I installed successfully, GRUB is now showing me 

      3 ubuntu options

      Other OS:
      Windows Vista loader
      Windows NT/2000/XP
      Windows NT/2000/XP loader

Now i cant access either Vista or XP.

(Im also having problem with Ubuntu after a successful install and a few boot ups, but thats a matter for a different thread.. :-)

    
If I choose Windows Vista - loader, I get the original Windows Boot Manager
                   Windows Vista 
                   Windows XP

   When i click on Vista, I get "windows failed to start" error. File \Windows\System32\winload.exe is missing or corrupt.

   When I click on XP, I get  \NTLDR is missing or corrupt.
                    

If I choose Windows NT/2000/XP (from GRUB menu), I get "Invalid Boot.ini"

If I choose Windows NT/2000/XP Loader (from GRUB menu), I get  

           starting up...
           BootMgr is missing
           press any key to restart

           Reboot and select proper boot device
           GRUB loading stage1.5

           then freezes

So in a nutshell, all 3 options with suboptions 1.1 and 1.2 are invalid for me...

I tried to google for solutions but can't find an easy way to restore my Windows Vista/XP boot options. I'll probably remove Ubuntu install and just make a wubi install later when i get back my Windows boot options..  any ideas and suggestions would be greatly appreciated...


I went back to check on the boot choices in GRUB by pressing E..
here they are for reference:

      Windows Vista loader
            rootverify (hd0,0)
            savedefault
            makeactive
            chainloader +1


      Windows NT/2000/XP
            rootverify (hd0,1)
            savedefault
            makeactive
            chainloader +1


      Windows NT/2000/XP loader
            rootverify (hd1,0)
            savedefault
            makeactive
            chainloader +1
            map (hd0)(hd1)
            map (hd1)(hd0)
            chainloader +1


  I have 2  physical hard disks, so i guess thats hd0 and hd1.

  All the OS are in hd0, hd1 are just for data.

  Vista and Xp are on separate partitions on hd0 so afaik hd0,0 and hd0,1 are correct. i tried changing the values a bit but no luck, altho i didnt do all combinations. my Ubuntu install btw is on hd0,5. 

  I checked that the Vista drive and the XP drive still have their ntldr files in them (i remember that was the issue last time i had a problem with dual boot)

  I used GParted from the LiveCD and drives shown in my st hard disk are

             dev/sda1/Vista ntfs  boot  -- thats my C or Vista drive
                 sda2/XP    ntfs   --- thats my D or XP drive
                 sda3/extended    lba

  Im not sure why the last option  Windows NT/2000/XP loader, have hd1 values in it.. as i said, the hd1 drive  as i understand it only contains my data files.. (unless it detected some remnants of old OS or ntldr or something.. not sure)

  Thats all the info i think i can give now.. hopefully someone can pls help..  can i still recover my windows boot?  thanks a lot for reading....

---

### Post by presence1960 on 2009-06-10
Let's get a better picture of your setup by downloading the Boot Info Script to your Desktop from : [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

If you can't boot into Ubuntu, boot your Live CD & choose "try Ubuntu without any changes". When Desktop appears download the Boot Info Script to Desktop.

Open a terminal and run this command > sudo bash ~/Desktop/boot_info_script*.sh This will create a RESULTS.txt file on your Desktop. Paste the contents of that file back here. Highlight all pasted text and click # sign on toolbar to place code tags around text. This will provide all the info about your setup and boot info.

---

### Post by kyleryner on 2009-06-10
> **presence1960 said:**
> Let's get a better picture of your setup by downloading the Boot Info Script to your Desktop from : [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

If you can't boot into Ubuntu, boot your Live CD & choose "try Ubuntu without any changes". When Desktop appears download the Boot Info Script to Desktop.

Open a terminal and run this command  This will create a RESULTS.txt file on your Desktop. Paste the contents of that file back here. Highlight all pasted text and click # sign on toolbar to place code tags around text. This will provide all the info about your setup and boot info.

Presence1960,

Thanks so much for the reply and instructions...

Yes, i couldnt boot to Ubuntu (it did boot properly a few times until it hanged and now it wont boot.. seems to be a gfx problem, but thats another issue altogether)

I tried what you suggested (I copy-pasted it, then tried typing it too). I get the message

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory


I noticed there are several threads about folks having dual boot problems like me..seems like its not yet been "idiot-proof" ;)

Anyway, ive been researching nonstop since i had the problem (good thing i can still boot the Ubuntu livecd and access the net from there.. but CD-based OS is sllooow)

Finally stumbled on a tip...

I booted the Windows Vista Boot DVD, and used "Repair" function...  viola!! It fixed the windows vista boot.

My PC still boots the GRUB menu... I have to choose

Windows Vista loader (making the other 2 choices unnecessary it seems)

from there, a new choice emerged.. WINDOWS VISTA ULTIMATE (Recovered) and i can boot Vista.  From Vista, I used Vistabootpro to fix the Windows XP entry (changed the drive letter).  Rebooted, same choices, and chose Windows XP this time... 

Windows XP  BOOT screen shows up... then second boot/title screen... but it stop there.. wont go into the Desktop.

So it seems i have solved half of the problem.. can boot into Vista, but XP only boots partially and freezes... Still trying to see if there's a similar fix like the Vista Recover (I dont have the XP Boot disc) but i just might reinstall it from scratch.

If i do manage to get back my Vista and XP boot OS, its still nested inside the GRUB menu so i still need to figure out how to just put it back the way it was and just use wubi to install Ubuntu 9...

anyway, thanks again for the help and maybe you can give me some additional pointers on how to wipe away the GRUB menu... (and keep the Vista/XP boot loader options)

---

### Post by presence1960 on 2009-06-10
> tried what you suggested (I copy-pasted it, then tried typing it too). I get the message

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory


Did you download the Boot Info Script to the Desktop? If so then open a terminal and run that command. The response you got from the command seems to indicate the Boot Info Script is not on the desktop. If you downloaded it somewhere else copy/paste it to your desktop then run that command again

---

### Post by kyleryner on 2009-06-11
> **presence1960 said:**
> Did you download the Boot Info Script to the Desktop? If so then open a terminal and run that command. The response you got from the command seems to indicate the Boot Info Script is not on the desktop. If you downloaded it somewhere else copy/paste it to your desktop then run that command again


d'oh! I didnt dl the file (blush). A newbie at Linux, i assumed the command would run/dl the file... silly of me.  :-)

anyway, sorry it took me a day to reply, but in messing with the boot manager, i ended up deleting Ubuntu for now.. (I find the GRUB boot options unweildy.. had to go into 2 menu levels before booting into vista).

Restoring Vista boot was a cinch.
I got a "partial" restore XP boot as well but it either got corrupted or it wasnt restored properly, so i ended up reinstalling XP from scratch.

Im not giving up on Ubuntu.. im thinking now if i should just do a wubu install (like i did the 1st time) or if i should retry a linux install and hopefully have better results (I have to research more i guess, since i did a by-the-book install from the livecd..if i do it again the same way, wont i end up in the same bind?) Aside from the dual-boot issues, Ubuntu permanently  froze on me on bootup after running ok a for a few times.  

Anyway, thanks again for trying to help. will save your tip for future reference...

---

### Post by presence1960 on 2009-06-11
no problem. Food for thought: if you do an install to a partition instead of wubi- create a partition(s) for Ubuntu. When you get to the Prepare disk space window of the partitioner choose "manual" option instead of use entire disk or guided resize.

---

### Post by willie2008 on 2009-06-25
Hi,

This method works for me.  First double check where you download your file
I went directly to my Desktop drive and run the script.

sudo bash ./boot_info_script032.sh

Then I check the result file.  My entry is like this

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /BOOTMGR /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

I made this entry in my menu.lst file

title Windows Vista
root (hd0,1)
makeactive
chainloader +1

title Windows Vista Recovery
root (hd0,2)
makeactive
chainloader +1


I was able to get back my dual boot.  One thing though I used to have my recovery safe mode boot but I guess the second entry did not do the trick.

But thanks for the great tip.  I am happy camper.

---

### Post by presence1960 on 2009-06-25
change this 
```
title        Windows Vista Recovery
root         (hd0,2)
makeactive
chainloader  +1
```

to
```
title        Windows Vista Recovery
root         (hd0,0)
makeactive
chainloader  +1
```

sda1 is your recovery partition. Numbering for disks & partitions in GRUB starts at 0. So sda1 = (hd0,0), sda2 = (hd0,1), sdb1 = (hd1,0), sdb2 = (hd1,1), etc.

---

