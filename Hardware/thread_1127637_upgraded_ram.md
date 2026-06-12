---
title: "upgraded ram"
date: 2009-04-16
forum: Hardware
---

### Post by Sojurner on 2009-04-16
I installed an additional 2 gigs of Ram just a min ago.. and linux is detecting only 3 of the 4.. i went from 2 to 4 gigs..

When i boot my pc my bios detects all 4 gigs but linux is only seeing 3.. any idea why?

---

### Post by abn91c on 2009-04-16
the 32bit ubuntu sees only 3.2 gigs, if you Pc is a new dualcore type PC it may support 64bit ubuntu and you may have to install that version. Post your hardware specs

---

### Post by taurus on 2009-04-16
If you are running 32bit kernel, you would only see 3.2GB of your total RAM.  If you want to use all 4GB, then you need to install the kernel from the server version or run 64bit (x86_64) if your CPU supports 64bit.

---

### Post by Sojurner on 2009-04-16
it does support 64 bit.. its a dual core amd 6000+.   Can i upgrade to the 64 bit kernel without re installing?


another question. wont i only be able to run 64bit versions of software then like in widows.. or will i still be able to run 32bit software with the 64bit kernel

---

### Post by taurus on 2009-04-16
If you install x86_64, you can still run all those i686 apps providing you've installed ia32-libs first.  (That is the 32bit libraries.)

---

### Post by Therion on 2009-04-16
> **Sojurner said:**
> it does support 64 bit.. its a dual core amd 6000+.   Can i upgrade to the 64 bit kernel without re installing?
No.  You'll need reinstall using a 64-bit installer.

> **Sojurner said:**
> another question. wont i only be able to run 64bit versions of software then like in widows.. or will i still be able to run 32bit software with the 64bit kernel
You can run 32bit packages, you just need the aforementioned ia32 package.  I've been running 64 bit distros for ages and it's never been an issue.

---

### Post by Sojurner on 2009-04-16
well dang.. lol here goes another install. but thats good to know that i wont have any issues running 32bit packages...

Thanx for the help



Will it read 8 gig when i do a mobo cpu and mem upgrade

---

### Post by Therion on 2009-04-16
> **Sojurner said:**
> well dang.. lol here goes another install.
They build character.  :)

As to your 8GB of memory question... 

64 bit OS'es will recognize up to 1TB of RAM, if memory serves (HA!), so you should be safe for a while.

---

### Post by Sojurner on 2009-04-16
What would the command be to isntall the 32bit libraries and such that yall mentioned earlier..

sudo apt-get install  (what)

---

### Post by Therion on 2009-04-16
> **Sojurner said:**
> What would the command be to isntall the 32bit libraries and such that yall mentioned earlier..

sudo apt-get install  (what)
```
sudo apt-get install ia32-libs
```
It's in Synaptic, but I believe it comes with a default install of 64-bit (at least it does in Jaunty because I have it installed, but I didn't have to install it myself).

---

