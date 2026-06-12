---
title: "Wemcam not showing up"
date: 2015-05-26
forum: Hardware
---

### Post by LaJuan on 2015-05-26
Hi,

I've had Ubuntu 14.04 LTS running on my Lenovo T430s a while now and I went to install Cheese Webcam Booth so I can use it and noticed, the webcam is not showing up in my hardware list. I checked the bios to see if something there that needed to enable it but, Ubuntu does not see the webcam. Before I had windows running on it and the webcam worked. So, I'm at a complete lost how to get it working now using 14.04 LTS. Any suggestions? 

:confused::confused::confused::confused::confused:

---

### Post by TheFu on 2015-05-27
Is your webcam supported by linux? Which chips does it use? Are there any drivers for it under Linux?
[http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware](http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware)

And I'd check that it isn't just disabled in the BIOS too.

---

### Post by LaJuan on 2015-05-28
I checked in the BIOS and not disabled. The camera and mic is internal so I'm assuming at this point, they are not supported by Linux but, the laptop is which is confusing me. I'll checkout the link you posted and let you know what I find.

---

### Post by TheFu on 2015-05-29
A laptop is just hundreds of "parts" - any of those parts may not be supported by the Linux kernel, at least when the part is brand new to the world.

For example, the touchpad on my netbook wasn't supported when 14.04 was released. 14.10 and later does support it. I refuse to run any non-LTS releases, so whenever a new kernel gets installed, I have to manually run a script to get the driver code, compile it, and install it. It is a trade off I'm willing to put up with until 16.04 (or I get the courage to install a HW-compatibility kernel).

There is hope.

---

