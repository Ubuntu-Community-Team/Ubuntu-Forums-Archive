---
title: "fsked up my partions... please help!"
date: 2005-11-11
forum: General Help
---

### Post by Trab on 2005-11-11
ok, wow, i totally messed everything up...
i was trying to redo my partions from partion magic on windows (i was gonn a move ubuntu to the bigger hard drive...) so i resized my windows partion.... and told it to fix my swap space on ubuntu (it got screwed up when i was doing something earlier)....
well, i think it crashed in the middle of partioning... booting into windows told me to reboot, or run some command.... i dunno, ill deal with that later...
booting in ubuntu takes me to the login screen, then complains because /home cant be found (its on a seperate partion...)... i think its the swap space issue....
i tried using the breezy install disk to overwrite the broken swap space, but instead of treating the harddrive as it has many partions, the only option is to overwrite the whole thing... obviously i dont want to do that...
i would like to repair my partions, so i can actually use my machine agian... running the Live-CD is very limiting...
thanks
-Trab

---

### Post by ssam on 2005-11-11
if you get to the login screen then i think that your swap is not the issue.

it is possible that the partition numbers have changed. for example if your home partition used to be hda2 and now its hda3 then linux wont be able to mount it.

from the live cd open gparted (applications -> system tools) and see if you can work out which partition your home drive is on. you should be able to get its address in the form /dev/hdxy where x is a letter, and y is a number.

now you need to mount your main ubuntu partition, and find the file
```
/etc/fstab
```
and change the device in the line that mounts /home/ to the /dev/hdxy you got.
save the file and all should eb well when you reboot.

sam

---

### Post by Trab on 2005-11-11
thanks, i think it moved /home from /dev/hdb7 to /dev/hdb8
im gonna try it again....
thanks mate....
by the way, the whole reason i had this issue, was i was trying to redo my partions, from Partion Magic in windows...
i wanted to move ubuntu (the file system and /home partions) to my larger 20 gig hd from the 10 gig hd. so i was trying to make room on the 10 gig to install windows on it... then i was gonna move /home to the bigger one, and recover everything from the old windows...
gparted wouldnt let me do ANYTHING with the partions... not even as root...
help?
thanks
-Trab

---

### Post by Trab on 2005-11-11
ubuntu works fine now, thanks a million mate!
i still have to fix windows, but w/e :-D

---

### Post by ssam on 2005-11-11
gparted can't do anything to a mounted disk (or atleast not a mounted partition). you can run it from a live cd though.

running
```
sudo update-grub
```
might get windows booting again.

---

