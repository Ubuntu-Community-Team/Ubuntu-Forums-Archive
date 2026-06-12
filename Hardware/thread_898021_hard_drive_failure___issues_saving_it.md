---
title: "hard drive failure   issues saving it"
date: 2008-08-22
forum: Hardware
---

### Post by pr1mal on 2008-08-22
Ok so i bought this seagate 7200.11 HDD and put all my important things on it and then it failed 10 days later.  It doesnt get detected by bios all the time and it can not be mounted.  It has XP in it.  So i hooked it up to my ubuntu (7.10) system and tried to run 
ddrescue -n
 on it,  the destination drive was a external maxtor 500 gig drive(had to buy that cause i had no other 500 gig drive to copy everything over on).  It ran for about 7 hours.

so now in ubuntu i try and mount the old drive and i get
ntfs_attr_pread:ntfs pread failed:in/out error failed to read $mftmirr.......failed to mount your NTFS is either inconsistent or you have hardware faults.....

and now i try to mount new(external copy) drive and i get 
$mft had invalid magic:failed to load $MFT..........NTFS is either inconsistent.....



So thats my problem i can mount either the failing drive or the "good" copy "ddrescue" made

any ideas on how i can mount either of these or how to save my dying HDD??  please... :(

---

### Post by CTRLurself on 2008-08-22
reformat the maxtor, install it internally into the computer.

Then, two choices:

A) install windows on it, find some free/cheap file recovery software for windows on ZDnet.com in their download section. Install that, plug in the Seagate in an enclosure externally. Keep re-plugging until it recognizes in windows. 

B) load Ubuntu onto it. Put the Seagate into an external enclosure, boot Ubuntu and keep re-plugging the Seagate til it recognizes in ubuntu as external media. 

then just copy any files you can, if no file are visible, run the file recovery software on it, and see what you can save. You don't want to copy everything from the Seagate because then you are very likely to also copy the problem (just like you did)... this is why i prefer windows - there is a lot of software available that allows you to pull just select files off of a bad drive without attempting to copy the whole thing.

Hope this helps.

---

### Post by pr1mal on 2008-08-24
even when the bios recognizes the device windows does not see it.  Ubuntu will see the phyical drive (and sometimes the partition)  but can never be mounted so i cant just use a GUI to copy over files.   
Is there a "dd" or "ddrescue" command that follows paths    
ie:  "ddrescue -n /dev/sdg1/DocumentAndSettings/User /dev/sda  logfile"

cause i dont need the whole drive.  Its really just 4 video files that are on there that i dont have backed up and are quite priceless to me.

thanks for the help.


O and i ran chkdsk on the original failed drive today and it sticks on 25% of the 5th test or something :(

---

### Post by pr1mal on 2008-08-25
I did the freezing the HDD trick and now windows and ubuntu can recognize it.  but neither OSes can access it, only programs meant to work with corrupted failing HDDs.  So does any one know any good linux or windows recovers that will work quick and only the directories i specify.  
I bought a windows  one (getdatabackNTFS) but it sucked and i ddrescue doesnt seem to be working because it can only do that whole logical drive (that i know of) and my drive gives up on life after about 10 minutes.

Thanks Thanks Thanks...

---

### Post by pr1mal on 2008-08-25
up....   need help

---

