---
title: "Strange problem"
date: 2013-03-26
forum: Hardware
---

### Post by never2far on 2013-03-26
On random time my Laptop (asus u31sd) just froze so i have tried to install a new kernel 3.5.0-26-generic which worked until today when laptop froze for like 2 seconds and then everything was normal except that I have found this in /var/log/syslog:

> 
Mar 26 16:54:40 hostname kernel: [16496.637907] [drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung
Mar 26 16:54:40 hostname kernel: [16496.637911] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
Mar 26 16:54:40 hostname kernel: [16496.641302] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
Mar 26 16:54:40 hostname kernel: [16496.817853] atl1c 0000:05:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
Mar 26 16:54:40 hostname kernel: [16496.925817] atl1c 0000:05:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
Mar 26 16:54:41 hostname kernel: [16498.269383] atl1c 0000:05:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
Mar 26 16:54:41 hostname kernel: [16498.397343] atl1c 0000:05:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.


Links used to try the new kernel are:
[http://askubuntu.com/questions/257617/how-can-i-upgrade-the-ubuntu-12-04-2-kernel-to-3-5-0-23](http://askubuntu.com/questions/257617/how-can-i-upgrade-the-ubuntu-12-04-2-kernel-to-3-5-0-23)
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

Using those links I managed to install the kernel but not xserver-xorg-lts-quantal . When i try to install it i get this error and I can't work it out:

```

~$ sudo apt-get install xserver-xorg-lts-quantal 
[sudo] password for ionut: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gvfs : Depends: gvfs-daemons (>= 1.12.1-0ubuntu1.1)
        Depends: gvfs-daemons (< 1.12.1-0ubuntu1.1.1~)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.


```

Thank you for any feature advice :)

---

### Post by mgu on 2013-03-27
Hello,

No advice, but you are not alone :( ...same problem for me with kernel 3.5.0-26 on my laptop - Asus N55SF - Ubuntu 12.10 64 :
 > Mar 27 12:26:53 mat-N55SF kernel: [ 2939.011220] [drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung
Mar 27 12:26:53 mat-N55SF kernel: [ 2939.011716] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
Mar 27 12:26:53 mat-N55SF kernel: [ 2939.246959] atl1c 0000:05:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
Mar 27 12:26:53 mat-N55SF kernel: [ 2939.334861] atl1c 0000:05:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
Mar 27 12:26:54 mat-N55SF kernel: [ 2940.265833] atl1c 0000:05:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
Mar 27 12:26:54 mat-N55SF kernel: [ 2940.353737] atl1c 0000:05:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.

Related bug : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1093650](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1093650)
Related post: [http://ubuntuforums.org/showthread.php?t=2127997](http://ubuntuforums.org/showthread.php?t=2127997)
a+

---

### Post by never2far on 2013-04-01
Thank you, 

I'll watch those bug reports

---

