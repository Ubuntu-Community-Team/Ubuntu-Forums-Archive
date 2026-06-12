---
title: "DLink network card driver install help"
date: 2010-10-05
forum: Hardware
---

### Post by tubaguy50035 on 2010-10-05
I have Googled this over and over, and the best information I have found so far is here:

[http://art.ubuntuforums.org/showthread.php?t=14788](http://art.ubuntuforums.org/showthread.php?t=14788)

I've followed everything and everything works, right until the  installation. It tries to compile and there is some error.  Everything  in the install.log file looks okay until the very bottom.  This is in  the compile driver section: Make: Leaving directory  '/usr/src/linux-headers-2.6.32-24-generic' +++Compiler error.  Thoughts?

---

### Post by tubaguy50035 on 2010-10-06
please help

---

### Post by Yellow Pasque on 2010-10-06
It uses a Marvell Yukon 88E8001 chipset, so I would try this driver: [http://extranet.marvell.com/drivers/driverDisplay.do?driverId=153](http://extranet.marvell.com/drivers/driverDisplay.do?driverId=153)

---

### Post by tubaguy50035 on 2010-10-07
Okay.  Thank you for that.  I still don't have the card working.  It is detected by the system by running "lspci".  It does not show up under ifconfig though.  Thoughts or ideas?

---

### Post by Yellow Pasque on 2010-10-07
So did that driver compile and install? Does it load? lshw will show that and also look for relevant errors in dmesg.
```
sudo lshw -C network
dmesg
```

---

### Post by tubaguy50035 on 2010-10-07
The driver did compile and install.  I will run lshw now and post back.

---

### Post by tubaguy50035 on 2010-10-07
After running lshw, it shows the device as disabled.  How would I enable it?

---

### Post by tubaguy50035 on 2010-10-08
I got it up and running!  I had to edit the network cards config file.  I'm only getting about 30~40 MB/s.  Is this typical?  This is from a raid 5 on one computer to a raid 5 on the server.  I would think I should see right around 100MB/s

---

