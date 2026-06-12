---
title: "Is there an alternative method to update???"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by mabtifro2 on 2009-01-26
For those of us without access to fast, stable connections, it is nearly impossible to update to 8.10 all in one shot. The update manager estimates my download time to be apprx. 14 hrs. The problem is I live in a country where the power goes out every few hours, sometimes on a schedule, and sometimes quite randomly. I was at 60% this morning before the electricity failed and wiped out the progress I had made. I've downloaded the full 8.10 iso and made a live sd disk... but there is no way to update from a live disk/usb/sd.. is there???

---

### Post by bgerlich on 2009-01-26
I see somebody didn't read the wiki :)

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)

---

### Post by mabtifro2 on 2009-01-26
gracias

so im trying to follow the instructions which go as follows:

-------------

Download the alternate installation CD 

Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded. 

If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like: 
sudo mount -o loop ~/Desktop/ubuntu-8.10-alternate-i386.iso /media/cdrom0
A dialog will be displayed offering you the opportunity to upgrade using that CD. 
Follow the on-screen instructions. 

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2: 
gksu "sh /cdrom/cdromupgrade"

-------------

i tried runing "sh /cdrom/cdromupgrade" like it instructed but nothing pops up. do i need to tweak the command since im using an sd card?

---

### Post by bgerlich on 2009-01-26
If you have properly mounted the iso, then no :).

---

### Post by mabtifro2 on 2009-01-26
i used unetbootin to mount it. it works fine when i start up, press esc, and choose to boot live from sd.. is there a way to test if it's been properly mounted or not

---

### Post by bgerlich on 2009-01-26
You don't have to do that. Just copy the ISO on sd card, start your Ubuntu, start the terminal, cd into your sd card directory in /media, type: ```
sudo mount -o loop ubuntu-8.10-alternate-i386.iso /media/cdrom0
```

If no errors pop up you are good to go.

---

### Post by mabtifro2 on 2009-01-26
hmmm..  still not working, it looks like it mounts properly because all the files appear in the media/cdrom0 directory and there is also the icon on my desktop that appears. and when i run the gksu command, it asks me for my pw, but does nothing more... any more thoughts??

---

### Post by bgerlich on 2009-01-26
Try running "sudo ./cdrom/cdromupgrade" in the terminal to see what the problem is. Post the output.

---

### Post by mabtifro2 on 2009-01-26
command not found

---

### Post by bgerlich on 2009-01-26
cd into the /cdrom and /media/cdrom0 foldres, type ls in both, post output.

---

### Post by mabtifro2 on 2009-01-26
i cd'd into both directories and got the same output; 'command not found'

---

### Post by bgerlich on 2009-01-26
what I meant is you should check using "ls" in which dir the file resides and then do "sudo ./cdromupgrade

---

### Post by mabtifro2 on 2009-01-26
marc@marc-laptop:/cdrom$ ls
autorun.inf  dists    isolinux    pics  preseed             ubuntu     wubi.exe
casper       install  md5sum.txt  pool  README.diskdefines  umenu.exe

marc@marc-laptop:/media/cdrom0$ ls
autorun.inf  dists    isolinux    pics  preseed             ubuntu     wubi.exe
casper       install  md5sum.txt  pool  README.diskdefines  umenu.exe

---

### Post by mabtifro2 on 2009-01-26
o.. apparently there is a separate iso for upgrading.. wtf is the purpose of that?? anyways at least i got the answer.

merci beaucoup pour votre aide.

what ever happened to the thank you buttons??

---

### Post by snova on 2009-01-26
> **mabizeid said:**
> what ever happened to the thank you buttons??

Temporarily disabled. See: [http://ubuntuforums.org/showthread.php?t=1039481](http://ubuntuforums.org/showthread.php?t=1039481)

---

