---
title: "Ethernet Card Setup"
date: 2009-04-23
forum: Hardware
---

### Post by wbryan6 on 2009-04-23
I've been trying to get the ethernet card working on my older Dell Inspiron 8100, and I finally found something that looks like it will work: [http://manpages.ubuntu.com/manpages/hardy/man4/xl.4.html]("http://manpages.ubuntu.com/manpages/hardy/man4/xl.4.html#toptoc3").  Unfortunately, I'm still too much of a noob to know what the following instructions mean:
```
      To compile this driver into the kernel, place the following lines in your
      kernel configuration file:
 
            device miibus
            device xl
 
      Alternatively, to load the driver as a module at boot time, place the
      following line in loader.conf(5):
 
            if_xl_load="YES"
```

After searching around, all I could find were other Manpages with similar instructions and nothing more in depth.  Does anyone have any words of wisdom that can help me get this working?  Thanks in advance.

---

### Post by SnaveDogg on 2009-04-24
> **wbryan6 said:**
> I've been trying to get the ethernet card working on my older Dell Inspiron 8100, and I finally found something that looks like it will work: [http://manpages.ubuntu.com/manpages/hardy/man4/xl.4.html]("http://manpages.ubuntu.com/manpages/hardy/man4/xl.4.html#toptoc3").  Unfortunately, I'm still too much of a noob to know what the following instructions mean:
```
      To compile this driver into the kernel, place the following lines in your
      kernel configuration file:
 
            device miibus
            device xl
 
      Alternatively, to load the driver as a module at boot time, place the
      following line in loader.conf(5):
 
            if_xl_load="YES"
```After searching around, all I could find were other Manpages with similar instructions and nothing more in depth.  Does anyone have any words of wisdom that can help me get this working?  Thanks in advance.


I'm looking for help too, it seems few and far between.

---

