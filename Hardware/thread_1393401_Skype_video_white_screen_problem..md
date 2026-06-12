---
title: "Skype video white screen problem."
date: 2010-01-29
forum: Hardware
---

### Post by adroitster on 2010-01-29
I am posting this question after digging through the web for many hours. I have installed the latest skype beta on my lenovo ideapad y550 laptop. I am running ubuntu 9.10 64 bit edition. The webcam works perfectly on my laptop since I have checked it with cheese :D . On skype it works pertially. I suppose it is not the problem with my webcam but probably has to do something with the graphics driver or webcam driver or skype config. Skype can detect my webcam and it can also start the webcam. During skype call the other user can see me which implies that skype is sending the video stream perfectly. The problem is that it wont display the streams from both the side (the sender and reciever) but instead just a plain white screen. Also skype used to work perfectly on previous ubuntu editions . Has the new beta broken the video display? I am using the latest 190.xx (probably 190.53) video drivers from nvidia on my Geforce GT130M video card (yeah this card is insane but some how I managed to make it work). Somebody please help me out with the issue. I can provide more details if needed to solve the issue.

---

### Post by adroitster on 2010-01-31
Alright I found the solution to the problem. Somebody on the forum had it and am just sharing it here to make this thread as solved.

```
export XLIB_SKIP_ARGB_VISUALS=1
skype
```

---

### Post by fdcoiea on 2011-02-28
I'm sorry but i'm still new to Ubuntu, so do I run this in terminal? nothing happens though. Thanks

---

### Post by shinyblue on 2011-03-09
:popcorn: yay! it works again! Thank you!

I've tried so many things from all over the interweb, (all along the same lines) but this one actually worked.

---

### Post by adroitster on 2012-05-31
> **shinyblue said:**
> :popcorn: yay! it works again! Thank you!

I've tried so many things from all over the interweb, (all along the same lines) but this one actually worked.

I am glad it helped you ! :)

---

### Post by Elfy on 2012-05-31
Old thread closed.

---

