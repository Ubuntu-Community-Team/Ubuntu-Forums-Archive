---
title: "Update manager item - can't update or remove"
date: 2008-09-24
forum: General Help
---

### Post by kiderjones on 2008-09-24
Hi. I have one item in my update manager (K3b in this instance) that will not check or update. It's just there, and remains when other software is updated.
Does anyone know how to remove this?
Thanks.

---

### Post by odin277 on 2008-09-24
Kiderjones
Had the same problem and this worked for me.
Open a terminal and type or copy/ paste the following one line at a time
(You will be prompted for your password after the first command):
sudo apt-get update
sudo apt-get upgrade
(if that doesn't rectify the problem then) 
sudo apt-get install k3b

As I said it worked for me so I'm hoping it works for you

---

### Post by kiderjones on 2008-09-24
Thanks odin277,
apt-get install did the trick.
woot

---

