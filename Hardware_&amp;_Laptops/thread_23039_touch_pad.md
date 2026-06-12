---
title: "touch pad"
date: 2005-03-30
forum: Hardware &amp; Laptops
---

### Post by blu.gecko on 2005-03-30
I have a Compaq Presario 2210US currently running 4:10
My touchpad is super touchy, and I need to tone down the touchy problem.

Im new to linux but if you put it in writing I will follow along.

blu.gecko :???:

---

### Post by ming0 on 2005-04-03
It depends on the file /etc/X11/XF86Config-4

I would have a look at it:
 ```
gedit /etc/X11/XF86Config-4
``` 
You should find a section that has some settings for a touchpad (I think).

If you want to, you could post your /etc/X11/XF86Config-4 here, and we could look at it.


Otherwise, you will need to use:
 ```
sudo gedit /etc/X11/XF86Config-4
```
to change it, but beware, you could end up with no GUI if you mess things up :) 

So, I guess you should use the following command to back the original up!

 ```
sudo cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.bak
```
Good Luck!

---

