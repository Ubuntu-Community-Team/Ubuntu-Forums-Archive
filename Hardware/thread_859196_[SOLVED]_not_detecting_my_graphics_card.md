---
title: "[SOLVED] not detecting my graphics card"
date: 2008-07-14
forum: Hardware
---

### Post by wildwest82 on 2008-07-14
Hey everybody! I am new to Ubuntu and Linux. I am having trouble trying to get hardy 8.04 to detect my Asus Radeon HD 4850. I have tried looking in Hardware drivers but it is not there.

---

### Post by pytheas22 on 2008-07-14
[envy]("http://www.albertomilone.com/nvidia_scripts1.html") might help you.  Install it with:
```

sudo apt-get install envyng-gtk
```

Then run it with:
```

sudo envyng-gtk
```

It has an option to automatically detect and install the driver for your card; let it try to to do that.  It doesn't always work but I've seen very good results from it in the past.

---

### Post by wildwest82 on 2008-07-14
Hey! Thanks for the quick response. I ran Envy and it said that it does not recognize my card as compatible with any version of the driver.

---

### Post by pytheas22 on 2008-07-14
Sorry to hear that.  Is your card really new?  What is the output of this command:
```

lspci
```

---

### Post by markbuntu on 2008-07-14
Envy and the driver it has, 8.47.3 is no good for your card but the 8.6 driver from ati is. Follow these directions very carefully, use Method 2.


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

ATI packaged this driver with the HD4800 series cards though many resellers and oems did not so it will work for you.

---

### Post by wildwest82 on 2008-07-14
That was the problem. I finally got full resolution. Hey thank you guys for all your help.

---

