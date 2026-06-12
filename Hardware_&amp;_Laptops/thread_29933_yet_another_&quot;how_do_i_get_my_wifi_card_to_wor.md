---
title: "yet another &quot;how do i get my wifi card to work with kubuntu&quot; thread"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by jon_hill987 on 2005-04-26
Yeah, i know there have been a fair few of these, anyway here is my problem:

I have a HP compaq nx9005 and am using a NetVision Wireless LAN Carbus Card.

I'm folowing the instructions i found to compile ndiswrapper (which i believe I need for my card to work) but i get an error at the folowing step:

```
apt-get install build-essential fakeroot linux-headers-`uname -r`
```

It says package linux-headers-'uname -r' can not be found. I have tryed both root and my own username in place of uname (I also tryed uname) do I need something else?

BTW: if you hadn't noticed I am a N00b, I installed linux last night. Please make any answers so a slug could understand, thanx!

EDIT: Sorry, I put this in the wrong forum, i have the Hoary 5.04 dist, if a mod ould be kind enough to move it i would be very greatfull.

---

### Post by jakev383 on 2005-06-15
You need to type 'uname -r' at the command line, which will tell you the version of the kernel you're running. For example, mine says:
2.6.10-5-386
which means I would do:
apt-get install linux-headers-2.6.10-5-386
for the headers for the kernel.

---

