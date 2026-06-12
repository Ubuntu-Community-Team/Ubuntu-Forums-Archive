---
title: "aptitude trys to retreive the same package from medibuntu multiple times"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by Caysho on 2009-03-19
I did an install of mythbuntu, and got all the updates as of today.
That was all successful.
The following happens when I get packages from medibuntu.
When using the Mythbuntu Control Center GUI, tt looks like the downloads are sometimes going in reverse.
From the commandline, this is what is looks like.

```

root@pvr:~# apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic libvncserver0 rdate localechooser-data libdebconfclient0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libstdc++5
Suggested packages:
  gstreamer0.10-pitfdll
The following NEW packages will be installed:
  libstdc++5 w32codecs
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.3MB/14.6MB of archives.
After this operation, 35.3MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://packages.medibuntu.org intrepid/non-free w32codecs 20071007-0medibuntu3 [14.3MB]
Get:2 http://packages.medibuntu.org intrepid/non-free w32codecs 20071007-0medibuntu3 [14.3MB]                                                    
Get:3 http://packages.medibuntu.org intrepid/non-free w32codecs 20071007-0medibuntu3 [14.3MB]       
1% [3 w32codecs 178000/14.3MB 1%]         20.8kB/s 49710d 6h16min59s^

```

From the GUI, it never finishes (typically takes ~10 minutes, I let it go for much longer)

---

