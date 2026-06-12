---
title: "SLI queston"
date: 2012-12-21
forum: Hardware
---

### Post by majorburt on 2012-12-21
alright, so i have these two graphics cards just sitting around and i'm wondering if i can SLI them together. they are as follows:

1:
BRAND: MSI
MODEL: N460GTX twin frozer II
GPU: GeForce GTX460
MEMORY SIZE: 768MB GDDR5

link: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814127519](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127519)

2:
BRAND: GALAXY 
MODEL: 60XMH6HS3HMW
GPU: GTX 460
MEMORY SIZE: 768MB GDDR5

link: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814162058](http://www.newegg.com/Product/Product.aspx?Item=N82E16814162058)

i know nothing about SLI(ing) video cards together so sorry if its an obvious answer.

thanks and good hunting.

---

### Post by haqking on 2012-12-21
> **majorburt said:**
> alright, so i have these two graphics cards just sitting around and i'm wondering if i can SLI them together. they are as follows:

1:
BRAND: MSI
MODEL: N460GTX twin frozer II
GPU: GeForce GTX460
MEMORY SIZE: 768MB GDDR5

link: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814127519](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127519)

2:
BRAND: GALAXY 
MODEL: 60XMH6HS3HMW
GPU: GTX 460
MEMORY SIZE: 768MB GDDR5

link: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814162058](http://www.newegg.com/Product/Product.aspx?Item=N82E16814162058)

i know nothing about SLI(ing) video cards together so sorry if its an obvious answer.

thanks and good hunting.


Yes it is capable and should work.

[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-25.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-25.html)

[http://www.geforce.com/hardware/technology/sli/faq](http://www.geforce.com/hardware/technology/sli/faq)

Your GPU's are the same so no problem there, and memory are the same so shouldnt be an issue with cross brands.

The Linux proprietary driver works well for me in Slackware and other Distros.

You might want to wait to see if someone with direct SLI experience in Ubuntu chimes in though but i think you should be fine.

---

### Post by majorburt on 2012-12-21
> **haqking said:**
> Yes it is capable and should work.

[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-25.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-25.html)

[http://www.geforce.com/hardware/technology/sli/faq](http://www.geforce.com/hardware/technology/sli/faq)

Your GPU's are the same so no problem there, and memory are the same so shouldnt be an issue with cross brands.

The Linux proprietary driver works well for me in Slackware and other Distros.

You might want to wait to see if someone with direct SLI experience in Ubuntu chimes in though but i think you should be fine.

what little i do know about SLI is that you have to have VERY similar video cards for it to work. how similar would the video cards have to be though?
 i know you couldn't SLI a GTX 460 and a GTX 560 together, but what about 2 GTX 460s with different memory sizes or bus speeds?

---

### Post by haqking on 2012-12-21
> **majorburt said:**
> what little i do know about SLI is that you have to have VERY similar video cards for it to work. how similar would the video cards have to be though?
 i know you couldn't SLI a GTX 460 and a GTX 560 together, but what about 2 GTX 460s with different memory sizes or bus speeds?

Like i said, yours should be fine as they are same GPU and memory.

From the links i posted:

> **Can I mix and match graphics cards that have different GPUs?**

  No. For example, an XXXGT cannot be paired with a XXXGTX in an SLI configuration.
    **Can I mix and match graphics cards from different manufacturers?**

  Using 180 or later graphics drivers, NVIDIA graphics cards from  different manufacturers can be used together in an SLI configuration.  For example, a GeForce XXXGT from manufacturer ABC can be matched with a  GeForce XXXGT from manufacturer XYZ. 
    **Can I mix and match graphics cards if one of them is overclocked by the manufacturer?**

  Yes. A GeForce XXXX GTX that is overclocked can be mixed with a standard clocked GeForce XXXX GTX. 
    **Can I mix and match graphics cards with different sizes of memory?**

  When purchasing a second graphics card, you should try to match the  memory size so that you are ensured full value and performance from your  purchase. However, while it is not recommended, NVIDIA does offer the  flexibility to run graphics cards with different sized memory by using  CoolBits. Using CoolBits (value set to 18), you can force both of the  cards to use the lower of the two memory sizes and operate them together  in SLI mode. When dissimilar memory sizes are enabled to work together  using CoolBits, the effective memory size for each card becomes the  smaller of the memory sizes.


---

### Post by majorburt on 2012-12-22
> **haqking said:**
> Like i said, yours should be fine as they are same GPU and memory.

From the links i posted:

thanks a lot haqking!!!

---

### Post by haqking on 2012-12-22
> **majorburt said:**
> thanks a lot haqking!!!

You're welcome.

Peace

---

