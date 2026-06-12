---
title: "install nvidia driver all possible ways"
date: 2011-07-24
forum: Hardware
---

### Post by pain.reign on 2011-07-24
I tried everything from the internet to install nvidia driver. Nothing works.

I need to install it on ubuntu 11.04. Nvidia driver GT 540 M.

Suggest any solution with steps i will make it.

As for what i already did:

1. Tried installing bumblebee - doesn't help intel works nvidia black streen when set in in xorg.conf
2. Tried sudo install nvidia-current. Installs ok. when configure xorg.conf with sudo nvidia-config command doesn't start again.
3. INstalled nvidia from nvidia site. same symptoms... 

Anyone can suggest anything except changing core for ubuntu etc..

also it says runlevel compability - fail at boot... if i change runlevel to 3 doesn't boot even in recovery mode.

---

### Post by realzippy on 2011-07-24
Since you seem to have an Optimus laptop ,
vga switcheroo/bumblebee is the only option for you if your
BIOS does not provide a switch for the graphic adapters.

---

### Post by pain.reign on 2011-07-24
I have asus k53sv what switch should i look for in bios? I checked bios i think i don't have any graphyc switches. But still my nvidia works in windows 7. But i also want it to work in ubuntu.

Also i don't know about optimus. I don't have a label saying optimus on my laptop.

---

### Post by realzippy on 2011-07-24
Here you can read about Optimus and check if this affects your machine:
[http://ubuntuforums.org/showthread.php?p=10304516#post10304516](http://ubuntuforums.org/showthread.php?p=10304516#post10304516)

Edit:
Looks like NVIDIA Optimus:
[http://greatshop1.wordpress.com/2011/06/25/asus-k53sv-sx080v-15-6-inches-i5-sandy-540m-gt-optimus-640-gb-to-699-e/](http://greatshop1.wordpress.com/2011/06/25/asus-k53sv-sx080v-15-6-inches-i5-sandy-540m-gt-optimus-640-gb-to-699-e/)

---

### Post by pain.reign on 2011-07-26
well yeah. I definately have optimus....thnx for the direciton. will try to work in this direction.

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

