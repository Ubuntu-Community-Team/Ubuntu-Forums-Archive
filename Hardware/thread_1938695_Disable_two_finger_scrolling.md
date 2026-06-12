---
title: "Disable two finger scrolling"
date: 2012-03-10
forum: Hardware
---

### Post by Ethereal Winter on 2012-03-10
Hello,

I'm relatively new to ubuntu and linux. I am wondering how to disable two finger scrolling when you are running ubuntu with xfce. I had to create a script that ran on startup to disable tapping but I am unable to find any information about two finger scrolling.

---

### Post by Toz on 2012-03-10
According to "synclient -l", there are two two-finger options:
> 
VertTwoFingerScroll    
HorizTwoFingerScroll   


Perhaps adding these to your existing script would work:
```

/usr/bin/synclient VertTwoFingerScroll=0
/usr/bin/synclient HorizTwoFingerScroll=0

```

---

### Post by Ethereal Winter on 2012-03-10
Thank you, that solved my problem :)

---

