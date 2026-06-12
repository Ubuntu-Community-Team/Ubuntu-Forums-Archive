---
title: "Installing Ubuntu on Toshiba Satellite L750"
date: 2012-02-13
forum: Hardware
---

### Post by vishaluc on 2012-02-13
Hi, I'v got the Toshiba L750 model. Could anyone help me with a step by step procedure to install ubuntu(any version). Never faced any problem while installing it on my desktop, but apparently toshiba doesn't support op systems apart from windows! i tried installing it, but while booting it doesn't show any option other than win7. Also the "help boot from CD" option doesn't work.

---

### Post by Mark Phelps on 2012-02-13
> **vishaluc said:**
> Hi, I'v got the Toshiba L750 model. Could anyone help me with a step by step procedure to install ubuntu(any version). Never faced any problem while installing it on my desktop, but apparently toshiba doesn't support op systems apart from windows! 
Not true ...
> i tried installing it, but while booting it doesn't show any option other than win7. 

That's most likely because, like many other PC suppliers, Toshiba may sell the PC with the maximum of 4 primary partitions already configured on the drive.  When the Ubuntu installer sees this, it refuses to allow you to install because it's unable to make the partitions needed.

Let's start by the following:
1) Boot using an Ubuntu desktop CD
2) Choose Try Ubuntu
3) Open a terminal and enter "sudo fdisk  -lu" (lowercase L, not a one).  That will list out the partitions in your PC.
4) Post the results of that command back here.

If you do have the maximum number of partitions already, you will have a very difficult time installing because you will have to REMOVE an existing partition in order to do that.

---

### Post by vishaluc on 2012-02-14
But the problem is that while booting i don't get an option for anythin else other than win7. I tried all the function keys while booting, and it gives me 2 options, one for win7 and one related to windows crash recovery or something like that. Just those two. No option of booting from CD drive or anything else.

---

### Post by Justinelectric on 2012-02-14
Go into the bios, and arrange the boot order to boot from CD.

---

