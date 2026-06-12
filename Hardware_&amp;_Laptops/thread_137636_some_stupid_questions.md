---
title: "some stupid questions"
date: 2006-02-28
forum: Hardware &amp; Laptops
---

### Post by reptil on 2006-02-28
1) can you help me ??!!

2) how can i fix this?  : Failed to strt the  x server (your graphical interface) it is likely that it is not set up correctly.  
--- running live CD ubunto 5.10
--- laptop compaq armada e500 (pretty old)

3) if i install ubunto 5.10 this  throuble countinue ? how can i fix ??

reptil

---

### Post by rjwood on 2006-02-28
[quote=reptil]1) can you help me ??!!

2) how can i fix this?  : Failed to strt the  x server (your graphical interface) it is likely that it is not set up correctly.  
--- running live CD ubunto 5.10
--- laptop compaq armada e500 (pretty old)

3) if i install ubunto 5.10 this  throuble countinue ? how can i fix ??

reptil[/quote]

```
sudo dpkg-reconfigure xserver-xorg
``` let x read your hardware go with defaults but make sure your video card driver is correct.

---

### Post by reptil on 2006-02-28
rjwood thanks i´m try it in this moment... 

new question : i need to edit  my xorg.conf file to use the  ATI  video driver... this is  possible  using the live cd ?

 reptil

---

### Post by reptil on 2006-02-28
i type : sudo dpkg-reconfigure xserver-xorg
but this  asking  me for a lot of  parameters ...  i´m a simple novice... if only the  gdm doesnt work. the all parameter will not change?

reptil

---

