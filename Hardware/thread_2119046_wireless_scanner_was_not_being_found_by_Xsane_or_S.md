---
title: "wireless scanner was not being found by Xsane or Simple scan"
date: 2013-02-22
forum: Hardware
---

### Post by Fungus on 2013-02-22
I've been going nuts for a few days since my Brother MFC-7840W wireless scanner was not being found by Xsane or Simple scan. I confirmed driver was installed per Brother linux website.

I also ran brsaneconfig3 -d, which showed and pinged the device all ok. it also showed its ip address as 192.168.1.101 on my wireless network (there is also a way to check and set the ip address on the machine itself. see manual)

Anyway i was poking around for configuration settings and I found the file /usr/local/Brother/sane/brsanenetdevice3.cfg. When I opened it up I see one line of text:

DEVICE=SCANNER , "MFC-7840W" , 0x4f9:0x1e5 , IP-ADDRESS=192.168.1.100

So, I change the ip address to 192.168.1.101. Close the file and then xsane and simple scan both work!

---

