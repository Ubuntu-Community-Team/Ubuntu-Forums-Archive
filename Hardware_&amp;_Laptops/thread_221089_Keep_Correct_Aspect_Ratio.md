---
title: "Keep Correct Aspect Ratio"
date: 2006-07-22
forum: Hardware &amp; Laptops
---

### Post by Raito on 2006-07-22
I am pretty new here, so if I posted this in the wrong place, or broke a rule, I am sorry.

I got a new widescreen laptop a while ago. But widescreen means problems. This is because I play a lot of games. Getting them to work on Linux is another story.(Believe it or not it actually was possible.) But I want to play fullscreen games unstretched.

I hate it when the aspect ratio is stretched. I know it is possible to set it so that it appears in the 4:3 aspect ratio when I go to 800 x 600 and have black void on both sides rather than stretching. 

I heard you could use a modeline generator. I found one on Google for XFree86. Will this work with X.org? Also if it does work... how and where do I edit the X.org config? 

Thanks

---

### Post by Ziox on 2006-07-22
i don't aoub tmodeline generator, but i can point you to where x.org config file is: it is located at /etc/X11/xorg.conf.

so..in command line it would be

gksu gedit /etc/X11/xorg.conf

---

