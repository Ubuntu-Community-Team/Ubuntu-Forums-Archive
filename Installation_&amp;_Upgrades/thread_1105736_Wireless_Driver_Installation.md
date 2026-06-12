---
title: "Wireless Driver Installation"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by Nick420 on 2009-03-25
Im tryin to get my wireless driver to work.

i have a Dell D520 | Latitude Laptop with the standard 1390 Wireless Card.  im new to Linux/Ubuntu so im not sure what to do to get this working. 

Even when i plug an ethernet cable directly to the router, i still cannot connect.  i need help in fixing this problem please.  

I'm assuming i need to install the driver on ubuntu, but im not sure where to find this driver, and how to transfer it to ubuntu.

If anyone could help me with this, it would be great!

Again- i cant connect to the internet in Ubuntu thru wireless nor Wired.  ive tried finding hidden networks, but it automatically disconnects me.  same with the wired networks.  i can get internet in Vista tho.

Thank you for your help.

---

### Post by cariboo on 2009-03-25
COuld you open an Applcations-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

and paste the output in your next post.

Jim

---

### Post by toehead2 on 2009-03-25
I had a similar issue with my Dell Inspiron 1100 laptop,could not get wireless to connect for more than a few seconds, wired didn't work. I rebooted the computer with (safe-mode) the second option at the boot screen. Everything worked from that point forward. As I am new to Linux I can't tell you why this worked for me but I am replying to this thread in Ubuntu 8.04 so it did work.:)

---

