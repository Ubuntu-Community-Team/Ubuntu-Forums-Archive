---
title: "Intel Video Drivers (for GMA 4500MHD)"
date: 2012-09-26
forum: Hardware
---

### Post by FiberOptix on 2012-09-26
Hi all, I'm running Ubuntu 10.04.

So recently a game I was trying to run complained that I lack support for Shader Model 3.0 (SM3). Honestly, I couldn't remember what video card this Dell Inspiron 1545 laptop had so after I "lspci | grep VGA" the answer comes back as: 

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

The [Inspiron Wikipedia page]("https://en.wikipedia.org/wiki/Dell_Inspiron#Inspiron_1545_.28Inspiron_15.29") confirms this, as it seems the card in question is the Intel [GMA 4500MHD]("https://en.wikipedia.org/wiki/GMA_4500MHD#GMA_X4500"). Now, I've read that the GMA 4500 MHD supports DirectX 10 and Shader Model 4.0 (SM4). It appears from lsmod that I'm using the i915 module.

Do I really have the best drivers installed for the card considering that it's supposed to support SM4 and appears as though I'm unable to use SM3?

If anybody can help I'd really appreciate it. Let me know if you'd like me to provide more information.

---

