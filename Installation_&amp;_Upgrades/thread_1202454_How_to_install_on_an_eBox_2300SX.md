---
title: "How to install on an eBox 2300SX"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by tra4d on 2009-07-02
This is a how to for installing etch on an eBox 2300SX (no math coprocessor).  I am by no means an expert but since I had trouble finding info on this and DMP provides a not very user-friendly linux version I thought I would post.

This was done with Debian Etch but could easily be adapted for Ubuntu (which is what I will be trying in the near future).

What you will need:
1. eBox 2300SX
2. USB CD or DVD drive
3. USB flash drive (optional - but will prevent you from having to burn files onto a CD/DVD)

Steps:
1.Change bios to boot from USB first and install distro by typing in the following at the boot prompt:
 ```
Press F1 for Help, or ENTER to boot: linux pnpbios=off 
```
(This will prevent the kernel panic/errors when trying to boot) 

2.Nothing too special needs to be done, however the install process will not find a network card since the drivers are not included in the kernel/distro.  Just select “no ether net card” when prompted.  Note, you will also need to skip the configuration of the network mirror since you will not be able to connect to the net.  The same for the package manger.

NOTE: if the process fails (usually on the grub install) just try again.  I have had it happen where it fails, and you do the exact same thing next time and it works.  

3.When the install steps have completed, restart the system as prompted (remember to take the CD/DVD out of the drive).

4.Put the CD/DVD back into the drive

5.Install the linux kernel headers:
```
 # apt-get install linux-headers-`uname -r` 
```

6.Install packages needed for for compiling/etc.:
 ```
# apt-get install make patch gcc build-essential 
```

7.Download the t6040 driver source code from [http://www.compactpc.com.tw/drivers/ebox-2300SX/r6040.tar.gz](http://www.compactpc.com.tw/drivers/ebox-2300SX/r6040.tar.gz)

8.Next, put the r6040 ethernet driver source onto a USB stick and insert the stick into the 2300SX

9.Mount the drive, something like:
 ```
# mount /dev/sda1 /mnt
```

10.Copy the source somewhere like:
```
 # cp /mnt/r6040.tar.gz /home/me/ 
```

11.Untar the file:
 ```
# tar xvfz r6040.tar.gz
``` 

12.Move the extracted folder to a source folder:
 ```
# mv r6040/ /usr/src/
```

13.Change to this new directory:
 ```
# cd /usr/src/r6040
``` 

14.Now load the mii module (which the r6040 needs to compile):
```
 # insmod /lib/modules/`uname -r`/kernel/drivers/net/mii.ko
``` 

15.Compile the drivers according to the README file:
```
 # make -f Makefile-2.6 KDIR=/usr/src/linux-headers-`uname -r`
``` 

16.To test that this module works, run (insert) it:
```
 # insmod r6040.ko 
```

17.Copy your new driver to the approapriate folder:
 ```
# cp r6040.ko /lib/modules/`uname -r`/kernel/drivers/net/ 
```

18.Generate dependency file(s) for module by running depmod:
```
 # depmod -a 
```

19.Setup your network card (in this case with a static IP):
```
 # vi /etc/network/interfaces 
```
Add the following:
  auto eth0
  iface eth0 inet static
  address 192.168.1.5
  gateway 192.168.1.1
  netmask 255.255.255.0
  network 192.168.1.0
  broadcast 192.168.1.255

20.Setup DNS:
	```
 # echo “nameserver 4.2.2.1” > /etc/resolv.conf 
```

21.Restart networking:
```
 # /etc/init.d/networking restart 
```

22.Test/show settings:
```
 # ifconfig 
```
This should show the device (eth0) as active w/ all settings.

23.Test to see if you can get to the net by ping, etc.:
```
 # ping google.com 
```

24.To make your module start automatically at boot, add the following 2 lines to /etc/modules:
```
 # vi /etc/modules
``` 
    mii
    r6040

25.Next, you may want to remove or comment out the apt sources for the CD, and uncomment the ones commented out by the installer.  After this, run an update:
```
 # apt-get update 
```

26.Now you should be able to install any additional software you need and be able to get onto the net.

Steps below are optional, but I will include them.

27. Disable IPV6 
```
 # vi /etc/modprobe.d/aliases  
```
change:
alias net-pf-10 ipv6
to:
alias net-pf-10 off
and add:
alias ipv6 off

28. Disable GDM.  There are a few ways to do this, but the easiest is this (also allows you to put it back if you want to get a gui going):
```
 # mv /etc/rc2.d/S21gdm /etc/rc2.d/K21gdm 
```

29. Install sysv-rc-conf in order to disable non-essential modules/software to speed up booting:
```
 # apt-get install sysv-rc-conf 
```

Note:  if you use the xfce CD like I did, you will have to put back the online sources for apt:
```
 # vi /etc/apt/sources.lst 
```
(in this file, uncomment out the two lines that the installer commented out with a # sign)
```
 # apt-get update 
```
If you get a pgp key error, check out this post:
[http://en.kioskea.net/faq/sujet-809-debian-apt-get-no-pubkey-gpg-error](http://en.kioskea.net/faq/sujet-809-debian-apt-get-no-pubkey-gpg-error)
Then run:
```
 # apt-get install sysv-rc-conf 
```

---

### Post by waterboy550 on 2011-03-03
I know this is old, but thanks a lot. I used your posted files and boom! Got my ethernet card up and running. Thanks a TON!

---

