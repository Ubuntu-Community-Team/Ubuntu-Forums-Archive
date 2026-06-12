---
title: "Compact Flash to PCMCIA Adapter"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by Varjagy on 2006-10-24
I have a CF-PCMCIA adapter, but it won't work when I boot.

I used dmesg and I everything looks ok, like everything should work.

I got it to work:

sudo mkdir /mnt/cf
sudo mount /dev/hde1 /mnt/cf

I found the hde1 in dmseg.

Well, this works for now, but can anybody help me to figure out how to get it to "auto load"

---

