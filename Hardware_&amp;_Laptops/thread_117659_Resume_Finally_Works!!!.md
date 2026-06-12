---
title: "Resume Finally Works!!!"
date: 2006-01-15
forum: Hardware &amp; Laptops
---

### Post by Luke on 2006-01-15
acpi seemed to almost work out of the box on my presario m2000. but the problem was  that although it would always go to sleep, it would only wake up sometimes. other times it would start to resume but i would be left with a blank screen and would have to reboot. but i think i finally found my solution.

originally i had the following as a boot parameter
```
acpi_sleep=s3_bios
```
i went into "/boot/grub/menu.lst", found the line that starts with "#kopt" and changed the above to  
```
acpi_sleep=s3_mode
```
then ran
```
sudo update-grub
```
and so far it has woken up properly every time (about 10 times so far). just figured i'd share in case it helps someone else who's having a similar problem.

---

### Post by elcu on 2006-01-27
I've got an M2217AP (but it has M2000 on the screen so I assume mine is of the same family to yours).

Sleep/Standby did not work out of the box for me.  At least, when I closed the lid, it would just lock screen, not go into powersaving mode.

Can you post your full kopt line?

Because I have this currently:

```
# kopt=root=/dev/hda2 ro
```

---

### Post by jecos on 2006-01-28
well /etc/default/acpi-support has to be modified in order to suspend and not just lock the system. (it says it in the comments what to change. set to "mem" ..etc)

To ThreadStarter: What video card is in your laptop, i have a compaq presario 2108us (radeon igp320m) and it can't resume.  I might not of tried that specific kernel boot option..

---

### Post by Botond on 2006-01-28
[QUOTE=jecos]To ThreadStarter: What video card is in your laptop, i have a compaq presario 2108us (radeon igp320m) and it can't resume. [/QUOTE]

You may experiment with this fix: [https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/6454](https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/6454)

---

### Post by Skye on 2006-01-28
This howto may also be helpful:
[http://www.ubuntuforums.org/showthread.php?t=75443](http://www.ubuntuforums.org/showthread.php?t=75443)

It made suspend/resume and sleep work perfectly for me, which is impressive considering I'm using ATi's fglrx drivers, which are known to have problems with suspending and resume.

---

### Post by Luke on 2006-02-10
sorry i didn't respond sooner. i haven't been using ubuntu for a little while and haven't been on the forums. i decided to try out kanotix which seems pretty good but i don't yet have the suspend working the same way i did in ubuntu. unfortunately i did not back up my menu.lst file so i don't have the old #kopt line to post.

it's true that my original post is not the whole story on how i got suspend working. it only described how i fixed the "not waking up" problem. i believe i got suspend to start working by using the laptop battery section in kde's kcontrol.

my video card is radeon xpress 200 and i have always been using the "vesa" driver. 

if i get things working properly in kanotix, i'll post up my #kopt line in case it can be of any use.

---

