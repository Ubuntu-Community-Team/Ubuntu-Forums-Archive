---
title: "fan control"
date: 2011-11-23
forum: Hardware
---

### Post by Tannor on 2011-11-23
Does anyone know if there is a way to control your fans in a Dell Laptop?  I use to have a nice little window app that can do that.

Thanks in advance

---

### Post by Redblade20XX on 2011-11-23
Hopefully this will point you into the right direction!
[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

- Red

---

### Post by Tannor on 2011-11-23
Not what I was looking for exactly.

Basically I am trying to find something that will make my fans go max all the time.

Yes I know it might get loud but if i do not do that my video card will overheat.  I already had 2 cards die very fast, and ever since I max my fans it has been fine.

---

### Post by Redblade20XX on 2011-11-23
Did you check if your fan can be controlled by acpi in the previous link?

 If so, you should be able to make a script to control the speed. 

If not, then your fan is most likely controlled by the BIOs and you'll have to check whether or not the BIOs allows you to control it.

:)

- Red

---

### Post by Tannor on 2011-11-24
I dont see it

/proc/acpi$ ls -lrt
total 0
-r-------- 1 root root 0 2011-11-24 11:08 event
-rw-r--r-- 1 root root 0 2011-11-24 16:15 wakeup
dr-xr-xr-x 3 root root 0 2011-11-24 16:15 button
dr-xr-xr-x 3 root root 0 2011-11-24 16:15 battery
dr-xr-xr-x 3 root root 0 2011-11-24 16:15 ac_adapter


And when i go into the BIOS have no way to control the fans.

What I dont get is I never hear the fans go on at all once I boot into ubuntu.

There must be some sort of way controlling it?

---

### Post by BC59 on 2011-11-24
You can install Jupiter and it has many tweaks about this.


```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```

---

