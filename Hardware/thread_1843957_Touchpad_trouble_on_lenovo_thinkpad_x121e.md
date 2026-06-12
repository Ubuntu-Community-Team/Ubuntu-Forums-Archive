---
title: "Touchpad trouble on lenovo thinkpad x121e"
date: 2011-09-14
forum: Hardware
---

### Post by martinyt on 2011-09-14
Hi. 

The touchpad on my x121e is not working properly - and I have found I solution here:

[http://askubuntu.com/questions/60237/how-do-i-set-up-the-touchpad-of-a-lenovo-x121e](http://askubuntu.com/questions/60237/how-do-i-set-up-the-touchpad-of-a-lenovo-x121e)

But I don't quite understand what they have done, and so I would like to start this thread.

I have downloaded the driver xf86-input-synaptics-1.4.1-1-x86_64.pkg.tar.xz, which I think is a newer driver than what comes with ubuntu. But I am not sure how to install and configure to make this work.

Has anyone done this or would like to guide me in this process? 

Thanks!

---

### Post by martinyt on 2011-09-30
The solution was easy - just unpack the 1.4 driver and use the .so to replace your .so file. I just missed that. I works - the touchpad is much better.

---

### Post by MorrisseyJ on 2011-10-04
This is great, but can you tell me where the synaptics driver is currently located on my machine. 

Thanks.

---

