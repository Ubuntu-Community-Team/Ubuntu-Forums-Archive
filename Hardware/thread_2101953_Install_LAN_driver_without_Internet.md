---
title: "Install LAN driver without Internet"
date: 2013-01-05
forum: Hardware
---

### Post by islan on 2013-01-05
Hi.

I have a new Gigabyte GA-Z77X-D3H motherboard which has an Atheros GbE LAN chip.  Apparently this is a new chip that is not currently included in Ubuntu 12.10 by default.

I was trying to follow the instructions [here]("http://ubuntuforums.org/showthread.php?p=12206393") and [here]("http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller") to install the alx driver.  I have compat-wireless-3.5.1-1-snpc.tar.bz2 successfully downloaded from a different computer and sitting on a USB drive.  However, I don't know how to perform this part without internet:

```
sudo apt-get install linux-headers-generic build-essential

or

sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r`
```

In case it's important, I had to install Ubuntu via USB since the computer does not currently have a CD/DVD drive.

Thanks in advance!  ):P

---

### Post by islan on 2013-01-06
Okay, it looks like those steps aren't necessary, and skipping them and just running the scripts worked fine.

---

### Post by jordii84 on 2013-03-11
Hi, i have exactly the same problem, but i don't understand your last post. What scripts must we run to make it work?

Regards,

---

