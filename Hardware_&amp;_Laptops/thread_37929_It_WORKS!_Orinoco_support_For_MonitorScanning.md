---
title: "It WORKS! Orinoco support For Monitor/Scanning"
date: 2005-05-29
forum: Hardware &amp; Laptops
---

### Post by digiital on 2005-05-29
After a slow compile overnight(not sure why it took so long), but my Thinkpad and the Orinoco(Gold) now supports Monitor and Scanning so in other words you can now run KISMET and WIFI-RADAR. Might not be the best solution, but it works.

The key is to install a older version of the Orinoco drivers, patched.

So follow the instructions found: [http://www.ubuntuforums.org/showthread.php?t=23596&highlight=kismet](http://www.ubuntuforums.org/showthread.php?t=23596&highlight=kismet) with a few exceptions.

(Please NOTE I will create some better step-by-step instructions, until then)

Alright, I'll list what steps you do NOT need to do:
[B]"get the monitor mode patch"
"patch the kernel-source"
"and if no errors appear"[/B]

Inplace of those steps do the following:

Download  from this page: [http://www.tzi.de/~plasmahh/orinoco.html](http://www.tzi.de/~plasmahh/orinoco.html) the following driver: **"orinoco-0.13e-SN-7.tar.bz2"**

Just for the quickness of posting this howto, lets download the driver into the /tmp directory with the following:

```
 cd /tmp 
```
```
 wget http://www.tzi.de/~plasmahh/orinoco-0.13e-SN-7.tar.bz2 
```
```
bunzip2 orinoco-0.13e-SN-7.tar.bz2 
```
```
 tar -xvf orinoco-0.13e-SN-7.tar
```
```
cd orinoco-0.13e-SN-7 
```
```
cp *.c /usr/src/linux/drivers/net/wireless/. 
```
```
cp *.h /usr/src/linux/drivers/net/wireless/. 
```

Thats it for me now. Now just continue from the step [B]"
Make a directory to backup the existing drivers."[/B]

If all goes well, you will be able to have your cake and eat it.

---

### Post by digiital on 2005-05-29
Hold the boat. I think I might have jump the gun alittle too soon.  I need to do some more testing.

---

### Post by NTolerance on 2005-06-01
Please keep us posted.  I am interested to see what you find as there currently isn't a good solution for this.

---

