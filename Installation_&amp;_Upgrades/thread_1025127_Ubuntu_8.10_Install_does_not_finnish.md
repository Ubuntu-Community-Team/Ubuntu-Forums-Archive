---
title: "Ubuntu 8.10 Install does not finnish"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by ranc0r37 on 2008-12-29
My install of ubuntu 8.10 fails. I get past the format drive, about 20% into installing and it just boots to the live user with a short cut on the desktop to install. I have ran the cd disk check, My install disk is good.  I'm currently running the memory check which I'm sure is good also. 

Amd 1.5 ghz
200 gb hard drive
3gb of memory


Don't flame or bitch if this is already covered. I have searched. If i did not need help or knew what i was doing I would not be posting.

---

### Post by kjamo36 on 2008-12-29
try downloading the Alt CD... its the non graphical installation cd. i had the same problem

---

### Post by ranc0r37 on 2008-12-29
If this works I'm going to shoot myself. I only spent 3 days trying to get either 8.10 or 8.04 to install. got a new cd drive and swapped hard drives. Any other suggestions while the alt install is downloading are welcomed

---

### Post by kjamo36 on 2008-12-29
when ur installing, its gonna ask u something about  swap memory.. its for hibernation, 
add like about 512mb for hibernation memory

---

### Post by ranc0r37 on 2008-12-29
i got the following errors while installing with the alt install

Debootstrap warning
Failure trying to run chroot/target dpkg--force-depends--install var/cache/apt/archies/libc6_2.8~20080505-oubuntun7_i386.deb

Base system installation error
The bootstrap program exited with an error. (return value 1)
Check /var/log/syslog or see virtial console 4 for details

failed to install base system
The base system installation into /target/ failed.
Check /var/log/syslog or see virtial console 4 for details

---

### Post by kjamo36 on 2008-12-29
ur system is a 64 bit or 32?

---

### Post by linux_tech on 2008-12-29
Try pre-formating a partition with ext3. You can run gparted off live cd
to do it

---

### Post by ranc0r37 on 2008-12-29
ran the install again and made it past the errors. currently hung up on the "select and install software" it gives no errors just says it failed and suggest I try again which I'm currently doing. The system is 32 bit. I am installing ubuntu-8.10-alternate-i386.iso

---

