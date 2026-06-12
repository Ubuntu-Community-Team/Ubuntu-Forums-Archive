---
title: "hard drive gone?"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by Ridgerunner9 on 2007-05-09
let's start at the begining my harddrive is fine. when i run mandriva or winblows it shows all my hardrives and i can access them just fine but with ubuntu it will only acceses my master harddrive.  I also have a 120 gig slave and either i do not know what i am doing or it's not there so any help getting all my hardrives into the mix would be great. i want to put media on the slave but i need to either find it or get the os to see it. thank you

---

### Post by taurus on 2007-05-09
Sounds like you need to mount it before you can access it.  Open a terminal and paste the output of this command here

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
or here is a guide for you.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Ridgerunner9 on 2007-05-09
just before you posted i found what i did wrong. i found a divice manger. when i found where it was i found i could mount it and i could even cut a shortcut to my places menu for easier access. i also found out how much easier it is when you are logged in as root:lolflag:  now that i can find it i will be able to use it thanks for your help.

---

