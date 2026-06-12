---
title: "D-link wifi adapter installation"
date: 2014-10-13
forum: Hardware
---

### Post by Jahidul_Hamid on 2014-10-13
How can I make DWA-132 D-link wifi adapter work in xubuntu/ubuntu 14.04 LTS. The device is not officially supported for linux or mac. I am looking for a workaround..

---

### Post by Stormlord on 2014-10-16
If you have checked in **Additional drivers** and there is no proprietary driver for your card in there, you can do the following:

1.  First of all, find the latest Windows XP driver for your card.  I has to be in an expanded form, not a self installing .exe file because you need access to the .inf file and the driver file themselves.
2.  Use your wired connection and install ndisgtk.  (**sudo apt-get install ndisgtk** if you use a terminal).  This will install ndiswrapper and its GUI app.  Make sure ndiswrapper-dkms gets installed too.  I think it's selected automatically when you install ndisgtk but I'm not 100% sure.
3.  After that, you should be able to find **Windows wireless drivers** installed on your system.  Run the app and install a new driver.  You must tell ndisgtk where the Windows XP driver folder is and especially the .inf file.  This is what it's looking for.  After it finds it, it will check your system for a matching device and it will inform you about its successful detection.

After you finish this process, you should be able to see all the available wireless networks in your area and of course yours too if the SSID is not hidden.

Make sure your SSID is not hidden.  Ndiswrapper has some issues connecting to hidden networks sometimes.

---

### Post by Vladlenin5000 on 2014-10-16
Suggesting *ndiswrapper* without even knowing what the hardware (chipset) this dongle has - different revision numbers, different chipset - is irresponsible*, to say the least...
Using that 'hack' with Windows drivers is always the last resource and even when it works it performs so poorly that one wonders if it was really worth the trouble...

Please connect the dongle and post the results of ```
lsusb
```

* It can turn any subsequent troubleshooting into a nightmare..

---

### Post by overdrank on 2014-10-17
Some post have been moved to the jail. Please stay on topic and please keep the [_Ubuntu Forums Rules_]("http://ubuntuforums.org/misc.php?do=showrules") when posting.
> The purpose of the Ubuntu Forums is to provide support for Ubuntu. We also want this to be a place where community can develop and we can enjoy one another's company. To achieve this, we strive to maintain an atmosphere that can be enjoyed by all and we ask all members of the community to be respectful at all times. This means please use etiquette and politeness. Treat people with respect. If you do this, the rest of the code of conduct won't need more than a cursory mention.

---

### Post by Bucky Ball on 2014-10-17
Avoid ndiswrapper at all costs unless there is no other way your wireless card will work. 

As suggested by Vladlenin5000, give the output of the command they've provided. Run the command with the wireless card in if it is USB.

---

