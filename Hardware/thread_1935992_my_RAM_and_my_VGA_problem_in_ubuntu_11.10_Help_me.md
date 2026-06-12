---
title: "my RAM and my VGA problem in ubuntu 11.10 Help me"
date: 2012-03-05
forum: Hardware
---

### Post by jejeh919 on 2012-03-05
Good afternoon to you guys , 
i've some problem's here, my laptop is HP pavilion dm3 , i have 4 GB RAM and nvidia geforce G105M , i'm using ubuntu 11.10 OS , my ubuntu have not detect the corret size of my ram and it's say's 'blank' with my graphics card , can anyone help me , i'm very noob with ubuntu .
here's the screenshoot , i use "sudo lshw" command to show my laptop spec.

> [IMG]http://oi42.tinypic.com/2lbkhhx.jpg[/IMG]

---

### Post by Yellow Pasque on 2012-03-05
You should be running 64-bit. That is what causes the RAM issue.
There is no VGA issue (just a bug in the System Info program).

---

### Post by 2F4U on 2012-03-05
Ubuntu 32 bit can address up to 4GB of RAM, but you won't be able to use the complete 4GB. Other hardware in the machine will take up addresses and if this is a graphics card without dedicated RAM, this will also reduce the available RAM.

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

