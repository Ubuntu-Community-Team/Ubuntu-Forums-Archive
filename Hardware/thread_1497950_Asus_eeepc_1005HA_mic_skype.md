---
title: "Asus eeepc 1005HA mic skype"
date: 2010-05-31
forum: Hardware
---

### Post by coolman98 on 2010-05-31
Is there any way to get my mic working with skype .
My mom is going to china and wants to skype us from the asus.

---

### Post by coolman98 on 2010-05-31
where is everyone?.......................................

---

### Post by lidex on 2010-05-31
Does the mic work otherwise?
Have you tried this fix:
Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
Reboot.

Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

