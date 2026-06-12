---
title: "Problems installing Ubuntu"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by doubledragon5 on 2009-10-01
Hi new to the Linux experience and have had one hell of a time trying to get anyone to work with my network.. So here is the question concerning Ubuntu. I have tried to install it twice. Each time I have choose use entire disk, and would choose, which disk to use.. After installing I can't boot into ubuntu or my windows partition.. I have two separate physical drives, one is for Vista, and the other I wanted to use and try out any version of Linux.. Where am I going wrong with the installation? Because each time required me to do a complete format of both drives, as even repairing the MBR would not allow me to access Vista, nor was I able to do a repair using the Vista CD. Thanks..  I also tried it without installing grub and letting Windows use its boot loader no dice..

---

### Post by rreese6 on 2009-10-01
To help you with your problem, more information is needed.

1. Boot up with LiveCD. Once you are on the Desktop, got to this link and download:
```
[Download Boot Information Script]("http://sourceforge.net/projects/bootinfoscript/")
```
This Script will gather your current configuration and make a report.
This gives us a better idea of what your problem is and how to fix it.

2. Open up terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will make a file called "Readme.txt" on your desktop.

3. Post the contents of that file here.

---

### Post by doubledragon5 on 2009-10-01
Thanks for responding will do that when I get home from work tommorow... Another problem I for got to mention I get get to the internet, as it will not recognize my wusb300n wireless adapter... I do have a pci wireless adapter I will install and see if that helps...

---

### Post by rreese6 on 2009-10-04
Any Progress with this issue?

---

