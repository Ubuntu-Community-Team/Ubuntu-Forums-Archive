---
title: "fglrx driver open source"
date: 2008-04-17
forum: Hardware &amp; Laptops
---

### Post by skeetwood-mac on 2008-04-17
I just switched to a radeon 9200 and my video is still a little bit slow. I was  thinking of trying the fglrx driver instead of the one that comes with ubuntu. Will that help? also the fglrx driver in synaptic doesn't say it supports the radeon 9200 but on the ati site it tells me to download the rpm of fglrx for the 9200. Any thoughts would be helpful before I go screwing up my system with un needed junk.

---

### Post by Saint Angeles on 2008-04-17
no rpms !

get the fglrx (.run file) from the ati website. 8.4 came out today!

---

### Post by skeetwood-mac on 2008-04-17
alright I got it. So do I just open that or do I need to uninstall the old one? Is there a how to somewhere?

---

### Post by Nameless_one on 2008-04-17
There's this:

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

It's as close to official as you can get.

---

### Post by boxfullofheads on 2008-04-17
Hi,
I just installed Ubuntu 7.10 3 days ago and this is my first time
trying Linux from a windows user.. i looked at my Graphics card
driver and found it to be on Permedia2 (generic) Permedia4 (generic)
and it tells me i have a ATI Radeon (fglrx) card should i change
the  driver to match the card? 
I was looking at this because the effects in CompizConfig are
Disabled.. (Water Effect) (Paint Fire) but Wobbly Windows
is working

---

### Post by skeetwood-mac on 2008-04-18
alright I followed those steps and I got part way through making the deb package and it says 

./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

is the file bad?

---

### Post by jocko on 2008-04-18
> **skeetwood-mac said:**
> I just switched to a radeon 9200 and my video is still a little bit slow. I was  thinking of trying the fglrx driver instead of the one that comes with ubuntu. Will that help? also the fglrx driver in synaptic doesn't say it supports the radeon 9200 but on the ati site it tells me to download the rpm of fglrx for the 9200. Any thoughts would be helpful before I go screwing up my system with un needed junk.

Fglrx does NOT support radeon 9200, ati abandoned everything older than 9500 almost two years ago, and the last driver to support your card does not work on xorg versions newer than 7.1. The open source drivers are your only option, unless you still use dapper or edgy...

---

### Post by skeetwood-mac on 2008-04-18
oh ok thanks. So theres no way for me to watch full screen videos without it being all choppy?

---

### Post by skeetwood-mac on 2008-04-19
do I need a new video card?

---

