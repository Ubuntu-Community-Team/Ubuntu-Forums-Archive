---
title: "Intel UHD 750 Driver"
date: 2021-06-04
forum: Hardware
---

### Post by mawsyh on 2021-06-04
Hi , I recently bought a i5 11600K CPU which has a Intel UHD 750 VGA, but apparently UBUNTU can not automatically install the exact driver.

I searched for the driver manually on Intel and 0.org but no answers.

Is there anyone here that can help me solve this issue ?

---

### Post by Yellow Pasque on 2021-06-04
Try booting with "i915.force_probe=4c8a"
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1905466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1905466)

---

### Post by mawsyh on 2021-06-04
firstly thanks for your concern,
the article solution was to insert "[COLOR=#000000]i915.force_probe=4c8a" to /boot/config/probmode.d directory which I dont have on UBUNTU. I am confused

(also tried making the directory and rebooting, didnt work)

also : [/COLOR]lspci | grep VGA00:02.0 VGA compatible controller: Intel Corporation Device 4c8a (rev 04)

---

### Post by Yellow Pasque on 2021-06-04
> **mawsyh said:**
> the article solution was to insert "i915.force_probe=4c8a" to /boot/config/probmode.d directory which I dont have on UBUNTU. 

I don't see that anywhere in the bug report. I have no idea where you got that.

See: [https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter](https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter)
I'm not sure if gksudo is still around, but the bottom line is that you pick your favorite text editor and start it with root permissions. So, for me
```
sudo vim /etc/default/grub
```

EDIT: Alternatively, you can try creating a file in /etc/modprobe.d/
```
echo "options i915 force_probe=4c8a" | sudo tee -a /etc/modprobe.d/i915.conf
```

---

