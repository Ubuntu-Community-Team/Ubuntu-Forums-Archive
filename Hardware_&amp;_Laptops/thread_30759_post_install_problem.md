---
title: "post install problem"
date: 2005-04-30
forum: Hardware &amp; Laptops
---

### Post by vignesh on 2005-04-30
I get an error saying that gui is not properly cofigured so I run xf86config and set my monitor and graphics card after that I run startx and I get an error saying  

fatal error 
no screens found
please help.

---

### Post by heimo on 2005-04-30
Try running
 ```
sudo dpkg --configure -a
``` 

And you can try to reconfigure xserver-xorg
 ```
sudo dpkg-reconfigure xserver-xorg
``` 

For resolution related problems:
[http://www.ubuntuforums.org/showthread.php?t=21984](http://www.ubuntuforums.org/showthread.php?t=21984)

---

