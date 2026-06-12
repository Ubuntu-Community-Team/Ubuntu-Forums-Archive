---
title: "Dell Latitude D620 Laptop"
date: 2013-08-24
forum: Hardware
---

### Post by gordie692 on 2013-08-24
I bought a Dell Latitude D620 laptop and because it only has 2 gigs and 120 gig hard drive I decided to put Ubuntu 12.04 LTS 32 bit and everything worked beautiful except I couldn't get the wifi light to turn on. So I posted but I just thought maybe I'll try using my old friend google and so happen that I found a command and read it and it was for 12.10 but thinking it should work older laptop they would use the same driver, So I use the driver in my terminal installed it rebooted and there it went and so far so it's been great the perfect little laptop without Windows running Ubuntu the flavor I love.

The command I typed was

sudo apt-get install Linux-firmware-nonfree

---

### Post by squakie on 2013-08-26
Post back the output of:

lspci

lsusb

ifconfig

iwconfig


Right now I wish I could remember what I did back when I had one of those laptops.  But, before we can really do anything we need to know the adapter - the above information should give us enough to start.

---

