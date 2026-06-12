---
title: "Reverting changes/installations"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by majo551 on 2009-08-13
Hello, 
I just wanted to resolve my MSI camera not working in Ubuntu. Installed a driver  based on [http://www.pamplast.com/gspca/ubuntuguide.html](http://www.pamplast.com/gspca/ubuntuguide.html) .
Not only the USB camara stopped working completely but it also stopped the video capture card.  
I am new to Linux and use Ubuntu for learning purpose and I really want to learn on making errors on my own.
I would be glad if anybody more experienced showed me how to revert back the changes the script made and allowing the original drivers for video in Ubuntu to work again.
Is there any option , like in Windows to return the system to the stage in  some point in time?
Thanks a lot for your recommendation
```

the script:
#!/bin/sh 
rm msicam.tar.gz* >/dev/null
sudo rmmod gspca
sudo rmmod msicam 
sudo rmmod sn9cxxx
sudo rmmod sn9c102 

sudo rm -R msicam/ >/dev/null
wget www.pamplast.com/gspca/msicam.tar.gz
tar xzvf msicam.tar.gz
cd msicam
sudo ./c
cd ..
sudo rm  msicam.tar.gz*
sudo rm -R msicam/


sudo echo "# This part is added by msicam_install script http://www.pamplast.com/gspca/"  >>/etc/modprobe.d/blacklist
sudo echo blacklist gspca >>/etc/modprobe.d/blacklist
sudo echo blacklist sn9c102 >>/etc/modprobe.d/blacklist
sudo echo blacklist sn9cxxx >>/etc/modprobe.d/blacklist
sudo echo "# End of list " >>/etc/modprobe.d/blacklist
exit 0

```

---

### Post by dstew on 2009-08-13
I don't think there is any automatic way to go back. It looks like the script removed and blacklisted three modules, probably this is what caused your video capture card to stop working. It completely removed the old msicam module, got a new one, and installed it. Since the old one did not work, probably you can just un-install the new one. Re-install the blacklisted modules, and then you will have a system with no msi camera functionality, but a working video capture card, hopefully.

First, edit the /etc/modprobe.d/blacklist file to remove the lines```
blacklist gspca
blacklist sn9c102
blacklist sn9cxxx
```You might want to add the line```
blacklist msicam
```to make sure the msicam module is not used. It might be causing a problem. Then, re-install the formerly blacklisted modules:```
sudo insmod gspca 
sudo insmod sn9cxxx
sudo insmod sn9c102
```Then, remove the msicam module:```
sudo rmmod msicam
```You don't have to bother removing the msicam module code from the hard drive. Leave it there for now. Anyway, see what happens after these steps. Post back your results.

---

### Post by majo551 on 2009-08-14
Thanks. Blacklisting bit worked, the re-install part ended with errors. Despite, the capture card works again.
Is there any system log on all the changes, installations and removals done  in order  to do a  manual system restore since there is no auto restore for similar cases?

Cheers,
Marian

---

### Post by dstew on 2009-08-15
System logs are in the /var/log directory. A series of syslog files contain the system logs. I don't know if they would have the information you are looking for, but anyway, that is where they are.

---

