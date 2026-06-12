---
title: "Problems with installing drivers for 512MB ATI Mobility Radeon(TM) HD 5470 switchable"
date: 2010-12-05
forum: Hardware
---

### Post by yangjiangnan on 2010-12-05
I downloaded  [ATI Catalyst  10.9 Proprietary Linux x86 Display Driver]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-9-x86.x86_64.run") and installed it on my HP Pavilion dv6 i5 64 bit, with Ubuntu 10.10 installed. However, I get the following errors:

jiangnan@jiangnan-PC:~/Downloads$ ./ati-driver-installer-10-9-x86.x86_64.run 
Created directory fglrx-install.eQuJUX
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.771.............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.35-23-generic:; make sure that the version is being
correctly set by --iscurrentdistro

=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.35-23-generic:; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.eQuJUX


Any solutions for the 2 errors?

Many thanks

---

### Post by depeha on 2010-12-06
Don't bother about ati drivers... it's not worth it... I have tried installing ati drivers several times on my Pavilion DV6-3040ec - intel i5 graphics + ati radeon hd 5650, kubuntu 10.10 32bit pae kernel (kubuntu reinstalled each time after installing ati drivers).  All you get is bad 3D performance and unworkable switcheroo.

---

### Post by yangjiangnan on 2010-12-07
After I installed the drivers and restart the computer, I could no longer boot in my Ubuntu system. All I got is "failed to get i915 symbols graphics turbo disabled".  How can I solve this problem and re-enter my Ubuntu?

---

### Post by depeha on 2010-12-08
go to recovery mode (second grub option), log in to terminal as root and remove fglrx

```
apt-get purge fglrx
```

---

### Post by yangjiangnan on 2010-12-08
Thanks!

> **depeha said:**
> go to recovery mode (second grub option), log in to terminal as root and remove fglrx

```
apt-get purge fglrx
```

---

### Post by depeha on 2010-12-09
Let me know if you´ll get working drivers pls...

---

### Post by yangjiangnan on 2011-01-08
> **depeha said:**
> Let me know if you´ll get working drivers pls...

Hi~~
I have tried many times installing ATI driver ati-driver-installer-10-12-x86.x86_64.run on my 64 bit Ubuntu 10.10 with this 5470 graphic card. However, every time when I reboot I only get a black screen. Then I have to remove /etc/X11/xorg.conf to get things back to normal. Why does the driver not work for me? I just wanna get it work.

By default, is my GPU used by Ubuntu 10.10, or is it just wasted? If I could successfully install the driver, will gnome-system-monitor and Xorg use less CPU, and will Win7 in my VirtualBox have better performance?

---

### Post by depeha on 2011-01-12
Don't know why, but it just doesn't work. Maybe 5xxx series is too new :D
Anyway, it uses power in ubuntu even if it´s not in use.
You can turn it off for better battery life:
```
sudo su
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

and chceck, if it works:
```
cat /sys/kernel/debug/vgaswitcheroo/switch
```
(My HP DV6-3040 gets from 45W to around 20W, switcheroo doesn´t support ati drivers)


By default, ubuntu uses Intel graphics, so even if you´ll get working ati drivers, CPU usage will be same.
And about VirtualBox.. I don´t think you´ll get better performance for virtual windows.

---

### Post by yangjiangnan on 2011-01-15
Thanks!
 I hope some day Ubuntu will itself be able to use my GPU......

---

### Post by depeha on 2011-01-17
you can switch to Radeon

```
sudo su
echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch
```

(it will use opensource driver), but it's much slower than integrated intel.

to switch back:
```
echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
```

---

