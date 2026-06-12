---
title: "Tried to install breezy"
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by jason.b.c on 2006-01-30
:confused: Anybody have an idea on how i could install ubuntu on a seperate hard drive in my computer?.  i tried to install and found out i did'nt have enough unpartitioned space (3.2mb's left) i really really don't want to try to install on this drive and take the chance of wiping out everything. What i was thinking was that if i put in another drive maybe labeled (B) or whatever. the only thing is is it possible to dual boot with two hdd's, one OS on one drive(c)windows 2k, and the other (ubuntu) on the second (b) drive.!!?   Is this even remotely possible or am i just loosing my mind?:KS

---

### Post by lha on 2006-01-30
[QUOTE=jason.b.c]:confused: Anybody have an idea on how i could install ubuntu on a seperate hard drive in my computer?.  i tried to install and found out i did'nt have enough unpartitioned space (3.2mb's left) i really really don't want to try to install on this drive and take the chance of wiping out everything. What i was thinking was that if i put in another drive maybe labeled (B) or whatever. the only thing is is it possible to dual boot with two hdd's, one OS on one drive(c)windows 2k, and the other (ubuntu) on the second (b) drive.!!?   Is this even remotely possible or am i just loosing my mind?:KS[/QUOTE]

In my opinion, the way you want to dual boot with is the easiest possible solution. 

Replace your current hard drive with an empty hd and put that old drive in another channel. (Eg. primary slave.) Then install Ubuntu on new drive. (Be careful not to select your Windows drive.) Usually installer can automatically set you dual booting. So when you are finished installing, you end up with a menu which lets you select wheter you want to boot Windows or Linux. No modifications are needed on Windows drive. If you have troubles, just plug out Ubuntu drive and put Windows drive where it used to be and you are back to plain Windows. (I told you that just in case... This method is as safe as installing a second os can be.)

---

### Post by jason.b.c on 2006-01-30
HHHMMM I guess i understand what mean,but wouldn't that cause other kinds of problems ,I mean switching back and forth between hd's isn't that going to start trouble with the systems bios?:o there's no other way to do it???

---

### Post by lha on 2006-01-30
[QUOTE=jason.b.c]HHHMMM I guess i understand what mean,but wouldn't that cause other kinds of problems ,I mean switching back and forth between hd's isn't that going to start trouble with the systems bios?:o there's no other way to do it???[/QUOTE]

You'll have to switch those drives _only_once_.  Grub (a boot loader) does the rest. This is the way I dual boot my computer and it works great. When you boot your computer, you'll see a menu where you can select between Ubuntu and Windows.

---

### Post by jason.b.c on 2006-01-30
You'll have to switch those drives _only_once_. Grub (a boot loader) does the rest. This is the way I dual boot my computer and it works great. When you boot your computer, you'll see a menu where you can select between Ubuntu and Windows.

----------------------------------------------------------------------------
Allright so lets see if i understand you correctly, i first remove my old hard drive and set it as slave and then install the new hd set primary in its place.then install ubuntu to the primary drive,and this grub boot loader will handle the rest,so then isn't that just what i wanted one os on each drive? does the that mean that the ubuntu drive HAS TO be set as the primary (master) drive?:cool:

---

### Post by lha on 2006-01-30
[QUOTE=jason.b.c]Allright so lets see if i understand you correctly, i first remove my old hard drive and set it as slave and then install the new hd set primary in its place.then install ubuntu to the primary drive,and this grub boot loader will handle the rest,so then isn't that just what i wanted one os on each drive? does the that mean that the ubuntu drive HAS TO be set as the primary (master) drive?:cool:[/QUOTE]

That's right. Both os'es will be on their own drives. Ubuntu drive could be somewhere else, but it would just cause you more work and you'd end up with things that may break.

Grub's your friend, it handles the dual-booting stuff. Sometimes installer doesn't set dual-booting right, but it is really easy to fix.

---

### Post by jason.b.c on 2006-01-30
ok well now i get it thank you very much! now if i can just figure out why my modem here in windows keeps on screwing up i'll be good to go    thats why i have'nt been able to type this stuff until now!:p

---

### Post by wrtrdood on 2006-01-30
It's not necessary to swap hardware.  The second drive should be identified by the partitioning tool as /dev/hdb.  Simply choose the partions to use on this particular device.  Install grub to the MBR of /dev/hda and you will be able to select either OS quite easily at boot.

---

### Post by lha on 2006-01-30
[QUOTE=wrtrdood]It's not necessary to swap hardware.  The second drive should be identified by the partitioning tool as /dev/hdb.  Simply choose the partions to use on this particular device.  Install grub to the MBR of /dev/hda and you will be able to select either OS quite easily at boot.[/QUOTE]
Doing that will make Windows depend on Ubuntu drive and Ubuntu will need Windows drive. It does work, but IMHO it is better to keep them separable so if other drive fails, the other will still provide a fully working system.

---

### Post by jason.b.c on 2006-01-30
:) yes exactly my idea thats why i asked the my first question to begin with (teehee) that way for one thing i wouldn't have to even touch the windows partition and even risk screwing it up or something else go wrong during the ubuntu install    :(   better safe than formatted  (right?)!!!!!!;)   besides that it just keeps everything seperate......holy cow what time is it:o

---

