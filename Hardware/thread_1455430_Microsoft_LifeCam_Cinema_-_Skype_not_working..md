---
title: "Microsoft LifeCam Cinema - Skype not working."
date: 2010-04-15
forum: Hardware
---

### Post by jbisetto on 2010-04-15
I've read a lot of posts that say this web cam will work right out of the box. I can see the cam on Cheese, but not on Skype. When I test the cam in Skype options the light on the cam turns on but there's no picture.

I tried changing the launch command but that doesn't work. If I use this when I try to test the web cam in Skype it shuts down Skype

```
bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'
```I also found this thread, 

[http://ubuntuforums.org/showthread.php?t=1336901](http://ubuntuforums.org/showthread.php?t=1336901)

but it doesn't indicate how the issue was resolved.

Any help would be appreciated.

---

### Post by jbisetto on 2010-04-19
Problem solved itself as a side effect of updating my video card drivers. WooHoo!!

---

### Post by MSPdwalt on 2011-08-31
How do you like the cam? Does it just work or does it work well in Ubuntu?  What version of Ubuntu are you on?

---

