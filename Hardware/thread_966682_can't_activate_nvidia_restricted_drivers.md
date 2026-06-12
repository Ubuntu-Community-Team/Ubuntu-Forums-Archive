---
title: "can't activate nvidia restricted drivers"
date: 2008-11-01
forum: Hardware
---

### Post by Rurushu on 2008-11-01
System --> Hardware Drivers

I am trying to enable *nvidia accelerated graphics driver (version 177)*

I have NVIDIA GeForce Go 7400; using ubuntu 8.10

The driver can't be activated!!

I tried to isntall nvidia-glx-177

> sudo apt-get install nvidia-glx-177
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-glx-177


Universe repos are enabled!

Any ideas?

---

### Post by Rurushu on 2008-11-01
By the way, when I try to reload my sources list I get this error:

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://ae.archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://ae.archive.ubuntu.com/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by cmp1988 on 2008-11-01
I can't activate my Nvidia restricted drivers as well.  Just stays at 0% for about 5 mins, then the little dialog box closes back to the previous window.  The driver choices are greyed out, but doesn't do anything.

---

### Post by kogos on 2008-11-01
i got the same problem... waiting to download the driver, gets stuck at 0% and then an error window with nothing in it shows up... Is it possible we got too many ppl downloading it and servers are overloaded??? 

and btw, i always get very low speed on anything i try to download from ubuntu servers... i'm downloading restricted format package now with 2kb/sec, and it already failed 3 times cause the server was not responding... and i know that this in not a DSL provider issue for sure...

---

### Post by kogos on 2008-11-03
I managed to fix this... As it seems, the server in my country is down (Greece), or the nvidia driver is not even there... I switched the server in "Software Sources" from "Server in Greece" (gr.archive.ubuntu.com) to main server, and it downloaded and installed with no problem. 

Let me know if that fixes your problem too (i think it will for both of you). 

For new users, to do this go to System>Administration>Software Sources... and on the first tab change the "Download from" setting. :)

---

### Post by jlespinosa on 2008-11-04
I had the same problem, as Kogos said I just changed the server location and started to download the drivers. Thank you, it worked

---

### Post by jward3010 on 2009-03-27
Oddly enough, the same is apparent in Jaunty 9.04 (alpha 6). I'm trying to download nvidia driver version 180 and rather than even getting the progress bar, nothing comes up. I changed to "Main Server" in sources and suddenly its downloading. 

It's probably down to it being a brand new driver release and it wont be updated to all mirrors for a while, hopefully only a couple days delay, theres a good chance earlier versions will work (like 173, 96 etc.) because they would be on the mirror.

---

### Post by dof on 2009-04-05
> **jward3010 said:**
> Oddly enough, the same is apparent in Jaunty 9.04 (alpha 6). I'm trying to download nvidia driver version 180 and rather than even getting the progress bar, nothing comes up. I changed to "Main Server" in sources and suddenly its downloading. 

It's probably down to it being a brand new driver release and it wont be updated to all mirrors for a while, hopefully only a couple days delay, theres a good chance earlier versions will work (like 173, 96 etc.) because they would be on the mirror.

Same here, but "Main Server" it's so slow. I've test my internet connection (comcast) it works okay and I've tested this repository in different days, it's the same for me. I've tested also the default for US, still slow...

---

### Post by millerjustin82 on 2009-04-08
I've been having the same issue with my 7950 gtx, I am totally new to ubuntu, and all linux stuff, I'll try changing the download mirror and see if that works.

---

### Post by dof on 2009-04-12
It doesn't work for me, i have to run with generic drivers and it sucks. I've tried to enable the drivers this morning, but no luck.
Here is the jockey.log. If anybody has an idea what need to be done please let me know.


2009-04-12 08:57:01,649 DEBUG: Installing package: nvidia-glx-180
2009-04-12 08:57:18,084 DEBUG: install progress statusChange nvidia-glx-173 0.000000
2009-04-12 08:57:18,086 DEBUG: install progress statusChange nvidia-glx-173 4.761900
2009-04-12 08:57:18,107 DEBUG: install progress statusChange nvidia-glx-173 9.523810
2009-04-12 08:57:18,782 DEBUG: install progress statusChange nvidia-glx-173 14.285700
2009-04-12 08:57:18,816 DEBUG: install progress statusChange nvidia-173-kernel-source 14.285700
2009-04-12 08:57:18,818 DEBUG: install progress statusChange nvidia-173-kernel-source 19.047600
2009-04-12 08:57:23,406 DEBUG: install progress statusChange nvidia-173-kernel-source 23.809500
2009-04-12 08:57:23,491 DEBUG: install progress statusChange nvidia-173-kernel-source 28.571400
2009-04-12 08:57:23,507 DEBUG: install progress statusChange man-db 28.571400
2009-04-12 08:57:23,606 DEBUG: install progress statusChange libc6 28.571400
2009-04-12 08:57:24,612 DEBUG: install progress statusChange nvidia-180-kernel-source 28.571400
2009-04-12 08:57:24,612 DEBUG: install progress statusChange nvidia-180-kernel-source 33.333300
2009-04-12 08:57:24,910 DEBUG: install progress statusChange nvidia-180-kernel-source 38.095200
2009-04-12 08:57:24,914 DEBUG: install progress statusChange nvidia-180-kernel-source 42.857100
2009-04-12 08:57:25,123 DEBUG: install progress statusChange nvidia-180-libvdpau 42.857100
2009-04-12 08:57:25,124 DEBUG: install progress statusChange nvidia-180-libvdpau 47.619000
2009-04-12 08:57:25,227 DEBUG: install progress statusChange nvidia-180-libvdpau 52.381000
2009-04-12 08:57:25,231 DEBUG: install progress statusChange nvidia-180-libvdpau 57.142900
2009-04-12 08:57:25,271 DEBUG: install progress statusChange nvidia-glx-180 57.142900
2009-04-12 08:57:25,272 DEBUG: install progress statusChange nvidia-glx-180 61.904800
2009-04-12 08:57:30,003 DEBUG: install progress statusChange nvidia-glx-180 66.666700
2009-04-12 08:57:30,013 DEBUG: install progress statusChange nvidia-glx-180 71.428600
2009-04-12 08:57:30,023 DEBUG: install progress statusChange man-db 71.428600
2009-04-12 08:57:30,955 DEBUG: install progress statusChange nvidia-180-kernel-source 71.428600
2009-04-12 08:57:30,988 DEBUG: install progress statusChange nvidia-180-kernel-source 76.190500
2009-04-12 08:57:31,606 DEBUG: install progress statusChange nvidia-180-kernel-source 80.952400
2009-04-12 08:57:31,614 DEBUG: install progress statusChange nvidia-180-libvdpau 80.952400
2009-04-12 08:57:31,619 DEBUG: install progress statusChange nvidia-180-libvdpau 85.714300
2009-04-12 08:57:31,634 DEBUG: install progress statusChange nvidia-180-libvdpau 90.476200
2009-04-12 08:57:31,639 DEBUG: install progress statusChange nvidia-glx-180 90.476200
2009-04-12 08:57:31,642 DEBUG: install progress statusChange nvidia-glx-180 95.238100
2009-04-12 08:57:31,970 DEBUG: install progress statusChange nvidia-glx-180 100.000000
2009-04-12 08:57:31,974 DEBUG: install progress statusChange libc6 100.000000
2009-04-12 08:57:32,676 DEBUG: (Reading database ... 138348 files and directories currently installed.)
Removing nvidia-glx-173 ...
Removing nvidia-173-kernel-source ...
Removing all DKMS Modules
Done.
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package nvidia-180-kernel-source.
(Reading database ... 138267 files and directories currently installed.)
Unpacking nvidia-180-kernel-source (from .../nvidia-180-kernel-source_180.44-0ubuntu1_i386.deb) ...
Selecting previously deselected package nvidia-180-libvdpau.
Unpacking nvidia-180-libvdpau (from .../nvidia-180-libvdpau_180.44-0ubuntu1_i386.deb) ...
Selecting previously deselected package nvidia-glx-180.
Unpacking nvidia-glx-180 (from .../nvidia-glx-180_180.44-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-180-kernel-source (180.44-0ubuntu1) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 180.44
Doing initial module build

Error! Your kernel source for kernel 2.6.28-9-generic cannot be found at
/lib/modules/2.6.28-9-generic/build or /lib/modules/2.6.28-9-generic/source.
Installing initial module

Error! Could not locate nvidia.ko for module nvidia in the DKMS tree.
You must run a dkms build for kernel 2.6.28-9-generic (i686) first.
Done.

Setting up nvidia-180-libvdpau (180.44-0ubuntu1) ...

Setting up nvidia-glx-180 (180.44-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

2009-04-12 08:57:32,955 WARNING: modinfo for module nvidia failed: modinfo: could not find module nvidia

2009-04-12 08:57:33,090 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Configured Video Device"\n', '\tDriver\t"nvidia"\n']})

---

### Post by norwoods on 2009-04-12
try running the following in a terminal window and then reinstall drivers:
sudo apt-get install build-essential linux-headers-`uname -r`

---

### Post by dof on 2009-04-12
> **norwoods said:**
> try running the following in a terminal window and then reinstall drivers:
sudo apt-get install build-essential linux-headers-`uname -r`

sudo apt-get install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
Package linux-headers-2.6.28-9-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.28-9-generic has no installation candidate

---

### Post by norwoods on 2009-04-13
> **dof said:**
> sudo apt-get install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
Package linux-headers-2.6.28-9-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.28-9-generic has no installation candidate
where did you get the 2.6.28-9 kernel? if you back down to 2.6.27-11-generic and try to install nvidia drivers i hope your troubles will go away

---

### Post by dof on 2009-04-13
> **norwoods said:**
> where did you get the 2.6.28-9 kernel? if you back down to 2.6.27-11-generic and try to install nvidia drivers i hope your troubles will go away

That's what jaunty uses, i've only ran updates, no different installs.

---

