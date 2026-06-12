---
title: "dual boot problem"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by pi149 on 2009-05-16
I have windows XP installed.  I installed Ubuntu 9.04 properly(I think).  I have no option to select Ubuntu at start up.  Can some one please help me?

---

### Post by pi149 on 2009-05-16
The GRUB menu thing does not even appear.

---

### Post by presence1960 on 2009-05-16
> **pi149 said:**
> I have windows XP installed.  I installed Ubuntu 9.04 properly(I think).  I have no option to select Ubuntu at start up.  Can some one please help me?

Did you partition your HDD to install Ubuntu or did you use wubi? If you have an Ubuntu partition boot from the Ubuntu Live CD & choose try Ubuntu without any changes to your computer. When the Desktop is loaded open firefox and come back here. Download this Boot Info Script to the Desktop from : [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Next open a terminal from Applications > Accessories > Terminal. Run in terminal ```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a RESULTS.txt file on your desktop. Copy and paste the contents of that file here. Put code tags around the text you paste here by highlighting the text and clicking the " # " from the toolbar.

This will show exactly how your system is set up.

---

### Post by pi149 on 2009-05-17
Thanks for the suggestion, but unfortunately I can not access the internet on the computer that I am trying to get Ubuntu on.

---

### Post by Game Over on 2009-05-17
I had dual boot problems once. After I backed up and wiped out Windows in one fell swoop, there were no more problems. I'm a happy camper now and I can safely say you would be too.

---

### Post by presence1960 on 2009-05-17
> **pi149 said:**
> Thanks for the suggestion, but unfortunately I can not access the internet on the computer that I am trying to get Ubuntu on.

Ok, try booting the Ubuntu Live CD & choose try Ubuntu without any changes to your computer. When the Desktop loads open a terminal: Applications > Accessories > Terminal. Run ```
sudo fdisk -l
``` and post the output here. BTW that is a lowercase L.

---

### Post by presence1960 on 2009-05-17
> **Game Over said:**
> I had dual boot problems once. After I backed up and wiped out Windows in one fell swoop, there were no more problems. I'm a happy camper now and I can safely say you would be too.

I know a lot of us don't particularly like Windows, but the OP didn't say he/she wanted to remove Windows. Currently we don't even know if the Ubuntu install succeeded. I recommend we get the partition info from fdisk first before we rush to judgment.

---

### Post by pi149 on 2009-05-17
All right, long text copying beginning.

---

### Post by pi149 on 2009-05-17
Disk /dev/sda: 160.0 GB, 160061885696 bytes
   255 heads, 63 sectors/track, 19457 cylinders
   Units = cylinders of 16065 * 512 = 8225280 bytes
   Disk identifier: 0x103d8ef0
   
      Device Boot             Start               End                    Blocks       Id    System
   /dev/sdal   *                            1       19457       156288321         7    HPFS/NTFS
  
  Disk /dev/sbd: 40.0 GB, 40020664320 bytes
  255 heads, 63 sectors/track, 4865 cylinders
  Units = cylinders of 16065 * 512 = 8225280 bytes
  Disk identifier: 0x05c0d225
 
  Device Boot            Start               End                  Blocks          Id    System
 /dev/sbd1   *                           1          2121     17036901           7     HPFS/NTFS
 /dev/sbd2           2122          4865         22041180           5     Extended
 /dev/sbd5                         2122          4745         21077248+  83     Linux
/dev/sbd6                         4746          4865        963868+     82     Linux swap / Solaris

sorry about formating

---

### Post by presence1960 on 2009-05-17
> **pi149 said:**
> Disk /dev/sda: 160.0 GB, 160061885696 bytes
   255 heads, 63 sectors/track, 19457 cylinders
   Units = cylinders of 16065 * 512 = 8225280 bytes
   Disk identifier: 0x103d8ef0
   
      Device Boot        Start        End          Blocks    Id  System
   /dev/sdal   *                1    19457   156288321      7  HPFS/NTFS
  
  Disk /dev/sbd: 40.0 GB, 40020664320 bytes
  255 heads, 63 sectors/track, 4865 cylinders
  Units = cylinders of 16065 * 512 = 8225280 bytes
  Disk identifier: 0x05c0d225
 
    Device Boot        Start        End          Blocks     Id  System
 /dev/sbd1   *               1      2121     17036901      7   HPFS/NTFS
 /dev/sbd2               2122      4865     22041180      5   Extended
 /dev/sbd5               2122      4745     21077248+  83   Linux
/dev/sbd6               4746      4865        963868+   82   Linux swap / Solaris

Looks OK. Try hitting ESC when you get the GRUB loading message. That should bring up the menu. Then you can choose Ubuntu. Once in Ubuntu open a terminal and install startupmanager by running in terminal ```
sudo apt-get install startupmanager
``` This is a GUI for editing your startup options. You can also install it through Synaptic Package manager- System > Administration > Synaptic Package Manager.
Let's see if that works. If not I see you have Windows installed to sda1 and sdb1. Which one is your Windows that you are using?

---

### Post by pi149 on 2009-05-17
I do not get the grub loading message.

---

### Post by presence1960 on 2009-05-17
> **pi149 said:**
> I do not get the grub loading message.

Ok I take it it goes straight to windows then correct? If so you will have to restore GRUB, follow this :
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD
```

try this and lets see what happens.

---

### Post by presence1960 on 2009-05-17
if your windows is on the same hard disk as Ubuntu you will have to make that disk first in boot order in BIOS. Just a thought there because I saw you have Windows installed to both hard disks. Reinstalling GRUB won't hurt anything. It's a shame you cant access the net to get that script. I was going to attach it but it exceeds the upload size limit for that filetype.

---

### Post by pi149 on 2009-05-17
At step 5 I get message "Error 15: File not found"

---

### Post by presence1960 on 2009-05-17
> **pi149 said:**
> At step 5 I get message "Error 15: File not found"

it looks like your install may have fouled up. Did you run check disk  for integrity when the options came up when you booted the Live CD? You may have a bad burn. I would burn another using a CD-R at the slowest speed you are able to select. Then try reinstalling. Also which hard disk is windows installed to? If it is the same disk as where you tried to install Ubuntu make sure you go into BIOS and set that hard disk as first in the hard drive boot order. If this is the case your boot order should be CD/DVD drive - disk with Ubuntu & Windows (sdb)- other disk (sda)

---

### Post by pi149 on 2009-05-17
> **presence1960 said:**
> Did you run check disk  for integrity when the options came up when you booted the Live CD?

Yes I did check the disk, it said it was fine.
I guess Ill try re burning then.

---

### Post by presence1960 on 2009-05-17
> **pi149 said:**
> Yes I did check the disk, it said it was fine.
I guess Ill try re burning then.
 Going to bed, but let us know how it goes. We want your Ubuntu up and running! ):P

---

### Post by pi149 on 2009-05-17
Ok, I burned an new disk at slowest possible speed, installed ubuntu, and it did not help at all.

---

### Post by pi149 on 2009-05-17
Again, the disc check thing said that the disk was fine.

---

### Post by Tomatosoup on 2009-05-17
I have the same problem:
[http://ubuntuforums.org/showthread.php?t=1162083](http://ubuntuforums.org/showthread.php?t=1162083)

---

### Post by pi149 on 2009-05-17
Hurray! I managed to get it to work:D  It worked for about 3.5 minutes.
NOW, I can not do anything because when ever I click on anything it turns pitch black, and within 5 seconds the entire screen is pitch black and I have to restart my computer to get out:mad:
It is not supposed to do that, right?

---

### Post by Tomatosoup on 2009-05-17
What did you do then? :o

Never mind, read it in my topic.
But still no solution.

It isn't suppose to do that no. :P
Hope it'll work for you.

---

