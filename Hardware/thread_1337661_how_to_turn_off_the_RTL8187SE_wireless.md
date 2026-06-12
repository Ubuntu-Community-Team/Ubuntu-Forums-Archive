---
title: "how to turn off the RTL8187SE wireless"
date: 2009-11-25
forum: Hardware
---

### Post by nivwiz on 2009-11-25
Hi,
I got a new netbook with the RTL8187SE and kernel 2.6.28
I can't find a way to turn off the wifi.
/sys/class/net/wlan1/device/power/state doesnt exist. only /sys/class/net/wlan1/device/power/wakeup
how can I make it turn off?
Niv

---

### Post by HappyFeet on 2009-11-25
```
sudo /etc/init.d/networking stop
```

---

### Post by nivwiz on 2009-11-25
> **HappyFeet said:**
> ```
sudo /etc/init.d/networking stop
```
wifi led keeps on after this

---

### Post by HappyFeet on 2009-11-25
> **nivwiz said:**
> wifi led keeps on after this

Usually there is a key combo Fn+? to turn it off.

---

### Post by nivwiz on 2009-11-25
right , as this doesnt work, I seek to find a command to do the job.
I will then ask how to assign this fn+F2 key combination the power down of the wifi script.

---

### Post by techfreak on 2009-11-27
I too have been looking for the solution to turn off the wifi radio power to extend battery life when Wifi is not needed.

Thanks for any help!:D

sudo iwconfig wlan0 power off

doesn't work.

---

### Post by Yellow Pasque on 2009-11-28
Unload the kernel module?:
```
sudo modprobe -r <modulename>
```
..where <modulename> is probably rtl8187se

---

