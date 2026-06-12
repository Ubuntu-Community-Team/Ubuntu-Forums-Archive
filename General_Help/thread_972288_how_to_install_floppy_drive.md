---
title: "how to install floppy drive"
date: 2008-11-05
forum: General Help
---

### Post by oldlager on 2008-11-05
i have just upgraded to intrepid ibex and i cant access my floppy drive which worked in ubuntu 8.04.
any help would be good.

---

### Post by sisco311 on 2008-11-05
open a terminal and post the output of:
```
sudo lshw -C disk
```
and
```
cat /etc/fstab
```

---

### Post by plucky on 2008-11-05
> **oldlager said:**
> i have just upgraded to intrepid ibex and i cant access my floppy drive which worked in ubuntu 8.04.
any help would be good.

Open a terminal and ```
sudo modprobe floppy
``` will load the floppy driver.

To make it permanent between reboots ```
gksudo gedit /etc/modules
``` and just add the word **floppy** on a separate line.This will load the floppy driver on a reboot.


Good Luck

---

### Post by oldlager on 2008-11-06
thanks for both replies the first command seems to think it is loading the c disk and the the dvd but does not mention  floppy,the second one does nothing.
I think i am in need of further help                                                           if possible.

---

### Post by Yellow Pasque on 2008-11-06
Do this:
> **sisco311 said:**
> open a terminal and post the output of:
```
sudo lshw -C disk
```
and
```
cat /etc/fstab
```

---

### Post by sisco311 on 2008-11-06
> **oldlager said:**
> thanks for both replies the first command seems to think it is loading the c disk and the the dvd but does not mention  floppy,the second one does nothing.
I think i am in need of further help                                                           if possible.

can you please post the exact output of the commands:
```
sudo modprobe floppy
```
```
gmesg | tail
```
```
sudo lshw -C disk
```and
```
cat /etc/fstab
```

---

### Post by oldlager on 2008-11-06
thanks both of you for your help i think i have tracked down the problem.
i fitted a second hardrive and this seems to be the problem,when i enter the commands they show the fujistu h/d and not the floppy so i will have to check the wiring.
its funny the floppy works fine with the second h/d which has xp pro.loaded but just wont show on the other drive,its not really a problem i can always just use xp for the floppies anyway it might make me transfer what is stored on them to cd.
thanks again for your help.

---

