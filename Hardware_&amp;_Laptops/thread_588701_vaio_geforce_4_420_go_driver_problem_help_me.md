---
title: "vaio geforce 4 420 go driver problem help me"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by barks on 2007-10-23
hi all,

im new to linux, i tried a few different live versions and decided to install ubuntu, i liked the feel of it.
ive partitioned my laptops and pcs and installed it with no probs.

except 2 

1 in the configure network manualy option there isnt an option to select no security?
2 on my vaio with geforce 4 420 go i get full resolution but when i download the restricted drivers for the card the next time i boot i get just to the login and the screen goes blank, looks like it turns off?
i have to reinstall it after.
i really want to get the desktop effects working but it just wont? anyone any ideas. also the wifi is slow but ok in xp?
thanks

---

### Post by barks on 2007-10-24
nearly 12,000 people on line and not 1 reply.

---

### Post by isc_franky on 2007-10-26
> **barks said:**
> hi all,

im new to linux, i tried a few different live versions and decided to install ubuntu, i liked the feel of it.
ive partitioned my laptops and pcs and installed it with no probs.

except 2 

1 in the configure network manualy option there isnt an option to select no security?
2 on my vaio with geforce 4 420 go i get full resolution but when i download the restricted drivers for the card the next time i boot i get just to the login and the screen goes blank, looks like it turns off?
i have to reinstall it after.
i really want to get the desktop effects working but it just wont? anyone any ideas. also the wifi is slow but ok in xp?
thanks

Hi 
I had the same problem when i was trying to install the last nvidia driver, but it didnt work
you can restore your graphic enviroment with the command 

sudo dpkg-reconfigure xserver-xorg
you only accept the default video parameters

you just choose the second option of ubuntu grub 
good luck

---

