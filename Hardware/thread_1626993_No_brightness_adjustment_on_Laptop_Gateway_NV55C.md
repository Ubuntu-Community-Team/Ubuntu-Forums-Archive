---
title: "No brightness adjustment on Laptop Gateway NV55C"
date: 2010-11-20
forum: Hardware
---

### Post by tzicatl on 2010-11-20
Hi all,

I got a hold to a brand new Gateway NV55C laptop. Brightness adjustment is not available. When pressing the brightness keys GNOME displays the fancy indicators but there is no brightness adjustment. 

I tryied to modify brightness manually, but i got no luck. Here's what I did:

```
# cd /proc/acpi/video/GFX0/
root@hormiga-vaca:/proc/acpi/video/GFX0# ls -l
total 0
dr-xr-xr-x 2 root root 0 2010-11-20 21:50 DD01
dr-xr-xr-x 2 root root 0 2010-11-20 21:50 DD02
dr-xr-xr-x 2 root root 0 2010-11-20 21:15 DD03
dr-xr-xr-x 2 root root 0 2010-11-20 21:50 DD04
dr-xr-xr-x 2 root root 0 2010-11-20 21:50 DD05
dr-xr-xr-x 2 root root 0 2010-11-20 21:50 DD06
dr-xr-xr-x 2 root root 0 2010-11-20 21:50 DD07
dr-xr-xr-x 2 root root 0 2010-11-20 21:50 DD08
-rw-r--r-- 1 root root 0 2010-11-20 21:50 DOS
-r--r--r-- 1 root root 0 2010-11-20 21:50 info
-rw-r--r-- 1 root root 0 2010-11-20 21:50 POST
-r--r--r-- 1 root root 0 2010-11-20 21:50 POST_info
-r--r--r-- 1 root root 0 2010-11-20 21:50 ROM
root@hormiga-vaca:/proc/acpi/video/GFX0# cat DD01/brightness 
<not supported>
root@hormiga-vaca:/proc/acpi/video/GFX0# cat DD02/brightness 
<not supported>
root@hormiga-vaca:/proc/acpi/video/GFX0# cat DD03/brightness 
levels:  10 20 30 40 50 60 70 80 90 100
current: 100
root@hormiga-vaca:/proc/acpi/video/GFX0# echo "10" > DD03/brightness 
root@hormiga-vaca:/proc/acpi/video/GFX0# #Brightness does not change
root@hormiga-vaca:/proc/acpi/video/GFX0# cat DD04/brightness 
<not supported>
root@hormiga-vaca:/proc/acpi/video/GFX0# cat DD05/brightness 
<not supported>
root@hormiga-vaca:/proc/acpi/video/GFX0# cat DD06/brightness 
<not supported>
root@hormiga-vaca:/proc/acpi/video/GFX0# cat DD07/brightness 
<not supported>
root@hormiga-vaca:/proc/acpi/video/GFX0# cat DD08/brightness 
<not supported>
root@hormiga-vaca:/proc/acpi/video/GFX0# 

```

All I know about the videocard is that is an Intel videocard, but don't know the model. lspci output is:

```
# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

```

CPU is:
```
# cat /proc/cpuinfo | grep "model name" | tail -n 1
model name	: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
```

Kernel is:
```
# uname -a
Linux hormiga-vaca 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux
```

And Ubuntu version is:
```
# cat /etc/debian_version 
squeeze/sid
root@hormiga-vaca:/proc/acpi/video/GFX0# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

```

Is this a bug? Is this fixable? 

I can provide more information if needed.

---

