---
title: "bcmwl-kernel-source"
date: 2010-02-19
forum: Hardware
---

### Post by kr651129 on 2010-02-19
Ubuntu 9.10 x32
Dell Inspiron 1545

So to get my wifi card working I needed to do

```
sudo apt-get install bcmwl-kernel-source
```

but the problem is when I run my Ubuntu system updates something happens to this driver and it wont work for me even if I uninstall and reinstall.  I then have to reinstall my whole Ubuntu system.

Has anyone else had this problem?

---

### Post by IcarusR on 2010-02-20
It sounds like updates overwrite your kernel sources & you nolonger have driver for wifi.
It is possible to prevent a package from ever updating. Not so sure I would want to do this with anything to do with kernel as there are frequent security updates.

Google search for "holding package ubuntu" gives a load of sites with info on holding package updates.

---

### Post by Ayuthia on 2010-02-20
When this happens, you might check to see what wireless modules are loaded:
Item 1:
```
lsmod|grep -e b4 -e ssb -e wl
```
If you see the wl module loaded and any combination of b43, b44, or ssb it could mean that one of those modules loaded before the wl module.  The b43/b44 and ssb modules are the open source drivers for the Broadcom cards.  The b44 driver is used for the Broadcom 44xx series wired ethernet cards.  The ssb module (which is required for the b43 and b44 cards) cannot be loaded before using wireless drivers like ndiswrapper or wl (The proprietary version for the wireless Broadcom cards).  When troubleshooting the wireless card and you see b43/b44/ssb loaded into the system (via lsmod) it is best to try removing those modules along with the wl module and reload them in the correct order.  For me, I don't like to load additional kernel modules when they are not necessary so I will check to see if I have that version of the Broadcom wired card and reload it if I do have it.  However, if you do not care that the module is loaded you can just do Option 2a without checking to see if the wired card does exist (It should not hurt anything).

Item 2:
If this might be the case, you will need to check and see if you have a Broadcom 44xx series wired ethernet card (they can cause conflicts with the wl module):

Option 2a:
```
lshw -C network
```
If you do have that model wired card, try the following:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo modprobe b44
sudo iwlist scan
```

Option 2b:
If you don't have that wired card model, try:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo iwlist scan
```

If it produces wireless sites, then we found the problem.  Just let us know if it is the problem and we can then make the necessary corrections to your system so that it loads things correctly.  I was thinking that Ubuntu has this issue resolved in Karmic because I have not seen as many of these issues lately, but I could be wrong.

Item 3:
However if nothing shows up in the lsmod command above, then you should check and see if the wl module exists.  The modprobe -l command will check through the /lib/modules folders to see if the kernel module exists:
```
modprobe -l wl
```
If it shows up, then you can try the modprobe commands listed above in item 2.  

Item 4:
If it does not, the next thing to try is to see if the system built the kernel module but for some reason, the kernel module library has not been updated.  We can update it by doing the following and then checking to see if the module is now found:
```
sudo depmod -a
modprobe -l wl
```

If the wl module appears, you can load it by using the modprobe commands listed in Item 2 or you can restart and things should be fine after that.

Item 5:
If it does not show up at all we can then check and see if the system had problems building the kernel module.  Starting in Karmic, Ubuntu chose to have this kernel module compiled on the your computer instead of supplying it pre-built.  They are now using an application called dkms.  You can check and see if the kernel module compile was attempted by checking:
```
ls /var/lib/dkms/bcmwl/
```

Item 5b:
There should be some version number folders in there.  You will need to go into the most recent version:
```
ls /var/lib/dkms/bcmwl/version-number/$(uname -r)/$(uname -m)/module/
```
Replace version-number with the actual version number.

If there is no wl.ko file there, then dkms had some kind of problem building the kernel module.  You can then try to manually build the module using dkms to see what is happening.  If you need help with this, let us know.

I gave you a few options to try because I was not for sure if you wanted to try and figure out what is happening.  Other options that might be easier is to uninstall the bcmwl-kernel-source and build it manually using the Readme.txt file from the [Broadcom site]("http://www.broadcom.com/support/802.11/linux_sta.php").

Hope that helps.

---

### Post by kr651129 on 2010-02-21
IcarusR
I'm thinking the same thing you are, when I run my update manger I can select which updates I want or don't.  I make sure kernel updates are not selected but you are correct I want to be able to have the latest kernel.

Ayuthia
I know you laid out those instructions fairly well and I'm not a n00b but I'm also not an expert, would you mind explaining a little more on those instructions?

---

### Post by Ayuthia on 2010-02-21
> **kr651129 said:**
> 
Ayuthia
I know you laid out those instructions fairly well and I'm not a n00b but I'm also not an expert, would you mind explaining a little more on those instructions?

I have tried to clean it up a little.  If you are still confused about an item, please let me know which item it is and I can try to help clarify it for you.  

These are the steps I usually take when I try to figure out what is happening.  I have not encountered your scenario with my Broadcom card so I am not for sure what exactly is causing your problem.  That is why I gave you several steps to check.  It seems that Ubuntu has gotten better with getting this to work, but there are still some issues that will come up for one reason or another.

---

