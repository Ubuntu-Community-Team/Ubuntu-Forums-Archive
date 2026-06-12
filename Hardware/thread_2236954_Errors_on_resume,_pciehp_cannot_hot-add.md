---
title: "Errors on resume, pciehp cannot hot-add"
date: 2014-07-29
forum: Hardware
---

### Post by blurrred on 2014-07-29
Sometimes when I resume my laptop (Asus UL50VT) after closing the lid, I  briefly get a flash of these messages which duplicate themselves on  each resume: 
```

pciehp 0000:00:01.0:pcie04: Device 0000:01:00.0 already exists at 0000:01:00, cannot hot-add
pciehp 0000:00:01.0:pcie04: Cannot add device at 0000:01:00

```
I'm fairly certain that this issue is linked with my nVidia GPU (I'm  using the nvidia drivers that support bumblebee) because after doing  lspci | grep 01:00, I get the following
```

01:00.0 VGA compatible controller: NVIDIA Corporation GT218M [GeForce G210M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)

```
The errors do not appear if I reboot my laptop and refrain from using primusrun or optirun to activate the nVidia GPU, but appear immediately after resuming if I use primusrun or optirun and duplicate themselves every subsequent resume.

---

### Post by martin-stecher on 2014-12-14
Hello
I have the same issue and would like to solve it. I am using ubuntu 14.04 on a Lenovo IBM Z61p.
Thank you for any suggestions.

---

### Post by blurrred on 2015-08-12
One year later and I still cannot fix this.

---

### Post by dino99 on 2015-08-12
your supported driver is : 340
which one is used on your laptop ? Maybe purge it then reinstall the driver; and glance into /etc/rc?.d folders about broken links

[http://www.nvidia.com/download/driverResults.aspx/81760/en-us](http://www.nvidia.com/download/driverResults.aspx/81760/en-us)

---

