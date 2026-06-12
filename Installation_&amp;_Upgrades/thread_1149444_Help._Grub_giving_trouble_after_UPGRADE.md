---
title: "Help. Grub giving trouble after UPGRADE"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by lordbux on 2009-05-05
hi friends

i was using ***ubuntu 7.x*** and i tried to upgrade to **8.4 ** from an alternate CD-ROM. 
but i could not run the upgrade sucessfully 
*so i used the alternative CD to do a  fresh install of 8.4  *
but as soon as i completed  the install it seems that:(
the GruB boot loader started giving messages like  ```
 could not mount 

``` :confused:

but the windows selection still works without a haze..
i am in big trouble:guitar:
please help.

---

### Post by sahabcse on 2009-05-05
For fixing the grub follow below url

[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)

---

### Post by lordbux on 2009-05-05
thankyou
i followd the instructions [B]
BUT TROUBLE[/B]:(

**booted by live CD**

ran the following comands:
```
$sudo grub

>find /boot/grub/stage1
    
(hd0,1)

>root=(hd0,4)


``` 
but as soon as i ran the next comand
*>setup (hd0)*
i got an error:(

```
grub> setup (hd0)

Error 17: Cannot mount selected partition

```:confused:

k again stuck
pleas help ...i got to get this working some how.
please someone.:lolflag:

---

### Post by sahabcse on 2009-05-05
pls follow the instruction clear

#sudo grub

grub> find /boot/grub/stage1 

(hd0,x)
root (hd0,x)
setup (hd0)

---

### Post by lordbux on 2009-05-05
oh..
thnx bro
ya i actuly enterd hd0 even after seeing hd1
..sry for the trouble..but only after i restart can i say what is 
gona happen.
anyway thank you:lolflag::guitar:

opensource rock:guitar::lolflag:

---

