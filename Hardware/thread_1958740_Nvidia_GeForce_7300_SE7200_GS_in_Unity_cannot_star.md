---
title: "Nvidia GeForce 7300 SE/7200 GS in Unity cannot start compiz effects or may be driver"
date: 2012-04-14
forum: Hardware
---

### Post by sensenku on 2012-04-14
Hi, I need help for solving my VGA problem ,my VGA card is Nvidia GeForce 7300 SE/7200 GS and I use Ubuntu 11.10, but I thing that driver not installed in my comp, how can I prove that driver is installed and in  use?

---

### Post by Docmero on 2012-04-14
Try this code 
```
sudo apt-get install mesa-utils
```

---

### Post by sensenku on 2012-04-15
I did it,but there is not effect :(

---

### Post by grahammechanical on 2012-04-15
Open the Dash and search for Additional Drivers. That utility will tell you if you have a proprietary driver installed. It will say activated. If it is not activated then click Activate and the driver will be downloaded and installed.

Bu the way, you do have a driver installed otherwise the OS would not be loading to a desktop. The driver is an open source development.

Also, as you have an Nvidia Card you can search in the Dash for Nvidia. If an Nvidia proprietary driver has been installed in the past you will have an Nvidia X-Server Settings utility. It gets installed along with the driver.

What is the problem that you are trying to solve?

Regards.

---

### Post by sensenku on 2012-04-16
I opened synaptic and installed all nvidias,and removed ati drivers. Then I installed it from additional driver which was written "recommended". And I am using Ubuntu 11.10 Unity UI. When I search in Dash, it founds Nvidia X Server settings utility, and there written name of my VGA card. But it is not activated,because I can not use Compiz effects :(

---

### Post by Cpierce on 2012-04-16
See if my post helps. I had the nvidia 7300 as well.

[http://ubuntuforums.org/showthread.php?t=1956779](http://ubuntuforums.org/showthread.php?t=1956779)

Once I did this, Unity 3D and compiz worked.

---

