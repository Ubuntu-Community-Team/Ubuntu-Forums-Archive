---
title: "GL Slow and Causes System Crash"
date: 2005-07-14
forum: Hardware &amp; Laptops
---

### Post by theubergeek on 2005-07-14
I installed the Nvidia drivers for my PCI GeForce4 MX 400 as per the instructions of ubuntuguide and have the following problems:

Glxgears told me that I could only pull 613 FPS, which is BS, as Xandros placed me MUCH higher with it's stock driver.

When I played GL games like Glest and Legends, my entire system froze after 1 minute of gameplay (and ctrl, alt, backspace did nothing).

I then tried to install the Nvidia driver from Nvidia's website. That seemed to work, up untill I found out that GL rendering was totally broken. 

I reinstalled the Linux-restricted-modules and nvidia driver from synaptic only to find out X won't start. I reverted the driver back to "nv" and now here I am stuck without GL.

Can anyone tell me how to fix this?

---

### Post by darkazurka on 2008-05-28
Glest for me (3.0.0) is very slow. I use it on a card that is similar to yours Geeforce2 MX 400.

I only got bad experiences (computer not working for weeks) by changing stuff in x.org configuration files, and reinstalling the nvidia graphics driver. Although if you have much time available, do all possible things, but analyse them so you understand what you do.

---

