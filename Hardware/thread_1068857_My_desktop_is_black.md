---
title: "My desktop is black"
date: 2009-02-13
forum: Hardware
---

### Post by eyezdk on 2009-02-13
Hey all. 

I installed kubuntu. and i just... "******" my desktop, 

I can log in, but all i can se is my curser just efter i login. 

any one can tell how to reset it back to "normal" 

Thx

---

### Post by SuperSonic4 on 2009-02-13
Sounds like a video card problem? What card do you have?

If you can drop into terminal by pressing ctrl+alt+f2 and logging in that way post ```
cat /etc/X11/xorg.conf
```

---

### Post by eyezdk on 2009-02-13
ahh, its solved now. found some help on the kubuntu forum. 

'kwriteconfig --group Compositing --key Enabled --file kwinrc false' did the trick for me

---

