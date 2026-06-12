---
title: "printing problems"
date: 2005-12-05
forum: General Help
---

### Post by emerick7 on 2005-12-05
I'm trying to get my HP Deskjet 712 set up.  I went through everything in the Admin->Printing properties and then installed the pnm2ppa driver.  I saw here somewhere that I need to change something in the pnm2ppa.conf file in /etc, but when I go to edit the file, I am not able to since it is read only.  The solution to making is editable is probably pretty obvious, but I'm not so sure where to go as I am new to linux.  Any other ways to get my printer working would be great.  Thanks for the help, Ty.

---

### Post by flopsy on 2005-12-05
Open a terminal with Applications > Accessories > Terminal. Enter
```
sudo gedit /etc/pnm2ppa.conf
```

---

