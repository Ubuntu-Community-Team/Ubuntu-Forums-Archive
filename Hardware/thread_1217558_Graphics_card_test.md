---
title: "Graphics card test"
date: 2009-07-19
forum: Hardware
---

### Post by jazb0 on 2009-07-19
I am concerned that my graphics card is getting ready to go out on me, does anybody have any suggestions of a way to test it? (I'm pretty new to linux)

---

### Post by overdrank on 2009-07-19
> **jazb0 said:**
> I am concerned that my graphics card is getting ready to go out on me, does anybody have any suggestions of a way to test it? (I'm pretty new to linux)

Hi and welcome, what is the model of the graphics card and the version of Ubuntu you are using? What are the symptoms that lead you to believe you card is failing?
You may use the command ```
lspci | grep VGA
```in the terminal to identify your graphics.
The terminal is located under applications, accessories.

---

### Post by jazb0 on 2009-07-19
Thank you! My graphics card is an nvidia geforce 440 go (in a toshiba laptop), and I'm using v9.04 of Ubuntu. Well, my screen has had different display problems for a while including a funny grey and white screen that looks like clouds and then turns all white, and columns flickering, etc. (Sorry, it's hard to describe it.) The only way to get out of either is with a hard reboot. I installed Ubuntu on my hard disk yesterday, and when I started up this morning the screen flickered in columns and then hung. But when I use the LiveCD everything works fine. I know that my hard dive is failing, so I'm trying to decide if that is the only problem. I hope all that makes sense!

---

### Post by overdrank on 2009-07-19
I am sorry I can not offer any help but I have seen many threads on the forums of nvidia geforce 440 issues on Jaunty.

---

### Post by jazb0 on 2009-07-19
If it was an OS issue wouldn't it show up with the livecd? (I've had a slight graphics issue for over a year). I just wish there was a way to test the card...

---

