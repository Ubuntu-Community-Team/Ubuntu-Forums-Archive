---
title: "Getting Compiz to work on a zd7245ea finally (Screen Saver problem)"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by Llewellyn01 on 2007-12-09
Hi,

I just wanted to share this for if someone else gets this problem, after spending time over the last three weeks reading up on Ubuntu and installing Compiz I had a odd problem with the screen saver never working.

The screen would go black but the screen saver would not work.

While surfing the net and looking up the problem I came across this blog at:

[http://forlong.blogage.de/list/category/88](http://forlong.blogage.de/list/category/88)

In the troubleshooting section I came across this command in terminal:

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

It worked and the screen saver now works, I know its a little thing but for a newb like me to Linux I stuck with looking up the problem and finally found an answer.

If anyone else has this laptop might be worth giving this a try if you get the screen saver problem like I did.

Now I can enjoy the rather cool 3D effects :-D

Cheers

Rich

---

