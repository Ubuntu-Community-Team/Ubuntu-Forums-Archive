---
title: "VGA Problem with the Dell 2007FP Color Monitor..."
date: 2006-12-22
forum: Hardware &amp; Laptops
---

### Post by Fawad Nazir on 2006-12-22
Hi All,

I am trying to install Ubuntu using Dell 2007FP Color Monitor. It start well but afterwards there is a small blue window coming my screen saying " Out of Range signal, Cannnot display this video mode, change computer display input to 1600X1200 @60Hz".

I also tried to change the resolution from the F5:VGA option in the bigginning but it does not solve the problem. I am not sure how to change the frequency to 60Hz?

Plzzz Help.

Regards,

---

### Post by Ashrael on 2006-12-22
You have to reconfigure your x server...(dpkg-reconfigure xserver-xorg)...and tell it your monitors characteristics...so try to find out on t he net what your monitor is capable of...then try the above command to reconfigure your X...

hope this helps!

---

