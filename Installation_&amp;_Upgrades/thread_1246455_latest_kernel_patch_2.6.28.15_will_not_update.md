---
title: "latest kernel patch 2.6.28.15 will not update"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by graham45 on 2009-08-21
Hi  I have run update manager and was presented with kernel patch/s 2.6.28.15 etc and asked to install them.  The system seemed to be working normally and I did not notice and errors, but after when I checked in /boot there are no new kernel files so obviously it has failed to update for some reason.  I have looked for update logs but cant find them - they must be somewhere in /var I would have thought. Anyway when I run update manager now it tells me I am up to date !!  That is after clicking the 'check' button by the way !  I am running 9.04 and always keep my patching up to date !!  Just this 1 problem with the latest kernel update. Can anybody suggest a way to resolve this please ?  Thanks.

---

### Post by wojox on 2009-08-21
Look in /usr/src/ :P

---

### Post by graham45 on 2009-08-22
Thanks for that info - indeed it all seems to be there - just not sure what to do with it now.....what action to take to get it loaded in /boot- this was part of a standard patch install - i was not trying to build a kernel !
Thanks for the information anyway

---

### Post by emeraldgirl08 on 2009-08-22
Someone passed this to me:

```
sudo update-grub
```

I basically had the same problem as you. I did not see the new kernel on my Grub boot. I just did the code and am going to restart.

We'll see :)

EDIT: 

Didn't work.

---

### Post by graham45 on 2009-08-23
Thanks for that suggestion - it would probably work if new kernel was in /boot/ but it isnt on my system and not on yours either it seems - thats the problem ! It seems update-manager does not log details of errors otherwise one could track the problem down, nice to know about the 'update-grub' command anyway. Of course before rebooting you can always ' cat /boot/grub/menu.lst | more' to check the nre kernel is added to the grub boot config.  It wont be there if it isnt in the /boot directory !!

---

