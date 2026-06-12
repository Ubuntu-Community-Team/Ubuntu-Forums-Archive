---
title: "integrated camera on XPS 1530"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by phishlax on 2008-01-20
Hey I have an XPS 1530 and I have installed camorama but when I try to run it it says could not connect to video device (/dev/video0/). Please check the connection. Any suggestions on how to get this to work? I would really like to be able to use my integrated camera!

---

### Post by phishlax on 2008-01-20
I have posted on here 7 times and no one has even responded to my problems once...does anyone on here ever help anyone???? I heard the Ubuntu community was supposed to be really helpful

---

### Post by sygram on 2008-03-01
Hi there,

i have just received mine. I have the same problem with the camera as well as the microphone is not working ...

Any luck ?

Regards,

Leon

---

### Post by sygram on 2008-03-10
i have managed to find a link :

[http://64.233.183.104/search?q=cache:Z02z0m8jG1MJ:www.nervous.it/2007/11/linux-dell-xps-m1330/+http://www.nervous.it/2007/11/linux-dell-xps-m1330/&hl=el&ct=clnk&cd=1&gl=gr&client=firefox-a](http://64.233.183.104/search?q=cache:Z02z0m8jG1MJ:www.nervous.it/2007/11/linux-dell-xps-m1330/+http://www.nervous.it/2007/11/linux-dell-xps-m1330/&hl=el&ct=clnk&cd=1&gl=gr&client=firefox-a)

it seems that this guy has figured it out, but i haven't tried it. I am not sure whether to wait for the official kernel update ...

Thanks

Leon

---

### Post by sdennie on 2008-03-10
I think the problem is that camorama only knows how to use V4L and, if your camera is the same as the one in the Dell m1330, it uses V4L2.  You can see if the webcam is working or not by running "gstreamer-properties" in a terminal and then in the Video tab selection V4L2 and hitting the test button.  I don't really know what the difference between V4L and V4L2 is but, things like Ekiga support V4L2 so, the camera will work just fine there.

---

### Post by jespdj on 2008-03-10
Maybe this helps: [http://ubuntuforums.org/showthread.php?t=673204](http://ubuntuforums.org/showthread.php?t=673204)

There's a [Dell Ubuntu Support](http://ubuntuforums.org/forumdisplay.php?f=256) forum right here.
Also see the [Dell Linux wiki](http://linux.dell.com/wiki/index.php/Ubuntu_7.10).

The webcam on my M1330 works with Skype and with for example cheese:
```
sudo apt-get install cheese
```

---

