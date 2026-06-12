---
title: "Lock screen -- screen goes blank"
date: 2009-12-12
forum: Hardware
---

### Post by shashi_ubunu on 2009-12-12
I have a HP Laptop loaded with 9.10 64-bit. 

If i do "Lock Screen" , after some time the screen goes completely blank and it won't show the login screen. I tried by pressing multiple keys, but i am not getting the login screen. Hard rebooting is the only for me to get back into my work.

Please anyone tell me how can i solve this issue ?

7.04 ,7.10, 8.04, 8.10 ,and 9.04 were perfectly working fine.

I am facing this issue only with 9.10.

---

### Post by chenxiaolong on 2009-12-12
Could you post the output of

```
dmesg | tail
```

---

### Post by shashi_ubunu on 2009-12-12
I have attached the dmesg output.

Thanks.

---

### Post by chenxiaolong on 2009-12-12
It's a bug (not too common) in the package "gnome-screensaver" that hasn't been fixed yet. You can use a different screensaver/screen-locking program though, like xscreensaver, but you will have to remove "gnome-screensaver".

sudo apt-get remove gnome-screensaver
sudo apt-get install xscreensaver*

Then, restart your computer, and configure the settings with System Menu > Preferences > Screensaver

Hope this works for you. 

By the way, I just noticed that you said your computer was by HP and that's what I had to do for my mom's HP laptop.

---

### Post by shashi_ubunu on 2009-12-12
I did what you mentioned.

But it's not working.

screen goes blank.

---

