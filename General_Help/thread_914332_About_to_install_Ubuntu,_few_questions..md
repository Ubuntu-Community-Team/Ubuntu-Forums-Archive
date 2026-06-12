---
title: "About to install Ubuntu, few questions."
date: 2008-09-08
forum: General Help
---

### Post by Virtua-Touch on 2008-09-08
1) Is my nVidia GeForce 6600 able to use desktop effects? (Cube, Wobbly windows, etc.)

2) Is EnvyNG a good way to install the drivers for my card?

and..

3) Can I run Windows  while install Ubuntu? (after booting into ubuntu for the install)

Thank you.

---

### Post by schmindy on 2008-09-08
1. not sure:(
2. not sure:(
3. Yes as long as you partition it correctly:)

---

### Post by kjohansen on 2008-09-08
2) There is built in functionality for installing restricted drivers for video cards.

System->Administration->Hardware Drivers

---

### Post by Virtua-Touch on 2008-09-08
Okay, My drivers were automatically installed. Now, how would I go about controlling my Windows (C Drive) and my Ubuntu (Installed with Wubi on the storage drive, E) at the same time?

---

### Post by panhandle on 2008-09-08
Looks like the installation might be a little complicated, but not too bad. 

Here are two links to get you started--look *before* installation. I don't personally use an Nvidia card, but I know people who have had difficulty. Take a look around the boards.

1) [http://www.linuxquestions.org/questions/ubuntu-63/6600-problems-with-nvidia-geforce-521743/](http://www.linuxquestions.org/questions/ubuntu-63/6600-problems-with-nvidia-geforce-521743/)

2) [https://wiki.ubuntu.com/EnvyNG](https://wiki.ubuntu.com/EnvyNG)

---

### Post by Virtua-Touch on 2008-09-08
> **panhandle said:**
> Looks like the installation might be a little complicated, but not too bad. 

Here are two links to get you started--look *before* installation. I don't personally use an Nvidia card, but I know people who have had difficulty. Take a look around the boards.

1) [http://www.linuxquestions.org/questions/ubuntu-63/6600-problems-with-nvidia-geforce-521743/](http://www.linuxquestions.org/questions/ubuntu-63/6600-problems-with-nvidia-geforce-521743/)

2) [https://wiki.ubuntu.com/EnvyNG](https://wiki.ubuntu.com/EnvyNG)
I already said that my drivers were installed automatically, and my composite effects are applied and working well. I need to know how to control Windows from Ubuntu.

---

### Post by SunnyRabbiera on 2008-09-08
> **Virtua-Touch said:**
> I already said that my drivers were installed automatically, and my composite effects are applied and working well. I need to know how to control Windows from Ubuntu.

you may need a virtual machine client for that bit, as you cant really do that sort of thing by default no matter what OS you use.

---

### Post by Virtua-Touch on 2008-09-08
> **SunnyRabbiera said:**
> you may need a virtual machine client for that bit, as you cant really do that sort of thing by default no matter what OS you use.
Darnit.

---

### Post by chuche17 on 2008-09-08
If by "control" you mean actually control the Graphical User Interface then you can't. No matter what OS you install you can't run your existing installation of Windows side by side to control. 

HOWEVER, you can control what you read/write off the drive assuming it is formatted in NTFS, or even FAT32. In Ubuntu 8.04 Hardy the drives should automatically mount and you would see them in the desktop. You can then easily browse their contents and read/write stuff to them.

---

### Post by Virtua-Touch on 2008-09-08
Yes. I know.

---

