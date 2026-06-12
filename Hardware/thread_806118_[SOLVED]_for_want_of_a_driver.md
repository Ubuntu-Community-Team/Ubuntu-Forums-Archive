---
title: "[SOLVED] for want of a driver?"
date: 2008-05-24
forum: Hardware
---

### Post by Kain000 on 2008-05-24
hey everyone,

so heres what's goin on,  

my system seems to be working fine for everyday things with ubuntu's native drivers, however I cannot enable any gnome effects or run the art manger to get any themes.  the only reason I wouldn't be able to change things like this would be that I am using the native driver instead of one for the radeon mobile 9000 card.  

any advice?
thanks
-sean

---

### Post by komputes on 2008-05-24
Hi Sean,

I have a similar radeon issue in Ubuntu 8.04 (which is what I assume you're using). Can you test something for me. If you have a Live CD of Ubuntu 7.10 can you pop it in and see if you can enable "gnome effects" as you say by going into System > Preferences > Appearance then the Visual Effects tab. How Far down Can you bring it in Ubuntu 7.10 compared to 8.04.

---

### Post by Kain000 on 2008-05-24
hey thanks for the quick reply
so i put in a live cd for 7.04 I had arround, (feisty fawn) and the native drivers in it worked for the gnome effects.

---

### Post by komputes on 2008-05-25
So it is what I thought. The changes in Hardy and Xorg makes it that it doesn't allow Radeon cards to enable desktop effects. Compiz apparently checks against a list to see what is valid and what isn't and apparently between 7.10 and 8.04  that list changed putting Radeon cards on the blacklist.

Many people have reported this to work for them:

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager 
```

Please let me know if this works:
[http://ubuntuforums.org/showpost.php?p=4777383&postcount=1](http://ubuntuforums.org/showpost.php?p=4777383&postcount=1)

---

### Post by Kain000 on 2008-05-25
hey thanks man, i've got it working now and looks a lot better.

thanks for the help.   

what hardware are you running with?

---

