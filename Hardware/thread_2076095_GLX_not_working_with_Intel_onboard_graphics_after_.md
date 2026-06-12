---
title: "GLX not working with Intel onboard graphics after nvidia  cuda drivers installed"
date: 2012-10-25
forum: Hardware
---

### Post by gorkiana on 2012-10-25
I have a Dell precision T1600 and I have an nvidia Quadro 2000 graphics card I want to use only for CUDA computing. For that I intend to use the onboard Intel graphics card.

The problem I am having is that once I install nvidia drivers I loose openGL capabilities with my Intel onboard graphics card.

This is the output of lspci -nn | grep VGA:

00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 Processor Family Integrated Graphics Controller [8086:010a] (rev 09)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF106GL [Quadro 2000] [10de:0dd8] (rev a1)

Can anyone help me with this?

Thank you.

---

### Post by mauricio_matera on 2013-10-05
I had the same problem but I think I could fix it: look how I did it at my blog  [http://mauricio-matera.blogspot.com.ar/2013/10/configuring-cuda-in-ubuntu-1304.html](http://mauricio-matera.blogspot.com.ar/2013/10/configuring-cuda-in-ubuntu-1304.html)  

Best 
M

---

