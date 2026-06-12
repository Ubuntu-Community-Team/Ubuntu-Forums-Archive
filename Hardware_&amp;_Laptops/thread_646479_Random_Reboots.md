---
title: "Random Reboots"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by MONODA on 2007-12-21
Hi I am using using Ubuntu Gutsy Gibbon and have been experiencing random reboots. Could this be caused from overheating of the cpu? Or could it be caused by compiz fusion? this has never happened without compiz but I guess thats becuase I always have it on. Any help would be appreciated thank you. This is the one problem keeping me from only having ubuntu and its pushing me back to windows. It happens about once a month. I have tried reinstalling but I keep getting the same problem.

---

### Post by mikewhatever on 2007-12-21
It could be because the reasons you mentioned and many others. I've also had a few sudden reboots while running Compiz, so decided not to use it. You should try to investigate: check the cpus temperatures, disable compiz, etc.

---

### Post by xzero1 on 2007-12-21
Try this link for a good stability test:
[http://www.ibm.com/developerworks/linux/library/l-hw1/index.html?wzone=linux?open&l=335,t=gr,p=lxhwstabgd1]("http://www.ibm.com/developerworks/linux/library/l-hw1/index.html?wzone=linux?open&l=335,t=gr,p=lxhwstabgd1")

---

### Post by MONODA on 2007-12-21
Ok well I have disabled compiz and am now doing the ibm test. How can I check my cpu temperature?

---

### Post by Sef on 2007-12-21
> How can I check my cpu temperature?


First open the terminal, then 

```
sudo apt-get update
```

then  

```
sudo apt-get install hddtemp
```

For [checking the temp]("http://ubuntu.wordpress.com/2005/09/18/find-the-temperature-of-your-hard-drive/"):

> Later, whenever you want to check the temperature of the hard drive, do a:
$sudo hddtemp /dev/hda

where /dev/hda is the hardrive designator - which you can change if neccessary.

---

### Post by LaRoza on 2007-12-21
It could also be a power supply issue.

I use an Infra Red thermometer for finding the temperature of system components, but the program might be a quicker solution.

---

