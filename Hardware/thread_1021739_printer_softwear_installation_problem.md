---
title: "printer softwear installation problem"
date: 2008-12-25
forum: Hardware
---

### Post by tsaleem on 2008-12-25
i have a HP laserjet 1020 when i install this softwear to interact to the motherboard the error comes "setup encountered an abnormal program execution setup will shutdown" 

plz tell what is it and how to resolve this problem

---

### Post by Sef on 2008-12-26
Read [HP LInux Imaging and Printing]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1020.html") for your printer.

---

### Post by linux_tech on 2008-12-26
Download hplip-
[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1020.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1020.html)


Basic instructions are for the automatic install are the following
In the terminal type:
```
sudo apt-get install hplip-gui 
``` (install hplip-gui)


To start fresh before installing new hp1020, go to System > Administration > Printing , and remove the current 1020 printer setup (if you have an old one)

```
 sudo hp-setup 
```  (make sure internet is connected then follow setup wizard to set up printer)
--*refer to these screenshot wizard instructions: [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html) (but mostly next, next....)

then make sure your username is in lpadmin and scanner groups:
```
sudo adduser $USER scanner
sudo adduser $USER lpadmin
```

lastly, reboot printer and reboot pc.  It should be connected and working  

If preferred, there is also a HPLIP Manual Install;
[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

---

