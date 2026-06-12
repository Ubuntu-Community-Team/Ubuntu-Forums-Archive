---
title: "Advise on NVIDIA and WEBCAMs"
date: 2006-04-02
forum: Hardware &amp; Laptops
---

### Post by lfrossati on 2006-04-02
Hi!

Well, it took me hours to discover a solution, but here it goes... this advice applies only to people with nvidia and some webcams (see [http://www.ubuntuforums.org/showpost.php?p=407656&postcount=1](http://www.ubuntuforums.org/showpost.php?p=407656&postcount=1))

1 - Dont try to use the latest nvidia drivers from nvidia's website. Since you need the linux-restricted-modules to get the webcam working ( see [http://www.ubuntuforums.org/showpost.php?p=407656&postcount=1](http://www.ubuntuforums.org/showpost.php?p=407656&postcount=1))
, you must use the nvidia driver provided by synaptic (see method 1 in [http://ubuntuforums.org/showpost.php?p=406726&postcount=1)](http://ubuntuforums.org/showpost.php?p=406726&postcount=1)).

2 - If you was using one of the latests nvidia's drivers (like 8174 or 8178), please correct the symlinks in /usr/lib after you install the driver using the method 1 above. I dont know why, but even if you do a sh NVIDIAxxx.run --uninstall it wont remove some libs and symlinks from /usr/lib. So after you install the driver from synaptic, you must go to /usr/lib and search for libGL*, correct the symlinks pointing to the 7667 version libs and then delete the 817* version libs. 

3 - After you get the nvidia driver working from synaptic, you can go to ([http://www.ubuntuforums.org/showpost.php?p=407656&postcount=1](http://www.ubuntuforums.org/showpost.php?p=407656&postcount=1)) and install the webcam driver.

Thats it. 

UBUNTU ROCKS!!!! :p

---

