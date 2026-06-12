---
title: "2X GPU (GTX 650 no SLI) 4 monitors setup"
date: 2013-01-11
forum: Hardware
---

### Post by debian3 on 2013-01-11
Hi,

I try to setup my 4 monitors (all the same monitor and same resolution) with 2 gpu GTX 650. I have installed the Nvidia driver, with 2 screen no problems, but I'm unable to get the second card to work without xinerama (with it there is no 3D and there is lot of UI glitch and the performance are not really good).

I have made lot of search, but for example if I use 2X twinview, I get 2 screen that works normally and 2 screen that are white. I did some test with ubuntu 12.04 and 12.10. Nvidia driver 304, 310 and 313 and none work. I use Unity.

Any idea?

---

### Post by Gandalf6596 on 2013-01-11
[SIZE=3]I[/SIZE] also have two GeForce GTX 650
You say you downloaded the  Nvidia driver.
Would you place tell me how you did it?


I've been trying and trying and trying.
Nothing worked.  I'm running on Ubuntu 12.10.

I've tried to modify my personal data etc, but apparently I haven't posted enough to be granted that permission.

Thanks

---

### Post by debian3 on 2013-01-11
It was a bit harder on 12.10 then 12.04. Currently I run in 12.04 (I prefer LTS) but on 12.10 here how:

First to install the driver:
#add-apt-repository ppa:ubuntu-x-swat/x-updates
#apt-get install nvidia-current-updates

Check your kernel version:
#uname -r 

It will give you your kernel version (like 3.2.0-35-generic)
Run:
#apt-get install 3.2.0-35-generic

So basically it will recompile with the driver and after a reboot it will work and the menu and everything should display.

---

### Post by Gandalf6596 on 2013-01-11
Thanks for the response, however here are the results...

gandalf@WhiteCastle:~$ **sudo add-apt-repository ppa:ubuntu-x-swat/x-updates**
[sudo] password for gandalf: 
You are about to add the following PPA to your system:
 Updated versions of X.org drivers, libraries, etc. for Ubuntu.

This PPA is for stable upstream releases of X.org components.  If you're looking for something even more bleeding-edge, please see the xorg-edgers PPA.

While Ubuntu does not "officially/formally" support these packages, if you discover problems when installing these debs please feel free to report bugs to launchpad.  However, please make sure to clearly state that you are running packages from this PPA so we know the fixes need to come here.

If you are upgrading from one release to another with this PPA activated, please install the ppa-purge package and use it to downgrade everything in here beforehand. sudo ppa-purge ppa:ubuntu-x-swat/x-updates will do it.

[Directions for packaging drivers can be seen at [https://wiki.ubuntu.com/X/DriverBuilding]](https://wiki.ubuntu.com/X/DriverBuilding])
 More info: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp9am_6b/secring.gpg' created
gpg: keyring `/tmp/tmp9am_6b/pubring.gpg' created
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp9am_6b/trustdb.gpg: trustdb created
gpg: key AF1CDFA9: public key "Launchpad PPA for Ubuntu-X" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
gandalf@WhiteCastle:~$** sudo apt-get install nvidia-current-updates**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-current-updates : Depends: dkms but it is not installable
                          Depends: linux-headers-generic but it is not installable or
                                   linux-headers
                          Recommends: nvidia-settings-updates
E: Unable to correct problems, you have held broken packages.
gandalf@WhiteCastle:~$ **sudo apt-get install 3.5.0-21-generic**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-image-extra-3.5.0-21-generic' for regex '3.5.0-21-generic'
Note, selecting 'linux-image-3.5.0-21-generic' for regex '3.5.0-21-generic'
linux-image-extra-3.5.0-21-generic is already the newest version.
linux-image-3.5.0-21-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

_____________________________________________________________________

The only change I had to make was running the commands as sudo.
As you can see the first command worked but the second one did not.
I tried the third install anyway, but it the response just confused me.
Any ideas what went wrong?

Thanks

---

### Post by debian3 on 2013-01-11
yes, 2 things, when you add-apt-repository, you need to do apt-get update after.
Last thing, you are missing some dependency, try 
apt-get install linux-headers-generic

Then retry to install nvidia

---

### Post by Gandalf6596 on 2013-01-11
The first part want well, but then ...

gandalf@WhiteCastle:~$ **sudo apt-get install linux-headers-generic**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'linux-headers-generic' has no installation candidate
gandalf@WhiteCastle:~$** sudo apt-get install nvidia-current-updates**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-current-updates : Depends: dkms but it is not installable
                          Depends: linux-headers-generic but it is not installable or
                                   linux-headers
                          Recommends: nvidia-settings-updates
E: Unable to correct problems, you have held broken packages.

---

