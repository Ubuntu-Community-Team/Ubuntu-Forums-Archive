---
title: "[SOLVED] Firefox Uses way too much RAM"
date: 2008-11-15
forum: General Help
---

### Post by init1 on 2008-11-15
I find that after a few hours of Firefox 3 usage in 8.10, Firefox takes up around 150MB of RAM. Why does this happen, and how can it be fixed?

---

### Post by lovinglinux on 2008-11-15
Try this:
[QUOTE=http://www.lifespy.com/2007/firefox-quick-tip-limit-ram-usage/]    * Access the about:config page.
    * Find the browser.cache.memory.capacity key.
    * Double-click it to change the value
    * Adjust the value. For those with 512MB to 1GB of RAM, start with a value of 15000. For those with less (between 128MB to 512MB), try a value of 5000.
    * Accept the changes and see how Firefox behaves.[/QUOTE]

---

### Post by alwayshere on 2008-11-15
i did this to speed up 

You have to open your /etc/sysctl.conf file.

sudo gedit /etc/sysctl.conf

Scroll to the bottom and just add these lines to it.

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

run the sysctl to take effect.

sudo sysctl -p

---

### Post by boblemur on 2008-11-16
lol wow thats more than my entire system....

try iceweasel... it uses the same engine and it looks the same... its just alot more lightweight im using it atm... and its alot smaller which is nice :) opens alot faster too

---

### Post by kerry_s on 2008-11-16
> **boblemur said:**
> lol wow thats more than my entire system....

try iceweasel... it uses the same engine and it looks the same... its just alot more lightweight im using it atm... and its alot smaller which is nice :) opens alot faster too

you know iceweasel is firefox?
only the name and icons have been changed.

---

### Post by init1 on 2008-11-16
> **lovinglinux said:**
> Try this:
browser.cache.memory.capacity doesn't exist, but browser.cache.**disk**.capacity, browser.cache.memory.**enable** and browser.cache.**offline**.capacity exist

---

### Post by init1 on 2008-11-16
> **alwayshere said:**
> i did this to speed up 

You have to open your /etc/sysctl.conf file.

sudo gedit /etc/sysctl.conf

Scroll to the bottom and just add these lines to it.

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

run the sysctl to take effect.

sudo sysctl -p
This has nothing do with Firefox's memory usage.

---

### Post by lovinglinux on 2008-11-16
> **init1 said:**
> browser.cache.memory.capacity doesn't exist, but browser.cache.**disk**.capacity, browser.cache.memory.**enable** and browser.cache.**offline**.capacity exist


Right-click anywhere in the about:config window and select New and then Integer from the pop-up menu

Enter browser.cache.memory.capacity in the New integer value pop-up box

You'll need to enter a number in the Enter integer value

Confirm that the new entry has been created and the integer value is correct

---

### Post by exploder on 2008-11-16
I am currently trying the browser.cache.memory.capacity suggestion because I noticed memory use climbing over time. Hopefully this will help. Thanks for the suggestion.

---

### Post by OrangeCrate on 2008-11-16
**Linux Memory Management or 'Why is there no free RAM?'**

> Traditional Unix tools like 'top' often report a surprisingly small amount of free memory after a system has been running for a while. For instance, after about 3 hours of uptime, the machine I'm writing this on reports under 60 MB of free memory, even though I have 512 MB of RAM on the system. Where does it all go?

Find the answer here:

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

---

### Post by exploder on 2008-11-16
OrangeCrate, thanks for the link! Very good information!

---

### Post by init1 on 2008-11-16
> **OrangeCrate said:**
> **Linux Memory Management or 'Why is there no free RAM?'**
I think it might be helping a little, but it's still an issue. (I changed it to 5000)


Find the answer here:

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)
This doesn't tell me why Firefox is requiring so much RAM. If I had 1GB RAM this wouldn't be an issue, but since I have 512MB, my system is using more than 200MB of swap.

---

### Post by philinux on 2008-11-16
150meg for FF is about right. Dont worry about swap linux takes care of it very well.

The important thing is does your system perform ok. If so no worries.

---

### Post by init1 on 2008-11-21
Well, I guess there isn't much I can do. Reducing the cache seems to have worked some though.

---

