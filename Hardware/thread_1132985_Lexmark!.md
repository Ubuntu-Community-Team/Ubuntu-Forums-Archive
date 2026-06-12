---
title: "Lexmark!"
date: 2009-04-22
forum: Hardware
---

### Post by B4RR13N705 on 2009-04-22
Hi, i was installing my lexmark x1250 grom this tutorial 
>  [http://geek-ness.blogspot.com/search/label/lexmark](http://geek-ness.blogspot.com/search/label/lexmark) 
(note that i already installed this printer in my pc with that tutorial in ubuntu, now i changed to ubuntustudio) In my ubuntustudio machine. I did everything there. Then i check if the setup was succesfuly, so:
```
 cd /usr/lib/cups/backend 
```
I use the z600 driver, so i type:
```
 ./z600 
```
But i get this error:
```

./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```
I went to Synaptic and search for libstdc but is already installed. 

Any idea?

---

### Post by B4RR13N705 on 2009-04-22
I was missing libstdc++5 !
Thanx anyway!

---

