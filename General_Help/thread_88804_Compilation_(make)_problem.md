---
title: "Compilation (make) problem"
date: 2005-11-11
forum: General Help
---

### Post by M4v3R on 2005-11-11
Hello everyone, I'm new here.
I recently installed kubuntu 5.10 and I like it much. I don't know linux system that good though, and I run up to a problem.
My computer is a laptop with Intel 2200BG Wireless card. I found some driver's that should help me use it, but I can't compile it. I've extracted source file (fsam.c) and Makefile to some directory and typed 'Make' and got an error message: "There are no rules for object 'modules'" or something like that (I use polish interface so I don't know exactly what it was). It seems to be referring to  /lib/modules/[kernel version]/build/, which doesn't exist. Can anyone help me on this?

---

### Post by Manny C on 2005-11-11
From where did you download the drivers and what driver did you download?

---

### Post by mo_x on 2005-11-11
I think the driver you need is the ipw2200 and it is already present in Ubuntu. From a terminal window type:
```
sudo modprobe ipw2200
```

---

### Post by M4v3R on 2005-11-11
Thanks for responses.
The ipw2200 driver is loaded, but card still doesn't work. The problem is that I'm on Amilo M7440G laptop with this little Wi-Fi button on the left to Power button. Wireless card is off by default to save power, and can be enabled only by this button. But the trick is, this button only works when card driver is loaded (in Windows - only after wi-fi indicator shows up). I've read that this fsam.c proggy will solve this situation, but unfortunately it doesn't compile. I've attached it, maybe it'll help. 
Thanks in advance.

---

### Post by Manny C on 2005-11-11
Have you tried executing
```
 sudo ifup eth1 
```
where eth1 is you wireless card address?

---

### Post by M4v3R on 2005-11-12
Yup, nothing happens.

---

### Post by mo_x on 2005-11-12
To compile make sure you have the following packages installed:
build-essential
linux-headers-[your kernel version]

---

