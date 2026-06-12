---
title: "Amilo 1650 G quick launch buttons"
date: 2007-10-05
forum: Hardware &amp; Laptops
---

### Post by Sofie on 2007-10-05
To activate or unactivate quick launch buttons for Amilo 1650 G see:

[http://damagedspline.blogspot.com/2007/03/fsc-amilo-a1650g-ubuntu-fiesty-32bit.html](http://damagedspline.blogspot.com/2007/03/fsc-amilo-a1650g-ubuntu-fiesty-32bit.html)

I used way 3:
alt+F2
enter the string: "gksu gedit /etc/modprobe.d/options"
add at the end of the file /etc/modprobe.d/options
I entered the string:
"options ath_pci rfkill=0"

And now I have turned on the wireless buton always.

Now I only need to find out how to connect to my network...

---

