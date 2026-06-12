---
title: "Touchpad problem"
date: 2009-04-10
forum: Hardware
---

### Post by sdd231163 on 2009-04-10
I have a Medion E1210 (which I believe is a rebadged MSI Wind) running Ubuntu 8.10.

The problem I have is that on booting the touchpad is not always detected. Sometimes I have to reboot 2 or 3 times in order for it to find it.

As the touchpad is not a removable item of hardware like an external mouse, is it possible to get the computer to simply know it is there all the time?

Or is there a way to make the detection work more reliably?

Thanks.
Stephen.

---

### Post by teaker1s on 2009-04-10
possibly a way to force load it would be to specify the module name in 
/etc/modules
you can see loaded modules by 
```
sudo lsmod
```

if you can see a module appearing and disappearing then
```
sudo gedit /etc/modules
```
add it to bottom of file and save.

If this is not the case- then
```
sudo lspci -v
```

and 
```
lsusb
```


will show what make your touchpad is and allow further investigation

---

