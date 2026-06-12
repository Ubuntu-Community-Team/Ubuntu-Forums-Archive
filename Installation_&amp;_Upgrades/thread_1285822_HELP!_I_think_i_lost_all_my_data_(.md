---
title: "HELP! I think i lost all my data :("
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by RobertHamilton on 2009-10-08
Okay, i have two HDD's both 640gb both had windows 7 on them but i formatted one of them (the one i no longer used). I just downloaded the new ubuntu (Jaunty Jackelope) today and wanted to install that on my 2nd HDD. So I did that and i choose to install it on the HDD that windows wasn't on. After the install i checked to see my windows HDD but it's labelled as New Volume and inside it is just a folder called "System Volume Information". I don't know what i've done wrong but i'm starting to panic because i think i've wiped my windows drive :( Also when i go into gparted and select the HDD that ubuntu isn't installed on it (sda), it says next to the New Volume Partition Size = 596 GiB and Used= 104.57 MiB but when i right-click that and go to Information it says Used= 0% and i know i had used more than 100mb on it. i had like 300Gb of valuable data! 

Plus, i can't boot into Windows either on the Grub loader it is listed but when i boot into it it tells me to windows repair and i've tried repairing it automatically and done bootsect /fixmbr and /fixboot but it still wont boot and now i can't even boot into Ubuntu cuz the windows bootloader has overwritten the GRUB loader...
 What do :confused:

---

### Post by Mark Phelps on 2009-10-08
Which is why I always recommend that when folks have two hard drives, and they want a different OS on each (Windows on one, Ubuntu on the other), they disconnect the Windows drive before attempting installation ...

You're best bet at this point is to boot from an Ubuntu LiveCD, go into Places, open the folders there for your MS Window partition, and see if there's anything there.

I've heard that you can then use Testdisk to recover your Windows files -- but I've never had any success doing that.  I suggest you do a search in the forums for "data recovery" and look for threads where folks have used Testdisk on MS Windows partitions.

An alternative is to use an MS Windows-based data recovery product (which I always do with MS Windows partitions), but those cost money.

---

### Post by RobertHamilton on 2009-10-08
> **Mark Phelps said:**
> 

I've heard that you can then use Testdisk to recover your Windows files -- but I've never had any success doing that.  I suggest you do a search in the forums for "data recovery" and look for threads where folks have used Testdisk on MS Windows partitions.

I've searched for testdisk and recovery in the forums and found this guide [http://ubuntuforums.org/showthread.php?t=387922](http://ubuntuforums.org/showthread.php?t=387922) but it doesn't seem to do me any good.. all it's doing is recovering the files that i can already access by opening the drive from Places-> Computer. Is there a way I can do a thorough search or repair or something like that to find broken data (the data i had on my windows 7 partition). Thanks heaps

---

### Post by catonic on 2009-10-08
This may help: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) to fix your mbr but then again the windows install should show up in grub's boot options. Anyway, it's always a good idea to install windows on 2 partitions so that if the os falls over (as it is prone to do) then a re-install does not wipe out all your data, which is put on the second partition. 
All the best, catonic.

---

### Post by RobertHamilton on 2009-10-08
Argh i tried PhotoRec too. It discovered my windows folders: "Music, Pictures, Documents etc." and recovered them but they're Empty!! Is this all I can do? Should i give up now :cry:

---

### Post by RobertHamilton on 2009-10-08
> **catonic said:**
> This may help: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) to fix your mbr but then again the windows install should show up in grub's boot options. Anyway, it's always a good idea to install windows on 2 partitions so that if the os falls over (as it is prone to do) then a re-install does not wipe out all your data, which is put on the second partition. 
All the best, catonic.

Thanks but it's not what i'm looking for now. I have fixed mbr i believe but i cannot boot into windows because the data on that HDD is probably completely ruined.
I get this info after a Windows 7 Repair:
"Boot configuration is corrupt.
repair action: partition table repair.
Result: Failed Error code = 0x490"

---

### Post by RobertHamilton on 2009-10-08
Okay well I am going to bed now but if anyone else knows any other method that I could possibly recover my data with please leave a post here and I will read it in the morning. Remember that I've tried TestDisk and PhotoRec to no avail, and that is all I've tried. Thankyou!

---

