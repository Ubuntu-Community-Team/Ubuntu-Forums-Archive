---
title: "Changing video cards"
date: 2009-08-17
forum: Hardware
---

### Post by shahgols on 2009-08-17
Hi everyone,

I have Kubuntu 9.04 and a Geforce 6800 XT.  I just ordered an ATI 6700 and a new monitor.  I know that once I get and install the new video card and monitor, I need to rerun the video configuration utility, but how is that done?  Also, when I first boot up Kubuntu after the hardware installation, what should I expect?  Will I be kicked into a command prompt or will the system just crash or should I expect something else?  Thanks in advance.

---

### Post by markbuntu on 2009-08-17
6700??? are you sure of that number?

Anyway, changing graphics cards can be pretty painless if you follow a few simple steps. 

First, remove completely any proprietary driver you have installed before you change out the card.
Replace the card.
Next, boot into the recovery kernel (grub) and use the fix x option and then continue. This will load the generic VESA driver which will work with any graphics card. 

This should get you to your regular kubuntu desktop where you can make adjustments or change the driver etc.

---

### Post by shahgols on 2009-08-17
OOOPS, I had a brain fart...I have no idea why I put 6700...it is an ATI 4650.  This one to be exact:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814103071]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814103071")

I have two questions regarding your post:

1.  How do I remove the proprietary drivers?  Where is that done from?
2.  Where is the "fix x option"?  

Thanks!

---

### Post by markbuntu on 2009-08-18
It depends on how you got the driver you were using. If you got it from nvidia then there is ususally a script somewhere to remove it. If it is a package you got with hardware manager you can remove the nvidia packages with synaptic package manager. If you used envy then use envy to remove it.

The fix x option pops up in a menu when you boot into the recovery kernel which you can do from grub.

The 4650 will work just fine with the driver from ati.

---

