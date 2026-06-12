---
title: "Upgrading to 64bit version of 8.10"
date: 2008-11-08
forum: General Help
---

### Post by rmcellig on 2008-11-08
I have the 32bit version of 8.10 installed on my PC. I recently bought a 64bit processor/motherboard and would like to upgrade to the 64 bit version of 8.10. I downloaded the 64bit CD version of 8.10 and would like to know what is involved in upgrading from my current 8.10 verion to the 64bit version of 8.10

---

### Post by simtaalo on 2008-11-08
installing fresh rather than upgrading is a better option

---

### Post by bodhi.zazen on 2008-11-08
As far as I know there is no direct upgrade, you simply re-install using 64 bit Ubuntu.

---

### Post by drs305 on 2008-11-08
You can't really do an 'upgrade' from 32 to 64-bit. You would have to do a clean install of the 64-bit version. If you have your /home on a separate partition you can save some of your settings and make the transition easier. 

You can also make a copy of your currently installed apps and then import the list to your new install with the following commands, which will save the list to your Desktop. (Save the list on a removable drive or another partition since the Desktop will likely be overwritten). The 64-bit versions of the apps will be installed.

Create a list of installed packages:
```

sudo dpkg --get-selections | grep -v "deinstall" >~/Desktop/package.list 

```
*Copy this file to the new setup and then:*
```

sudo aptitude update
cat ~/Desktop/package.list | xargs sudo aptitude install

```
*or*
```

sudo dpkg --set-selections <~/Desktop/package.list
sudo aptitude update 
sudo aptitude upgrade

```

---

### Post by aquarianwolf on 2008-11-08
I'm sticking with 64bit 8.04 I've tried 8.10 but I found it to be really laggy and it didn't seem as happy to do things as 8.04 does.

---

### Post by rmcellig on 2008-11-08
Thanks. So I should hold off going with 8.10 64 bit for now? At the moment I am running 32 bit 8.10.

---

### Post by Skripka on 2008-11-08
> **rmcellig said:**
> Thanks. So I should hold off going with 8.10 64 bit for now? At the moment I am running 32 bit 8.10.



"Should" is a matter of debate.  There are several threads o'er in yonder X86_64 forum on the pros/cons of 64-bit.



Unless you have more than 4 GB of ram, odds are you won't notice much difference.  I depends on how well the software you are using is optimized for such--as well as where the bottlenecks are in your system.

---

### Post by Yellow Pasque on 2008-11-08
I would not recommend wiping out a working install for 64-bit unless you're doing some application that would see significant gain from it (e.g. video encoding, Photoshop, running virtual machines)

---

### Post by rmcellig on 2008-11-08
Thanks for all of your help. I will stay with my current 32bit version of 8.1.0

---

