---
title: "ubuntu 10.04 sometimes crashed in startup"
date: 2010-09-18
forum: Hardware
---

### Post by alirajabi on 2010-09-18
I have a problem in ubuntu 10.04 with Dell xps m1530 (And my friends have it) 
ubuntu 10.04 sometimes crashed in startup before gdm 
I searched and I found out that vga driver should be cause of this problem 
I checked all method, for example : 
Intall driver from hardware driver. 
OR
Remove Nouveau then install nvidia driver from hardware driver
OR
insert 
```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv 

```
Into 
blacklist.conf 
```

sudo gedit /etc/modprobe.d/blacklist.conf 
sudo modprobe nvidia-current
sudo lsmod | grep -i nvidia

```

 And another methods , I checked all but this problem didn't solve .
Please Help me for inssue 

Thanks
 
I Used they guides and all things that found in internet:
```
https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia
OR
http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html
And ...

```

---

### Post by alirajabi on 2010-09-18
Are u there ?:D

---

### Post by saeid on 2010-09-18
Same problem :(
Ubuntu 10.04.01
nvidia-current 195.36.24-0ubuntu1~10.04

---

### Post by alirajabi on 2010-09-19
you can help we ?
All go sleep!!!

---

