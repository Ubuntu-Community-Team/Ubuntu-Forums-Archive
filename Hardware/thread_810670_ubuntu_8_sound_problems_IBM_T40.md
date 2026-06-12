---
title: "ubuntu 8 sound problems IBM T40"
date: 2008-05-28
forum: Hardware
---

### Post by Flamedrix_14 on 2008-05-28
I have installed ubuntuhttp://ubuntuforums.org/register.php?do=addmember 8.04 on my ibm thinkpad t40 can anyone help me with finding and installing the sound drivers for ubuntu?
I am new to ubuntu and have limited knowledge of the operating system and need step by step details. Thanks for your help.

---

### Post by Kinnza on 2008-05-28
are you sure the sound driver doesnt work or maybe you are just muted?
try running: alsamixer from command and see if the right bars are not muted....

---

### Post by Flamedrix_14 on 2008-05-28
> **Kinnza said:**
> are you sure the sound driver doesnt work or maybe you are just muted?
try running: alsamixer from command and see if the right bars are not muted....

ok but how do i do that? Like I said I have very little knowledge of how to run this operating system.

---

### Post by xfceuser on 2008-05-28
sound driver must normally has been automatically installed.
type in a terminal 
gnome-alsamixer
and see if it shows the control of your sound card.

---

### Post by Flamedrix_14 on 2008-05-28
> **xfceuser said:**
> sound driver must normally has been automatically installed.
type in a terminal 
gnome-alsamixer
and see if it shows the control of your sound card.

i did and it just came up in a new window with nothing on the screen.
what does that mean?

---

### Post by xfceuser on 2008-05-28
thats unfortunately means your sound driver is not functioning.
try this command and see the output: 
sudo /etc/init.d/alsa-utils restart

---

### Post by Flamedrix_14 on 2008-05-28
> **xfceuser said:**
> thats unfortunately means your sound driver is not functioning.
try this command and see the output: 
sudo /etc/init.d/alsa-utils restart

it said "Command not found"

---

### Post by xfceuser on 2008-05-28
try 
sudo /etc/init.d/alsa-utils reset

---

### Post by Flamedrix_14 on 2008-05-28
> **xfceuser said:**
> try 
sudo /etc/init.d/alsa-utils reset

it said [ok] reseting alsa

---

### Post by xfceuser on 2008-05-28
also do:
sudo apt-get install alsa-utils

then try again these commands:

sudo /etc/init.d/alsa-utils restart

and 

gnome-alsamixer

---

### Post by Flamedrix_14 on 2008-05-28
it says that alsa-utils is already the newest version and 0 to remove and 17 not upgraded

---

### Post by Flamedrix_14 on 2008-05-28
by the way thanks for helping me out with this

---

### Post by xfceuser on 2008-05-28
then try again these commands:

sudo /etc/init.d/alsa-utils restart

and

gnome-alsamixer

---

### Post by Flamedrix_14 on 2008-05-28
it says it failed that there were no sound cards found.

---

### Post by xfceuser on 2008-05-28
try somewhere in administrative menu or system menu about sound, and see if it is enabled ...

---

