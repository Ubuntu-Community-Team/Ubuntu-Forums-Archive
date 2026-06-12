---
title: "How to get the bluetooth working on my dell inspiron 1525"
date: 2011-07-18
forum: Hardware
---

### Post by arunharidas on 2011-07-18
Hello,

I am using a dell inspiron 1525 laptop and ubuntu 11.04. I am a beginner i dont know how to connect the inbuilt bluetooth. In the task bar there is a bluetooth icon and a 'x' mark on it and also i dont think my wifi also working i couldnt connect to wifi when i tried once. I have read many posts and couldnt find a solution. Please help me

```
sudo dellWirelessCtl --sw_bt 1 --bt 1 
Set runtime settings for Bluetooth

Set runtime switch settings for Bluetooth

Radio Status for Bluetooth:
	Bluetooth enabled at boot
	Bluetooth supported
	Bluetooth enabled
	Bluetooth installed
	Bluetooth controlled by wireless switch at boot
	Bluetooth runtime switch control currently enabled
	Status Code: 0

```

---

### Post by arunharidas on 2011-09-04
Hi friends,
finally I got the bluetooth working!!! ... i just found the solution from this thread
[http://ubuntuforums.org/archive/index.php/t-1653435.html](http://ubuntuforums.org/archive/index.php/t-1653435.html) ...
I tried it on vista through virtual box, when i installed the driver which said by **Xanko** on vista through virtual box suddenly the bluetooth light began to glow and started working

---

