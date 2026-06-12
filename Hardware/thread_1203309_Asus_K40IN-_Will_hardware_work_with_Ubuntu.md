---
title: "Asus K40IN- Will hardware work with Ubuntu?"
date: 2009-07-03
forum: Hardware
---

### Post by FarmerDaughter on 2009-07-03
I'm hoping to get this notebook and install Ubuntu Jaunty myself on it. 
 
[http://www.canadacomputers.com/index.php?do=ShowProduct&cmd=pd&pid=023679&cid=896.500](http://www.canadacomputers.com/index.php?do=ShowProduct&cmd=pd&pid=023679&cid=896.500)
 
Will this hardware work? If you feel that there are too many issues, which Asus laptop is most compatible with Ubuntu 9.04 (stilling paying less than $1100)?
 
Thanks!
 
ETA- Was also looking at this Gateway, but I'm not too sure about the brand name and how long they have a tendency to last (would like to get atleast 5 years.)
 
[http://www.canadacomputers.com/index.php?do=ShowProduct&cmd=pd&pid=021453&cid=896.645](http://www.canadacomputers.com/index.php?do=ShowProduct&cmd=pd&pid=021453&cid=896.645)

---

### Post by kungfoofool on 2009-07-10
I purchased this laptop, and alas there are many issues. I'm keeping track of (some of) them here: [Ubuntu 9.04 Jaunty on ASUS K40IN-A1]("http://realm3.com/articles/ubuntu_9.04_on_asus_k40in-a1")

So far the biggest issue is with the sound & the Nvidia G102M GPU. I'm still (unfortunately) using Vista until I can get all of that working properly.

---

### Post by kungfoofool on 2009-07-12
After installing the latest Nvidia drivers (instructions in link above) a lot of issues were resolved. I still have two issues that I'm working on:
- Disabling the touchpad while typing
- Getting the laptop speakers to work

---

### Post by davilicious on 2009-08-06
Hi,
 
First of all I wanna say that I'm new to linux but I'm very interested on exploring it, especially Ubuntu.
 
Earlier I have the same problem as you, I installed Ubuntu 9.04 on ASUS K40IN-1A and the speaker didn't work.
 
But after I flash my motherboard BIOS form version 207 to version 213, the speaker works perfectly. I guess it's because of the BIOS upgrade cause I didn't do anything else [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]
 
Hope this helps.
 
 
Best regards,
 
David$

---

### Post by jan-12 on 2009-08-20
a way to partly solve the touchpad messing up when typing is to install touchfreeze via synaptic.  not 100% but better than nothing.  i have the same problem with the g102m nvidia.  for now, just stayed with the default setting without the nvidia driver, so no video acceleration. maybe karmic...

---

### Post by zayustman on 2009-09-09
I try update Bios to 213..n work good on sound. for NVIDIA G102M download latest geforce 9 series notebook and install manual. mine works fine. by the way I'm use Ubuntu 8.10 Inteprid Ibex. work nice with compiz fusion, 

note : DONT UPDATE NVIDIA DRIVER VIA SYNAPTIC PACKAGE it will delete manual driver we install n will not work properly. but if you have been update it..install driver manual again. it will be back again. have a nice try..:P

---

### Post by kolkhoz on 2009-09-28
I also have Asus K401N. Initially it came with Vista, then I immediately put XP on it. After that I tried the whole dual boot thing with Ubuntu 9.04, but that didn't work. The live CD would run, but then at some point i would get a bug int 6 cr 2. I tried persistent install from a USB, wubi install inside windows, i tried older versions, i updated the BIOS...at some point i would still get a bug int 6 cr 2. I'm not sure what the reason is. Any thoughts?

---

