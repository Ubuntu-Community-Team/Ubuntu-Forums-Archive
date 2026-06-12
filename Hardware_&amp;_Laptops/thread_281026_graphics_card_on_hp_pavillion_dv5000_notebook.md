---
title: "graphics card on hp pavillion dv5000 notebook"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by ojasvi rajpal on 2006-10-20
Hi all,
I have been using ubuntu for past one month now . I want to know that how can  I config my nvidia graphic card or better still how to check is it working or not .
the output of following commands may be helpful in pinpointing the prob:-
$lspci -n | grep 0300
$0000:01:00.0 0300: 10de:01d8 (rev a1)

$lspci | grep VGA
$0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01d8 (rev a1)

thanks

---

### Post by ReaderRat on 2006-10-20
[**Installing Nvidia Drivers**](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by willca on 2006-11-05
If try to install the X nv drivers using apt-get. Edit your xorg.conf and change the driver to nv. But before you do that I would suggest you back up your config first.

I had problems with another laptop that had nvidia before. I got it to change to the resolution I like but cannot make 3d acceleration work. Most likely because my card was so new that is not yet supported by Xorg.

Good luck. If you need more help, posting your xorg.conf will be good as well.

HTH
-W

---

