---
title: "USB External HDD - Cable is Bad?"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by Simey on 2007-10-24
Hi, 
I have a Hitachi "Travelstar" 2.5" 60gig hard drive (IC25N060ATMR04-0)
In a rather generic looking "Welland" external hard drive case

It is formatted as NTFS, and I do have NTFS-3G on for both internal and external drives.

When plugged in the hard drive whirs up, but could not be found using fdisk or gparted.

```

simon@simon-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

After having tried to mount it multiple times in different USB ports.
```

simon@simon-desktop:~$ dmesg|tail
[  563.994168] hub 4-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[  564.920406] hub 4-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[  674.946986] hub 4-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  675.873230] hub 4-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  676.799472] hub 4-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  677.725707] hub 4-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1016.492972] hub 4-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1017.419201] hub 4-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1018.345429] hub 4-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1019.271674] hub 4-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?

```

The cable most definitely is not bad, and has been tested and proven to work on a Windows machine. The only peculiar thing is that it has an odd appendage. While there is a usual cable from a male USB plug to the HDD connector, from the male plug there is a thinner cable going to a T shaped double-USB plug, one male, one female (I hope that makes sense to anyone other than me, if not and you think it matters, I'll find a picture for you.) I have tried plugging it in with both male connectors, with no variation in results. Is there some form of interference with these odd cables that Linux cannot deal with? 

Thanks a lot for any response, all suggestions are welcome. 
Simey.

Edit: It looks related to this, however, what is going on there is well over my head. [http://ubuntuforums.org/showthread.php?t=386173&highlight=Maybe+the+usb+cable+is+bad](http://ubuntuforums.org/showthread.php?t=386173&highlight=Maybe+the+usb+cable+is+bad)
Oh, and for the record, everything else USB that I have tried has worked just fine, if you're wondering.


**Problem sovled! **
Having been given the hint by Windows, and that fact that it always used to mount everything as USB1.1 regardless of which port it was plugged into, I decided that the motherboard attempting to use USB2.0 was the problem and so disabled it.

This can be read up on, here;
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Workaround_for_random_device_disconnections](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Workaround_for_random_device_disconnections)
The symptoms are different to what that is directed to, but the solution is the same: hideously slow data transfer makes it work.

Thanks for listening to my monologue :-)

---

### Post by Simey on 2007-10-24
< Deleted >

---

