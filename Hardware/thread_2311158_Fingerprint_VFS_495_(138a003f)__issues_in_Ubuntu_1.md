---
title: "Fingerprint VFS 495 (138a:003f)  issues in Ubuntu 15.10"
date: 2016-01-25
forum: Hardware
---

### Post by mike396 on 2016-01-25
Hi guys!
I tried to install Ubuntu 15.10 to my laptop hp probook 430 g3. I expected it to work fine but unfortunately there are some problems pupped up through instalation  i can't solve yet.
One of the problem is the fingerprint  (VFS 495 (138a:003f)) driver which was not recognized automaticaly. Can anybody help with it?
To be honest , im pretty new in the Ubuntu world.
Any help will be greatly appritiated.

---

### Post by Vladlenin5000 on 2016-01-25
Hi and welcome.

Yours is a tricky one. This should work for 15.10 also: [https://balintbanyasz.wordpress.com/2015/03/27/get-validity-vfs-495-fingerprint-reader-working-in-ubuntu-14-04/](https://balintbanyasz.wordpress.com/2015/03/27/get-validity-vfs-495-fingerprint-reader-working-in-ubuntu-14-04/)

---

### Post by mike396 on 2016-01-25
Hi Vladlenin5000!
Thank you for quick response.
I have tried that one but unfortunately the procces stucked in line 7

sudo[COLOR=#686868][FONT=Consolas] [/FONT][/COLOR]ln[COLOR=#686868][FONT=Consolas] [/FONT][/COLOR]/usr/lib/x86_64-linux-gnu/libssl.so /usr/lib/libssl.so.0.9.8

As i see the file libssl.so is not exist in this folder and it returns an error.
Hope things are not so complicated at the moment.

---

