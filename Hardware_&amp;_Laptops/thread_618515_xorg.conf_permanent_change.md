---
title: "xorg.conf permanent change"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by zvezdogled on 2007-11-20
Hi,

i have ubuntu gutsy and in order for my display to work properly i had to modify xorg.conf. Everything cool until i restart the computer and when it turns up again the displey is again at ressoulution of 640x400 and i have to make the changes to xorg.conf again. 

so my question is how to make the change permanent

thankyou

---

### Post by taurus on 2007-11-20
What video card do you have and have you installed a driver for it?  Can you post your /etc/X11/xorg.conf?

Applications -> Accessories -> Terminal
```
cat /etc/X11/xorg.conf
```

p.s.  Are you still running Edgy?

---

### Post by zvezdogled on 2007-11-20
no its other laptot that i don't have hire with me 
as i said i installed gutsy alternate and i added the restricted nvidia driver.
And the problem is not xorg.conf its just that each time i reboot it is overwritten so i have to change it again in order to work properly.

---

### Post by JC Casiano on 2007-11-21
Ok, normally xorg.conf does not just rewrite itself.  Question: is xorg.conf the same as when you shutdown?  I had some issues with xorg.conf, and on my Sony GRT100 this would most likely cause the boot resolution to be lower than the LCD resolution.  What I ended up doing was commenting out all resolutions in the "Monitor" section other than the ones that I found useful, and then setting the only "Mode" in the screen section to the highest mode my LCD would support natively, which is 1400x1050.

---

