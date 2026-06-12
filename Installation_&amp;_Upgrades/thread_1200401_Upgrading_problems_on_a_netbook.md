---
title: "Upgrading problems on a netbook"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by nlinggod on 2009-06-30
I have an EEE 901 which I put Ubuntu Netbook remix on.

The EEE901 has 2 SSDs, one 3G and one 16G. I put the / directory on the smaller one and /home on the other one.

Now I find that I don't have enough space on the smaller SSD for upgrades. It's sitting at 97% full.

How can I arrange things so that the basic stuff for ubuntu sits on the smaller SSD and all the other stuff, like extra applications, games n stuff, sit on the larger SSD?

Thanks in advance

---

### Post by nlinggod on 2009-07-02
No body knows how? I've been searching myself but most answers I find are filled with language that goes straight over my head , so I'm not even sure if it answers my question!

---

### Post by buellman on 2009-07-02
You could try to merge both drives to one virtual big drive with LVM.

Greets. Buellman

Ps: [Instructions for Ubuntu Hardy]("http://menelkir.wordpress.com/2008/05/22/lvm-on-ubuntu-hardy-heron/") but maybe it will work for you.

---

### Post by nlinggod on 2009-07-02
Sweet thanks mate. I'll give that a try.

---

### Post by buellman on 2009-07-02
No problem :-)

Greets. Buellman

---

