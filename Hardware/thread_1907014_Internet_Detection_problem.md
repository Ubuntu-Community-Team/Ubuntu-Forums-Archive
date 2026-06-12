---
title: "Internet Detection problem"
date: 2012-01-10
forum: Hardware
---

### Post by Soma250 on 2012-01-10
Hello,
On a newly purchased Acer 5250 laptop I recently installed Ubuntu 11.10, which was followed by a string of random lockups, more often than not triggered by attempting to connect to a wireless network.  I decided to "downgrade" to Ubuntu 10.04 LTS, thinking it more reliable/stable.  I just finished this fresh install and Ubuntu is not detecting any internet connections - neither the wireless networks that my other laptops detect nor the ethernet connection I am currently using.
Any ideas on how to approach this? Help much appreciated!

---

### Post by IWantFroyo on 2012-01-10
If you want to try 11.10 again, run "Additional Drivers" and see if there are any wireless drivers you need.
 
As for Ubuntu 10.04, it seems you have a driver issue there, too, but without internet I'm not sure what to do about it.

---

### Post by Soma250 on 2012-01-10
I've been directed to [http://ubuntuforums.org/showthread.php?p=9449490](http://ubuntuforums.org/showthread.php?p=9449490) #6 as a likely answer to my problems, but I can't follow the steps - even having downloaded the new drivers and put them on to the relevant laptop I seem to need a functioning connection to install the drivers.

---

### Post by IWantFroyo on 2012-01-10
You need utilities to compile from source on your computer.

Check out this article:
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

You need to get build-essential, automake, checkinstall, and gcj onto that computer. Probably the best way to do this would be to go to the Debian Package Search and download the DEBs for Squeeze, and load them onto a flash drive.

Then use this to install:
```
sudo dpkg -i packagename
```

Here's automake to get you started:
[http://packages.debian.org/search?keywords=automake](http://packages.debian.org/search?keywords=automake)

---

