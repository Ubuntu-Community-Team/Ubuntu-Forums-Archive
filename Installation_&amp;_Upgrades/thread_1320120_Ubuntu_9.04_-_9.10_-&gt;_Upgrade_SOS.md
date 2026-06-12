---
title: "Ubuntu 9.04 - 9.10 -&gt; Upgrade SOS"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by skarlekar on 2009-11-08
I was upgrading my 9.04 parition to 9.10 on a 64-bit machine. Half-way through my machine froze. I forced an hard reboot and now it is not coming up. It is saying that it is waiting on an UUID - apparently the id for my partition. Any thoughts on how I can get around this? Anybody?

---

### Post by AndreLeComte on 2009-11-09
Do you get a message like this?:
[IMG]http://img193.imageshack.us/img193/9374/img0037cf.jpg[/IMG]

---

### Post by AndreLeComte on 2009-11-09
This basically solved the issue for me:
> **arekku said:**
> [Here](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)

Replace your nonworking initrd file with a previous version. For you Andre all you need to do is (just in case you are new)

cd /boot
sudo mv initrd.img-2.6.31-14-generic backup
sudo cp initrd.img-2.6.28-16-generic initrd.img-2.6.31-14-generic

---

