---
title: "T61 Nvidia Drivers... tried it all"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by nuglobe on 2007-10-01
Alright, what am I missing. I have gone through as many drivers and step-by-steps that I can find.


I have a T61 with Nvidia NVS 140M. 

This was my last attempt. 

Killed X -> Uninstalled (wasn't there but I checked) nvidia-glx-new -> sh NVIDIA-Linux-x86-100.14.19-pkg1.run -> Restart X

I have libc-dev and linux-headers-i386 installed.

When I restart it comes up in 640 x 480.

Please be gentle, I'm new.

:confused:

---

### Post by chris_ak on 2007-10-01
Did you run nvidia-xconfig?  and don't forget to modprobe nvidia.

---

### Post by nuglobe on 2007-10-01
Nvidia-xconfig is included in the driver isn't it? It asks you after it installs the drivers. I looked up modprobe and I'm not sure how I would use that in this case?

---

### Post by nuglobe on 2007-10-01
Alright I was able to find out how Modprobe works, and how I should use it for Nvidia. However, it still doesn't work. I have also followed the guide on the Nvidia Linux forums, which means removing restricted drivers (&common).

This is really starting to get under my skin. Any more ideas? 

Thanks.

---

