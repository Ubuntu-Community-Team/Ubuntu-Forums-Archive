---
title: "Nvidia Gforce 9200GS black screen on login"
date: 2010-05-28
forum: Hardware
---

### Post by eGelor on 2010-05-28
> product: Intel(R) Core(TM)2 Duo CPU     P7450  @ 2.13GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 64 bits


my xorg.conf only works with driver nv in low graphic mode.
:confused:

---

### Post by vandorjw on 2010-05-28
if you have 10.04 remove the xorg.conf file from /etc/X11
then reboot your machine.

that might help, but I am not sure.
Did you install restricted drivers from Nvidia?

---

### Post by eGelor on 2010-05-29
i make a test and install drivers manually.
test with 10.04 recommented drivers.
now i test yours and then an other thread .
[http://ubuntuforums.org/showthread.php?p=8389348#post8389348]("http://ubuntuforums.org/showthread.php?p=8389348#post8389348")

---

### Post by Dougie187 on 2010-05-29
Did you blacklist these modules after you manually installed the nvidia driver? Also, Did you uninstall nouveau from synaptic, along with all nvidia things from synaptic too?

```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```

---

### Post by eGelor on 2010-05-29
i make the blacklist 
nouveau=xserver-xorg-video-nouveau?
remove xserver-xorg-all

install drivers manually . but nothing 
change the grub to nomodeset . nothing 




Please help.

---

### Post by eGelor on 2010-06-13
Can anybody help me to make nvidia work in my ubuntu lucid 
2.6.32.22 generic ??

---

### Post by eGelor on 2011-08-29
My new Xorg file.

---

