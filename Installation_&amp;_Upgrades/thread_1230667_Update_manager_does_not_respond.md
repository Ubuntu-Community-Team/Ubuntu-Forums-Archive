---
title: "Update manager does not respond"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by patocardo on 2009-08-03
I click on update icon, then Update Manager opens and list all available packs as usual, but when I click on Update button, it does not respond any more. I am trying to update pack from yesterday

---

### Post by quixote on 2009-08-04
I think there may be a bug in that particular update.  I had the same problem yesterday.  It seems to be a problem with the GUI interface letting you be sudo.  I got around it by starting the program as sudo from the command line (Start > Accessories > Terminal):```
gksudo /usr/bin/update-manager
```
Hope that works for you too.

---

### Post by patocardo on 2009-08-05
Thank you, but nothing happend

---

### Post by snowpine on 2009-08-05
Try from the terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

Post any errors here...

---

### Post by patocardo on 2009-08-06
snowpine: It is already updated and upgraded, but unfortunately Update Manager still break down when I click a button (this time it was [Check]), and Synaptic does not even open

---

### Post by quixote on 2009-08-07
Really, try getting at it by command line.  The problem is that the GUI interface isn't working.  Sometimes that's the fault of "gksudo".  

Try the sudo commands snowpine suggested and see what the errors are.  You're just trying to see whether the commands run.  It doesn't matter whether there's any real updating / upgrading to do.

---

### Post by huggies15 on 2009-08-09
Ive just had a similar problem, with neither update manager nor synaptic loading. I ran
sudo apt-get update, and sudo apt-get upgrade, followed by the gksudo /usr/bin/update-manager and it all works fine now.
Thank you,
Steve

---

### Post by mobryan on 2009-08-09
new user. Try to update and get this message.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 
Help!

---

### Post by snowpine on 2009-08-09
> **mobryan said:**
> new user. Try to update and get this message.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 
Help!

The solution is in the error message. Open a terminal and:

```
sudo dpkg --configure -a
```

If you get any errors, cut and paste them here...

---

### Post by mobryan on 2009-08-10
How do I open a terminal? marlene

---

### Post by snowpine on 2009-08-10
> **mobryan said:**
> How do I open a terminal? marlene

Applications-Accessories-Terminal

---

### Post by mobryan on 2009-08-11
ok I did that and this is what I received below in the box. Now what do I do? M

owner@owner-desktop:~$ sudo dpkg --configure -a
[sudo] password for owner: 
owner@owner-desktop:~$ sudo
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
owner@owner-desktop:~$ 
owner@owner-desktop:~$

---

### Post by huggies15 on 2009-08-11
all you have to do now is type:
sudo apt-get update
sudo apt-get upgrade

should work

---

### Post by stephenfranklin on 2009-08-12
hey, i got that kind of problem.
when i type sudo dpkg --configure -a
i got this result any body help me...
```

Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-initrd-2.6.24.4-desktop-1mnb.img
Cannot find /lib/modules/initrd-2.6.24.4-desktop-1mnb.img
update-initramfs: failed for /boot/initrd.img-initrd-2.6.24.4-desktop-1mnb.img
dpkg: subprocess post-installation script returned error exit status 1
```

---

### Post by patocardo on 2009-10-13
I still have problems with opening Update Manager and Synaptic, I also discovered that I cannot open Software-Sources even from terminal. What should I do with the system?

---

### Post by quixote on 2009-10-13
Have these commands been failing for you?
```
sudo apt-get update
sudo apt-get upgrade
```

If so, you may want to backup your data to another partition or drive, note which extra programs you've installed, and then just do a clean install once Karmic Koala comes out.  It seems like a lot of bother, but sometimes with these iffy problems it's actually an easier solution than fighting with it.

---

