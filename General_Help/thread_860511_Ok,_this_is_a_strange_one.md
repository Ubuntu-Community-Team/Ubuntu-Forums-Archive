---
title: "Ok, this is a strange one"
date: 2008-07-15
forum: General Help
---

### Post by mikeymo1741 on 2008-07-15
I have an Acer Aspire 3001 that is dual-booted to Ubuntu Hardy and XP Home.  I've never had a problem with it, both work fine.  I use Xp more than Ubuntu, but boot to both regularly. 

Last night when I booted to Ubuntu, I noticed right away something was amiss.  First off, there was nothing on my desktop.  Second, it did not connect to my wireless.  In fact, I cannot get it to connect or even show the networks, though in the setup screens they are all there and correctly configured.  

When I go to Places, all the proper folders are listed, but when I select one, I get the wait icon for a bit, then nothing.  Programs seem to work OK.  

Is there a built in repair or restore utility?

---

### Post by tamoneya on 2008-07-15
in terminal run:```
sudo dpkg-reconfigure ubuntu-desktop
```
Then restart gdm with ```
sudo /etc/init.d/gdm restart
```

---

### Post by mikeymo1741 on 2008-07-17
Unfortuneatly, that did nothing.   The gdm resarted then hung up.  When I rebooted, all was as broken as before.

---

### Post by Archimedes0212 on 2008-07-17
have you tried going back to one of the 'recovery' images that you can select in the grub menu?  Does it have the same problem there?

---

### Post by tamoneya on 2008-07-17
> **mikeymo1741 said:**
> Unfortuneatly, that did nothing.   The gdm resarted then hung up.  When I rebooted, all was as broken as before.

Did you get any errors when you did the gdm restart or did it just hang from the start?

---

### Post by Mgiacchetti on 2008-07-17
this is why i always do a complete restart after EVERY update, just to make sure ubuntu still works.

---

### Post by Ataris on 2008-07-17
This is a question I've always had: Is there a way to reinstall ubuntu without formatting the partition or harddrive?

That would solve the problem, no?

---

### Post by tamoneya on 2008-07-17
> **Ataris said:**
> This is a question I've always had: Is there a way to reinstall ubuntu without formatting the partition or harddrive?

That would solve the problem, no?

just use the manual partitioner and you should be fine.  Make a backup though just in case.

---

### Post by mikeymo1741 on 2008-07-17
> **tamoneya said:**
> Did you get any errors when you did the gdm restart or did it just hang from the start?

Nope, it just hang.   

I will try the recovery image; I didn't try that.

---

### Post by nanog on 2008-07-17
Try logging into tty1 shell by issuing ctrl alt F1 (and pressing any key).


Stop GDM:

sudo /etc/init.d/gdm stop

Update - and attempt to fix a broken desktop metapackage:

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install ubuntu-desktop

Start GDM

sudo /etc/init.d/gdm start

post any errors that come up.

If the above does not work.

Try:

sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

If this does not work then you can try 
sudo apt-get remove --purge ubuntu-desktop 
sudo apt-get install ubuntu-desktop

This may remove config files and cause other breakage so a full /home/directopry backup is a good idea.

---

