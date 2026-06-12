---
title: "Laptop camera stopped working"
date: 2012-08-01
forum: Hardware
---

### Post by rickbeton on 2012-08-01
Hi

My old Dell XPSM1330 has a built-in laptop camera which has been working fine for years. I upgraded to 12.04 in April and everything was (I think) working fine then.

Now, the camera doesn't work; I think it's a software problem but I need some help to find out what.

/var/log/dmesg includes these lines

```
[    4.396255] Linux video capture interface: v2.00
[    4.398716] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:7670)
[    4.399784] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    4.400474] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[    4.400477] uvcvideo: Failed to initialize the device (-5).
[    4.400527] usbcore: registered new interface driver uvcvideo
```

I checked lshw and lspci but neither have any mention of the webcam device.

Thanks for any advice,
Rick

---

### Post by toastbrot888 on 2012-08-09
I have exactly the same problem - same laptop, same Ubuntu version, and roughly the same time of the first occurence of the problem. So, I suppose something in relation with a recent Ubuntu update broke the webcam driver somehow. I don't have a solution. Googling around just takes me to solutions like manually compiling the webcam drivers, but always with the hint that at any version of Ubuntu above xx.xx, this particular webcam should work out of the box (which it did until some days ago). I think that at least for some time I will wait for an update which solves the problem. Nevertheless, any hint about how to solve this problem is greatly appreciated.

---

