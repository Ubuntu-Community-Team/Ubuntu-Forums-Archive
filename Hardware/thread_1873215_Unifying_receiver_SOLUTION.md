---
title: "Unifying receiver SOLUTION"
date: 2011-11-01
forum: Hardware
---

### Post by CppD on 2011-11-01
Hey folks,

I was frustrated that I couldn't pair more than one device to my logitech unifying receiver, so I reverse engineered their USB protocol and now I have a very low-level, very crude solution to the problem of only being able to pair one device.  tar.gz can be downloaded here:

[http://www.filedropper.com/pyunify](http://www.filedropper.com/pyunify)

basically you just do this:

sudo mount -t debugfs none_debugfs /sys/kernel/debug
modprobe usbmon
cat /sys/kernel/debug/usb/usbmon/u0
sudo modprobe -r usbhid

run the script, turn on and off the device you want to pair (repeat as many times as you want)

and then

sudo modprobe usbhid and it should work.

Let me know what you think!  I just wanted to spread the word because I was VERY frustrated when I found out I couldn't do this on my main OS/after I had soldered a unifying receiver into a usb hub soldered into my old eeepc 701.

Further deets can be found on my blog: [http://tequals0.wordpress.com/2011/11/01/reverse-engineering-logitech-unifying-usb-protocol/](http://tequals0.wordpress.com/2011/11/01/reverse-engineering-logitech-unifying-usb-protocol/)

---

### Post by organsnyder on 2012-03-22
Thanks - it worked great! A couple of notes:

1. The download link on this thread is dead. The blog post has updated download info.

2. I had to run "sudo python PyUnify.py" instead of "sudo PyUnify.py" (as specified in the readme) or even "sudo ./PyUnify.py". The script is missing the #!/usr/bin/python line at the top to allow it to be run on its own.

Otherwise, it worked exactly as advertised and was very easy. I'm typing this post on my new K270 keyboard, which has been paired with the receiver that I already had for my trackball. Thanks again!

---

