---
title: "Quite a lot of problems..."
date: 2008-11-17
forum: General Help
---

### Post by Turiko on 2008-11-17
I recently installed ubuntu to be in a dualboot, alogn with windows xp pro (i'm a gamer; no ubuntu-only). When i installed, i knew there would a be a few small problems (like having trouble getting wlan up and running) but i got way more then i expected.

I'll just list the problems in range of how important i think they are:

1) Wlan. I simply NEED this. i can't fix anything if i have to keep switching back and forth between xp and ubuntu!

I have an atheros pci-e card. i got the madwifi drivers, "made" them (command make in main directory, as in install guide puti n with the archive), and then nothign happened. The same usual just was displayed: wlan card found, found working, but not even a single wireless network found.

2) GRUB. I don't want ubuntu booting up every time i boot my pc and then not pay attention to the screen. It's supposed to be easy to change it, with the .ink file and all. I found the settings, but ended up not being able to save... i tried making an account privileged with admin, to edit the file and then delete the user. It didn't work out as i planned - still i couldn't save the file. i tried changing the account to root, wich brings me to my third problem

3) the account screen. everythign is grey, as usual before unlocking. Then i click unlock, ubuntu spends about a minute or so doing nothing, and then i get a nice error sayign "an error occured". Not specific, so i'm afraid i have no clue what ever happened to it.


I've tried finding solutions to my wlan and grub, but both needed an internet connection. a guide to set up your internet is useless if you need to connect to the internet before it is solved. For the accoutn screen i haven't looked, because i just know a to nof unrelated results will be shown. "error" isn't exactly specific.

---

### Post by Marius Derekus on 2008-11-17
If you are wanting windows to be the OS to automatically boot up, then download easyBCD on windows. It allows you to choose which OS you want to be your default.

---

### Post by Marius Derekus on 2008-11-17
Try right clicking the the little icon that looks like two little monitors on the right hand corner of your screen. There should be an option that say "Enable Wireless". Make sure that option is checked.

---

### Post by Turiko on 2008-11-17
yes, on windows... xp. easyBCD is for tweakign the vista loader, whislt i'm using grub that was installed with ubuntu.

---

### Post by Marius Derekus on 2008-11-17
Your right. I forgot, yours is not the smae as mine, sorry. (I have a wubi install)

---

### Post by Turiko on 2008-11-17
> **Marius Derekus said:**
> Try right clicking the the little icon that looks like two little monitors on the right hand corner of your screen. There should be an option that say "Enable Wireless". Make sure that option is checked.

it is checked. i can even acces the options for wireless connections. but no connections are ever found.

---

### Post by Marius Derekus on 2008-11-17
I'll keep thinking then. (I sympathize you greatly, i had to boot back and forth just like you for a long time.)

---

### Post by lavinog on 2008-11-17
To configure grub, you can use startupmanager
install it with synaptic or 
```
sudo apt-get install startupmanager
```
it is a gui for configuring your startup.

for your wireless, have you enabled the restricted drivers...i think you have to go to Adminstration>Hardware Drivers.

I am not sure about the unlock issue. Does this happen everytime you turn on your computer?

---

### Post by Marius Derekus on 2008-11-17
I've told this to many people, but maybe it'll still help (this is about your grub problem) but try typing```
gksudo nautilus
``` in terminal, it'll give you a separate window with super administrator permissions. Then edit the file through that window

---

### Post by Marius Derekus on 2008-11-17
I've told this to many people, but maybe it'll still help (this is about your grub problem) but try typing ```
gksudo nautilus
``` in terminal, it'll give you a separate window with super administrator permissions. Then edit the file through that window

---

### Post by Turiko on 2008-11-17
> **lavinog said:**
> To configure grub, you can use startupmanager
install it with synaptic or 
```
sudo apt-get install startupmanager
```
it is a gui for configuring your startup.

for your wireless, have you enabled the restricted drivers...i think you have to go to Adminstration>Hardware Drivers.

I am not sure about the unlock issue. Does this happen everytime you turn on your computer?

read my problem number 1: no internet.

> **Marius Derekus said:**
> I've told this to many people, but maybe it'll still help (this is about your grub problem) but try typing ```
gksudo nautilus
``` in terminal, it'll give you a separate window with super administrator permissions. Then edit the file through that window

how exactly do i edit it trough that window? xD i have no idea how to.

---

### Post by Marius Derekus on 2008-11-17
You must type the command in terminal. Then a new window should pop up that looks just like any other ordinary window, but it has special privleges. After that go the directory of the file you want to edit, open the file just by clicking it (like you would with any other file). Than make the changes you want to make, and save. (It all works as if you using a regular window, but, it just has special privleges.

---

### Post by Marius Derekus on 2008-11-17
If you need more help just ask. (and give me about 10-20 minutes to reply. I have to run an errand).

---

### Post by lavinog on 2008-11-17
> **Turiko said:**
> read my problem number 1: no internet.


ok well then your only option is to edit it by hand.
Make a backup first:
press alt-f2:
```
gksudo cp /boot/grub/menu.lst /boot/grub/menu.backup
```

Now edit it:
press alt-f2:
```
gksudo gedit /boot/grub/menu.lst
```

you should see a section that looks like this:
```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

```
where the last line is the one that is important
change the 0 to the number corresponding to your windows entry.
to find this number scroll down to where you see:
```
## ## End Default Options ##
```
from there count the number of titles (starting at zero)
(also note that if you have a divider that says "Other operating systems:" it will count as an entry.)
when you are done, save the file.

A nice feature is the saved default...which when setup correctly will boot to the last os you booted to.

---

### Post by Turiko on 2008-11-19
you should see a section that looks like this:
```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

```
where the last line is the one that is important
change the 0 to the number corresponding to your windows entry.
[/QUOTE]
well, i don't have such a section. are you sure that isn't an update done in 8.10? i have ubuntu 8.04 clean install.

---

### Post by lavinog on 2008-11-19
It has been the same for the past couple of years.
Plus I copied that from a computer running 8.04.1

Can you post what you have?
How did you install ubuntu? (using wubi or booting from cd)

---

### Post by Turiko on 2008-11-19
i booted from a cd i ordered, and i installed it trough that.
And, again, it's a whole mess to "just" copy what i have, since i don't have an internet connection... can anyone help me with wlan first, because that'd make the rest easier too.

---

### Post by lavinog on 2008-11-19
> **Turiko said:**
> i booted from a cd i ordered, and i installed it trough that.
And, again, it's a whole mess to "just" copy what i have, since i don't have an internet connection... can anyone help me with wlan first, because that'd make the rest easier too.

can you not use an ethernet cable?
I would recommend starting a new thread for you wireless card. I don't know a whole lot about the drivers other than that they are restricted.
If you start a new thread, make sure you title your thread accordingly.

---

### Post by Turiko on 2008-11-20
i'll start a new thread, as i can' use a cable. It's have to be like 20+ meters, something that is quite expensive to just fix a software problem.

---

