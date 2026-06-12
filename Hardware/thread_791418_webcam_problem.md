---
title: "webcam problem"
date: 2008-05-12
forum: Hardware
---

### Post by soty on 2008-05-12
Hi everyone, I'm a newbee on ubuntu. I've just reformated my HP Pavilion dv6000 laptop with Windows Vista and installed Ubuntu. My problem is that I can't access my inbuilt webcam anymore. How do i install it or what do i need to do to start using it?  Please help.

Thanks,

Soty

---

### Post by hermes0710 on 2008-05-12
Can you post the output of ```
lspci
```

---

### Post by imon9 on 2008-05-12
if you are on Hardy Heron (ubuntu 8.04) try install a package through synaptic call  "cheese"

built in webcam is usually newer, so i assume it is supported and detectable...as V4L2

so some v4l1 program will not be able to detect it.... but the is a patch call "flashcam" that could help :)

---

### Post by abhay2101 on 2008-05-13
you run gstreamer-tools

and run video test.it should show video..

---

