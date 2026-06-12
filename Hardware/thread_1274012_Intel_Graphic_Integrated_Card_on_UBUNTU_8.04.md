---
title: "Intel Graphic Integrated Card on UBUNTU 8.04"
date: 2009-09-24
forum: Hardware
---

### Post by azsquall on 2009-09-24
H:confused:
I have a Lenovo THINKPAD T61 with Intel Graphic Integrated card 
```

khoa@khoa-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)

```

but look like I cannot enable desktop effects ?

is there any way that i can fully use this video card? i.e right driver?

many thanks!!!!
PS: although i was able to get right resolution, but the quality of image is not really good though ;(

please help

---

### Post by Ravernomina on 2009-09-24
The new Intel Drivers have ben glitchy in Jaunty try this guide and let me know if it fixes it :)

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

If you Need help ill Translate for you (:

Btw Welcome to the forums and Ubuntu Linux :), Welcome to Freedom... Welcome to Linux (:

---

### Post by azsquall on 2009-09-24
Thanks million for the help.
I've been using linux for years, but mostly with server application, not desktop ;) thus, graphic was not a requirement until today ;

my T61 has windows XP pre-installed. I loaded ubuntu 8.04 to have dual boot. Kinda testing things out before migrating to linux ubuntu. So far, it worked for MATLAB, mathematica, LATEX, JAVA, etc etc

I ran into problem by the way :(
before posting this topic, I tried many methods, include adding SKIP_CHECK=yes to compiz_manager. Wondering if it will cause problem for this method.

thanks again
```

khoa@khoa-laptop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79
gpg: requesting key 3E731F79 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error


```
```

khoa@khoa-laptop:~$ sudo apt-get install xserver-xorg-video-intel-2.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xserver-xorg-video-intel-2.4: Depends: libdrm2 (>= 2.3.1) but 2.3.0-4ubuntu1 is to be installed
                                Depends: libpciaccess0 (>= 0.8.0+git20071002) but it is not going to be installed
                                Depends: xserver-xorg-core (>= 2:1.5.99.901) but 2:1.4.1~git20080131-1ubuntu9.2 is to be installed
E: Broken packages


```

---

### Post by azsquall on 2009-09-24
hi there again
STRANGE
i tried  **sudo aptitude install **and this is what i have got

```

khoa@khoa-laptop:~$ sudo aptitude install xserver-xorg-video-intel-2.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  xserver-xorg-video-all xserver-xorg-video-intel-2.4 
The following packages will be automatically REMOVED:
  xserver-xorg-video-i810 xserver-xorg-video-intel 
The following packages will be REMOVED:
  xserver-xorg-video-i810 xserver-xorg-video-intel 
0 packages upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 424kB of archives. After unpacking 119kB will be freed.
The following packages have unmet dependencies:
  xserver-xorg-video-all: Depends: xserver-xorg-video-i810 but it is not installable
  xserver-xorg-video-intel-2.4: Depends: libdrm2 (>= 2.3.1) but 2.3.0-4ubuntu1 is installed.
                                Depends: libpciaccess0 (>= 0.8.0+git20071002) but it is not installable
                                Depends: xserver-xorg-core (>= 2:1.5.99.901) but 2:1.4.1~git20080131-1ubuntu9.2 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
xserver-xorg-video-all

Keep the following packages at their current version:
xserver-xorg-video-intel-2.4 [Not Installed]

Score is -9812

Accept this solution? [Y/n/q/?] y
The following packages will be automatically REMOVED:
  xserver-xorg-video-all xserver-xorg-video-i810 xserver-xorg-video-intel 
The following packages will be REMOVED:
  xserver-xorg-video-all xserver-xorg-video-i810 xserver-xorg-video-intel 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1069kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 119323 files and directories currently installed.)
Removing xserver-xorg-video-all ...
Removing xserver-xorg-video-i810 ...
Removing xserver-xorg-video-intel ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
khoa@khoa-laptop:~$


```

---

