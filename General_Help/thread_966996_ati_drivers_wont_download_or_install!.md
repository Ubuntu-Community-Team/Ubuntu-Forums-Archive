---
title: "ati drivers wont download or install?!"
date: 2008-11-01
forum: General Help
---

### Post by Murlis on 2008-11-01
when i click enable in 'hardware drivers', it goes into downloading and stays at 0% downloading until it just disappears (Using 8.10 and ATI Radeon Xpress 1250)

---

### Post by taurus on 2008-11-01
I suppose the network connect is working on your machine.  Also, what does your /etc/apt/sources.list look like?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Cl0ud9 on 2008-11-01
> **Murlis said:**
> when i click enable in 'hardware drivers', it goes into downloading and stays at 0% downloading until it just disappears (Using 8.10 and ATI Radeon Xpress 1250)

I had this same problem after upgrading. I then used envyng to install the ati fglrx driver and didn't run into any problems.

---

### Post by Murlis on 2008-11-01
> **taurus said:**
> I suppose the network connect is working on your machine.  Also, what does your /etc/apt/sources.list look like?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

this is what the terminal says:
thomas@samsung-r20-ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb-src [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid main restricted
deb-src [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid-updates main restricted
deb-src [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid universe
deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid multiverse
deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid-security main restricted
deb-src [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid-security universe
deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid-security multiverse
deb [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid-proposed restricted main multiverse universe
deb-src [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/) intrepid-proposed restricted main multiverse universe #Added by software-properties
thomas@samsung-r20-ubuntu:~$


and cl0ud9, your suggestion comes up with a driver but- 
3
 +---------------------------------------------------------------------------+
 | Number | Candidate Version | Installed Version | Compatible | Recommended |
 |---------------------------------------------------------------------------|
 | 0      | 8.543-0ubuntu4    | -                 | +          | +           |
 +---------------------------------------------------------------------------+
Please select the number corresponding to the desired driver and press ENTER 
(or type another number and press Enter to go back to the previous menu): 
0

Dowloading the packages...
[===================================57.1%====>                                 ]result could not be parsed
Error in function pulse
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/Envy/packagemanager.py", line 75, in pulse
    self.newObject.updateUi(percent)
  File "interface.py", line 65, in updateUi
    numHashes = int(round(numHashes))
TypeError: an integer is required
/usr/bin/envyng: line 4:  6254 Segmentation fault      sudo python interface.py
root@samsung-r20-ubuntu:/home/thomas#

---

### Post by HuaiDan on 2008-12-14
Hello all,

Has there been any follow up on this? I get the exact same problem, right down to the 57.1% crash point, on Intrepid 8.10 running on core 2 with both an NVidia 7300 gt and an 8600 gt.

I have a thread open on launchpad for an identical issue where one user solved by reinstalling python.  I haven't tried that to any success. Details can be found [here.]("https://bugs.launchpad.net/ubuntu/+source/envyng-core/+bug/287367")
What would help me are instructions for removing and reinstalling python, but I can't seem to get my GUI back after running "sudo apt-get autoremove python" and then "sudo apt-get install python". If anyone can tell me how to do this, you have my eternal gratitude.
Thanks,
David



> **Murlis said:**
> 
 +---------------------------------------------------------------------------+
 | Number | Candidate Version | Installed Version | Compatible | Recommended |
 |---------------------------------------------------------------------------|
 | 0      | 8.543-0ubuntu4    | -                 | +          | +           |
 +---------------------------------------------------------------------------+
Please select the number corresponding to the desired driver and press ENTER 
(or type another number and press Enter to go back to the previous menu): 
0

Dowloading the packages...
[===================================57.1%====>                                 ]result could not be parsed
Error in function pulse
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/Envy/packagemanager.py", line 75, in pulse
    self.newObject.updateUi(percent)
  File "interface.py", line 65, in updateUi
    numHashes = int(round(numHashes))
TypeError: an integer is required
/usr/bin/envyng: line 4:  6254 Segmentation fault      sudo python interface.py
root@samsung-r20-ubuntu:/home/thomas#

---

### Post by HuaiDan on 2008-12-15
Disregard. Success!

What worked for me was shutting down gdm and running the download from Nvidia website 
sh NVIDIA-Linux-x86_64-177.82-pkg2.run

The trick is to select 'no' for download kernel, then select 'yes' for build kernel, then yes the rest of the way through.  Finally, restart gdm, reboot, 



That's how my story went.

---

