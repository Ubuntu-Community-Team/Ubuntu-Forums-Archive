---
title: "some keys not working"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by divali on 2007-03-16
I've just installed Edgy onto a friends Dell Inspiron and all went well untill I went to log in after reboot and found out that some of the letters on the keyboard wouldnt type out some of the letters in the password.
I grabbed my pc ps2 keyboard, plugged it in and then was able to type the password and continue. I then noticed that all the letters that act as the number pad were the ones that wouldn't work,(n-m-h-j-y-u-i etc) even when I fiddled the Num-Lock on and off.
I am 100% sure that is not the problem of the laptop because it was ok before the install.
 Has anyone else had this problem?
How could it be fixed?

---

### Post by teaker1s on 2007-03-16
desktop panel
system>preferences>keyboard


sounds like your keyboard is incorrectly mapped- try the first suggestion, failing that you will need to find out correct keymap requirements and in terminal

```

sudo dpkg-reconfigure xserver-xorg
```

---

### Post by divali on 2007-03-18
Thanks, I'll get back as soon as I can.

---

