---
title: "A challenge to those skilled in Ubuntu"
date: 2011-01-06
forum: Hardware
---

### Post by Nathanv.1 on 2011-01-06
Many may know of the Kinect hack used to use the Kinect as a potential camera and I may assume you have also heard of the TISCH project done to use this as a multi touch device for photos. Well I have searched the internet up and down and even though there is already a thread on here about this problem, no one seems to be replying to my last message. So I ask all of you up to the challenge to tell me how I can do this. I am able to view it in glview but when trying to use the ```
touchd -Vf
``` command I only get the response of ```
user@user-laptop:~$ touchd -Vf
touchd - libTISCH 1.1 image processing layer
(c) 2008 by Florian Echtler <echtler@in.tum.de>
Caught runtime exception:
  No IIDC camera with requested index found.
Cleaning up.. done. Goodbye.
```

Please help me out here. Thank you.

---

### Post by shaszard on 2011-01-07
**edited** not sure now after doing more reading.  Floe mentions that libfreenect isn't available on PPA repository, so I assume that the build that you are using does not support Kinect.  (short answer sorry!)

---

### Post by Nathanv.1 on 2011-01-07
Well their site says it works: [http://tisch.sourceforge.net/]("http://tisch.sourceforge.net/"). I may just be understanding it wrong.

---

### Post by @work on 2011-01-10
I've seen the same problem. This is however for as far as I can see a problem with the libtisch package u are using. It doesn have the kinect (pre)compiled in it. You should also check google on the tisch.touchd file in youre home dir. You can change the 1 to five (I need to do this on the shadow to otherwise its defaulting back to 1) to tell youre pc to use the kinect instead of webcam or some.

However. I cant get the right ldflags and lcflags for compiling this package. Besides that the depthJS chrome add-on isn't working aswell. glview as u describe also works fine here. I feel some other "general" package is missing. If anyone has any idea please let us know! (All the libglutfree3 and libusb packagages I thought of have been checked) perhaps a path missing?

I also installed libtisch2. This asks for a tisch.touchd.xml config file which I dont have and can't find. If someone has this perhaps we can skip the original issues ;-)

hope to see some replies on this subject.

---

### Post by @work on 2011-01-11
I got it work -arounded.

install libtisch2

run

touchd -V -c /usr/share/libtisch/kinect.xml

& demo

---

### Post by Nathanv.1 on 2011-01-24
well thanks for replying and sorry for the long wait in reply but where or what coding do I need to do in order to install libtisch2?

---

### Post by IcarusR on 2011-01-25
If you'd used google you too would have found this

[http://groups.google.com/group/openkinect/browse_thread/thread/bb16faa5318f3b59]("http://groups.google.com/group/openkinect/browse_thread/thread/bb16faa5318f3b59")

---

