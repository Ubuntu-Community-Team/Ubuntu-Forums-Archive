---
title: "HP Paviliion DV7 1245dx"
date: 2011-03-14
forum: Hardware
---

### Post by bigougit on 2011-03-14
The headphone jacks aren't working. I'm using Ubuntu 10.10 and I used Wibu to install it (dual boot with win7)

I've searched everywhere and can't find how to fix this, thanks in advance.

---

### Post by David D. on 2011-03-14
I had this problem, it turned out the laptop was not sensing that something (headphone) was plugged into the jack.  The fix I found is to edit the alsa-base.conf file.

Open a terminal and enter the below to open the file for editing

```
gksudo gedit/etc/modprobe.d/alsa-base.conf
```

Insert this line at the bottom of the file

```
Options snd-hda-intel model=hp-dv7 enable_msi=1
```

Save the changes to the file, close the terminal and reboot.

---

### Post by bigougit on 2011-03-14
when i enter gksudo gedit/etc/modprobe.d/alsa-base.conf
nothing happens

---

### Post by p110011 on 2011-03-14
How about ```
alsamixer
``` f6 to select card and arrow to enable jack?

---

### Post by David D. on 2011-03-14
Sorry, I had a type.  There should be a space after the "gedit".  Try this code:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by bigougit on 2011-03-14
Thanks David D. It works now :)

now if only i could figure out installing java x.x I forgot how complicated stuff can be with linux lol

---

### Post by Yellow Pasque on 2011-03-14
sun java is in the canonical partner repo: [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories)

---

