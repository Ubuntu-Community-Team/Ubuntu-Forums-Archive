---
title: "How to see XP NVIDIA Raid ubuntu 7.10"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by JPMATRIX on 2007-11-20
I people, I have been dedicating lot's of time to gutsy, learning how to handle this completely new system (to me), to this point I just google, but now I need some help, because a think this is a little more delicate then the problems I ad so far.

I installed ubuntu on an hold 60Gb IDE hard drive but I have a raid 0 for windows XP, I just want to be able to access this raid to  easily see my mp3 movies etc...

The motherboard is an ASUS ps5n-e SLI, could any one help? 

I am going to continue googling.. the right words and I just might get lucky :)

---

### Post by colo on 2007-11-20
You'll probably need dmraid for this ( [http://packages.ubuntu.com/gutsy/admin/dmraid](http://packages.ubuntu.com/gutsy/admin/dmraid) ). I don't know if the Linux kernel already supports Windows Software RAID Arrays - if you got one of those set up, I can't provide you with any meat to google for, sorry.

---

### Post by JPMATRIX on 2007-11-24
Ok thanks so I installed dmraid using

sudo apt-get install dmraid

But how do I configure?

Edit:

Tried sudo dmraid -s
Gave me this:

*** Active Set
name   : nvidia_ecaaibca
size   : 976794112
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0

Dont know what to do next :(

---

