---
title: "5 Button Mouse Edgy"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by fernando_lopes_jr on 2006-10-27
I use to be able to make my 5 button mouse work with ubuntu with this 
HOW TO: [https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons](https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons)

now in edgy it doesn't work anymore can same show me how to make it work the way it use to with back, forward buttons in browser.
I would also like to know how can I make my scroll less sensitive the pages pass too quick for me.

Thanks for the help.

---

### Post by EeEk on 2006-10-27
I just added 
```
        Option          "Buttons"               "7"
        Option          "ButtonMapping"         "1 2 3 6 7"
```

to /etc/X11/xorg.conf

Didn't work until after a restart though.

The scroll speed...I have no idea :D

---

### Post by fernando_lopes_jr on 2006-11-01
Doesn't anyone know a way to chage scroll speed?

---

### Post by shaft350x on 2006-11-05
Just wanted to say thanks for having this up here.  I used it on my system and can now use my other two buttons on my mouse that I'd grown so used to using.

Thanks again
~J

---

