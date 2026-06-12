---
title: "Completely remove ati 10.4 from ubuntu 10.04"
date: 2010-05-02
forum: Hardware
---

### Post by foxsick on 2010-05-02
Yesterday I installed ati catalyst 10.4 and after restart my system didn't start. I went to recovery console and wrote: 
sudo sh /usr/share/ati/fglrx-uninstall.sh
then
 sudo aptitude purge ~nfglrx ~~nvideo-ati && dpkg-reconfigure -phigh xserver-xorg.
So my system have been getting up. But now I haven't got a FGRLX driver in Hardware Manager so, I didn't remove driver completely. How can I do it? 
When I was on Ubuntu 9.10 I also tried to install  ati driver and had the same bag, but I found the solution of it somewhere... I don't remember where... I introdused this command and FGLRX driver has been apearancing... Now I want to do the same.

Really sorry for my English, but my fellows citizens don't know the solution of this problem... If I haven't said something, I try to explain that.

---

