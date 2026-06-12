---
title: "problem in my new laptop"
date: 2011-11-14
forum: Hardware
---

### Post by khaled.battah on 2011-11-14
hello I got my new laptop
HP dv6-6177ee
I have two problems with ubuntu 11.10
 my ATI graphic card is not recognized and the additional hardware utility finds the drive 2d and 3d and i cant install them both right?
the secound proglem is my processor the I7 
I think all the 8 cores are working and that makes my battery goes down so quickly.. how can i close the cores and make the battery life good and also the last problem is the heat,because it sucks

---

### Post by BillyBoa on 2011-11-14
The problem with the battery could be solved installing jupiter:

```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```

For more about it you could search to tweak your kernel:

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

For the ATI drivers try to install the new ones from AMD:

[http://linux.softpedia.com/get/System/Hardware/ATI-Radeon-Linux-Display-Drivers-6719.shtml](http://linux.softpedia.com/get/System/Hardware/ATI-Radeon-Linux-Display-Drivers-6719.shtml)

You download the file and then move it to home and write to a terminal:

```
sudo bash /usr/share/ati/fglrx-uninstall.sh
```

```
sudo bash ati-driver-installer-11-10-x86.x86_64.run
```

---

### Post by khaled.battah on 2011-11-14
thanks  man :):) I will try it and what about the cores of the I7??

---

### Post by iavor on 2011-11-14
> **khaled.battah said:**
> thanks  man :):) I will try it and what about the cores of the I7??

About the cores.. try in BIOS see if there is a option to disable Hyper-Threading, that would remove the extra 4 threads and give you some juice.

---

### Post by khaled.battah on 2011-11-15
another question
why is my intel graphic card not recognized at all???
Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

---

### Post by BillyBoa on 2011-11-15
Check here if the solution applies to your problem

[http://ubuntuforums.org/showthread.php?t=1615564&highlight=intel+graphic+card](http://ubuntuforums.org/showthread.php?t=1615564&highlight=intel+graphic+card)

---

### Post by khaled.battah on 2011-11-15
no thats not what i mean:(:(
wha ti mean that the intell GPU is un recognized and I am unable to use the ATI either because teh ATI is for the heavy graphics (Games)

---

### Post by khaled.battah on 2011-11-15
but I will try the tips of jupiter t osee if it might work

---

