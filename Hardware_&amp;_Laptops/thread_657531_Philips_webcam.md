---
title: "Philips webcam"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by dotancohen on 2008-01-03
I have just received a Philips SPC610NC webcam. I installed the gspcav1 driver from [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) however the cam does not work. When I open Kopete -> Settings -> Configure -> Devices all I see is a blue screen. Even running "sudo modprobe pwc" does not activate the camera. What must I do?

Thanks in advance.

---

### Post by icheyne on 2008-01-03
Use the instructions here to test your webcam. Then you know if it's a problem with the drivers or with Kopete.

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Maybe use Easycam to reload the drivers.

---

### Post by dotancohen on 2008-01-04
Thanks. I tested the webcam and there's no /dev/video, so it is a driver problem. However, easycam does not support my camera. The camera is "ID 093a:2601 Pixart Imaging, Inc.".

---

### Post by icheyne on 2008-01-04
Unless your webcam is covered by the drivers in the "[Manual installation instructions]("https://help.ubuntu.com/community/Webcam#head-3e239fe5ae4bb77dbc04efd5465e076190be6958")", then I think you're out of luck. :(

---

### Post by dotancohen on 2008-01-04
According to [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) the cam _is_ supported.

---

### Post by icheyne on 2008-01-05
Sorry I'm out of ideas. :'(

---

