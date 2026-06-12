---
title: "GUI for listing system hardware like KDE Control Centre"
date: 2009-12-22
forum: Hardware
---

### Post by chandra on 2009-12-22
I am using Kubuntu 9.10 and have long wanted to examine my hardware setup using a GUI similar to the provided by KDE Control Centre in KDE 3.x.y.

I can use the command line tool ```
lshw
``` but I am looking for something that shows memory type, usage etc.

I believe that Ubuntu 9.10 has

```
System -> Administration -> System Monitor -> System
``` that shows something along these lines, though not in as detailed a fashion as the old KDE Control Centre.

Can anyone point me in the right direction to do this please for KDE 4.3.2 in Kubuntu?

Thanks.

---

### Post by chandra on 2009-12-22
Thanks to _sAm_ at

[http://ubuntuforums.org/showpost.php?p=5934304&postcount=3](http://ubuntuforums.org/showpost.php?p=5934304&postcount=3)

```
sudo apt-get install sysinfo hardinfo
``` and invoking the relevant utilities seems to do what I want. The latter package is more hardware-specific.

However, I would still like to ask if anyone knows of a near-replacement for the old KDE Control Centre. The multiplicity of plasma widgets claiming to monitor the hardware in KDE 4.3.2 do not seem an adequate replacement for the old KDE Control Centre.

Thanks.

---

