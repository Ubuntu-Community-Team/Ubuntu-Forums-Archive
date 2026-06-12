---
title: "how can i edit etc\ppp\options"
date: 2005-11-25
forum: General Help
---

### Post by trisscross on 2005-11-25
hi i am trying to setup my modem and after reading up  i need to edit a file (etc/ppp/options) but i don't know how to if i try to edit in file browser/file system it tells me (you are not the owner,so you cant change thease permissions ?? i have been trying to sort this out for hours now. how do i get permission to edit a file
please can someone help me
~tris

---

### Post by xristos on 2005-11-25
Try this from a console
```
sudo gedit /etc/ppp/options
```

---

### Post by canadianwriterman on 2005-11-25
In the Terminal window, you can type:

**sudo gedit /etc/ppp/options**

---

### Post by hw-tph on 2005-11-25
In Ubuntu you use the sudo command to execute commands as the superuser (hence "sudo" - SuperUser DO): **sudo gedit /etc/ppp/options** will execute the gedit editor on the /etc/ppp/options (forward slashes in Linux and all other Unix-like operating systems :)).


*Edit:* I need to type faster. :D

H&#229;kan

---

### Post by trisscross on 2005-11-25
thankyou (gedit) i was typing edit with no luck .i dont know all the commands is there any where that i can print them ??
i loive ubintu now i have got it working on the net 
now its working i am going to install it on my a 64 rig
thanks again ror the quick replys :smile: :smile:

---

