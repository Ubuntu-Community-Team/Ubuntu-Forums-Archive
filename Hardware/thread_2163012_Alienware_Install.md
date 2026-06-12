---
title: "Alienware Install"
date: 2013-07-16
forum: Hardware
---

### Post by elroypettyjohn on 2013-07-16
When installing from a CD, I get the message (approximatly) "this kernal needs a CPU with the following", next line is "pae", nextline is "download a different kernal".  My Alienware is approximately 10 years old.

---

### Post by papibe on 2013-07-16
Hi elroypettyjohn.

Which Ubuntu version are you trying to install?

Is it 32bits or 64bits?

Are you able to run the installation CD as a Live media (option Try Ubuntu)?

If so, could you post the results of these commmands?
```
sudo lshw -C cpu | grep -i product

free -m
```
Regards.

---

### Post by Yellow Pasque on 2013-07-16
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

But yes, please give output of those commands to see if you can use fake PAE or not.

---

### Post by elroypettyjohn on 2013-07-16
I am trying to install 12.04 LTS.  I have no opportunity to enter commands -- the keyboard is totally inactive -- the only way I can recover is to disconnect all power and reboot.  I can boot Windows XP on this computer.

---

### Post by Yellow Pasque on 2013-07-16
Well, to make the story short, install Lubuntu 12.04 (once you have it installed, you can install whatever desktop you want if you don't care for lxde: [http://cdimages.ubuntu.com/lubuntu/releases/precise/release/](http://cdimages.ubuntu.com/lubuntu/releases/precise/release/)

---

