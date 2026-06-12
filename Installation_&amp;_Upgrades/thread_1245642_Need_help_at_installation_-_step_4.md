---
title: "Need help at installation - step 4"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by dillonrabbit on 2009-08-20
Hi all, 
 
I am a new linux user and only recently installed ubuntu 9.04 on my laptop (Sony Vaio VGN-NR38M). It worked fine for a few days but then it said that there was an "unclean shutdown" and that i should try to run FSCK manually. I did this by following advice on other forums. When FSCK was running it said it found "errors" - it gave me the option to ignore (y) and to Force Overwrite (y). I agreed yes to both. 
 
now when i turn it on i get "error 17" and nothing else.
 
I've tried to re-install ubuntu but i can only get as far as step 4 "Prepare Partitions" - it is blank, there are no drives visible and nothing for me to select. 
 
The buttons at the bottom - "new partition table" "new partition" "edit partition" "delete partition" are greyed out. 
 
 
Does any know how i can fix this? 
 
I considered taking the drive out of my laptop and reformatting it, would this help or is it more likely that there is a hardware issue with the drive itself?
 
Thank you for taking the time to read this, i'm sorry if i'm not very specific with my description of the problem.
 
Regards,
 
DR

---

### Post by wojox on 2009-08-20
Boot of the LiveCD.
Open a terminal:

```
sudo grub
```

Then
root (hd0,0)

setup (hd0)

exit

Reboot (removing the livecd), and your boot menu should be back.

---

### Post by mick222 on 2009-08-20
should last command not be quit

---

### Post by Pumalite on 2009-08-20
Right

---

### Post by dillonrabbit on 2009-08-20
Thank you all for your quick replies,
 
When i type "root (hd0,0)" i get the following error message
 
Error 21: Selected disc does not exist
 
Any help with this would be greatly appreciated, i am currently trying to find a solution online myself. 
 
Thank you

---

### Post by wojox on 2009-08-20
Boot of the LiveCD again and open System > Admin > Partition Editor
Wipe out the partitions and start over.

---

### Post by dillonrabbit on 2009-08-20
Thank you for the help again:) 
 
I've tried going to partition editor - it scans for devices then gives the message "No devices detected" ?
 
I also tried "find /boot/grub/stage1" and this gave me error 15: file not found
 
Any advice would be greatly appreciated, i'd be happy to try a different linux OS if this would solve the problem?

---

### Post by raymondh on 2009-08-20
Hope [this site]("http://members.iinet.net.au/~herman546/p15.html#17") and this [thread]("http://ubuntuforums.org/showthread.php?t=442945") can help you diagnose/correct error 17.

---

