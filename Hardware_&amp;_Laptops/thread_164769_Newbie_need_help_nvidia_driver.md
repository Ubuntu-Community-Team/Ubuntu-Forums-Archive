---
title: "Newbie need help nvidia driver"
date: 2006-04-23
forum: Hardware &amp; Laptops
---

### Post by xwindows2 on 2006-04-23
I installed 6.06 beta dapper, want to get the nvidia driver to work
not sure how to or where to start
If someone can help me with this that would be great, with step by step
instructions..I have installed nvidia driver before on fedora 3  2 yrs ago..
 Not sure if done the same way or automatically
 My hardware amd 1300..512 ram..video pny gforce 5200 ... 15 gig hd

---

### Post by johnc4510 on 2006-04-23
If glx is the correct driver for your card:
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

---

### Post by xwindows2 on 2006-04-23
not sure what you mean sudo, from edit prog?

---

### Post by scooper on 2006-04-23
[QUOTE=xwindows2]not sure what you mean sudo, from edit prog?[/QUOTE]

From a command prompt, sudo is a command that runs another command with root (admin) rights, if you provide your password.

---

