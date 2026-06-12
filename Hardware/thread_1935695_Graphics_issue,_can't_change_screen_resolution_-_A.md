---
title: "Graphics issue, can't change screen resolution - Acer Aspire 5736Z"
date: 2012-03-04
forum: Hardware
---

### Post by rasterize on 2012-03-04
Hi,

I installed Ubuntu 11.10 on my Acer Aspire 5736Z laptop. There was a black screen issue during install which I corrected by selecting the nomodeset option. Then after installation I could not boot up (same black screen) so had to use grub to add nomodeset, and Ubuntu boots. I followed this [guide]("http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/"). 

However I cannot change screen resolution, all it gives me is 1024x768, yet my Laptops native resolution is 1366 x 768.

**Graphics Card**
Integrated 3D graphics
Intel®  Graphics Media Accelerator 4500M with up to 1759 MB of Intel® Dynamic  Video Memory Technology 5.0 (64 MB of dedicated system memory, up to  1695 MB of shared system memory), supporting Microsoft® DirectX® 10

I came across a blog comment on [http://laptops-specs.blogspot.com/2011/01/acer-aspire-5736z-specifications.html](http://laptops-specs.blogspot.com/2011/01/acer-aspire-5736z-specifications.html) (the last comment) referring to my exact laptop model which seems to suggest the person has got it working, however I do not understand his guide, in particular 'then go to the none-graphic screen  and log in as root, then run “X -configure”. I do not know what 'none-graphic' screen is, since after setting 'nomodeset' in Grub it boots normally.

Any ideas?

---

### Post by Yellow Pasque on 2012-03-04
> **rasterize said:**
> I do not understand his guide, in particular 'then go to the none-graphic screen  and log in as root, then run “X -configure”.
I'm pretty sure this means, press Ctrl+Alt+F1 to get to the terminal before you log in, and then:
```
sudo service lightdm stop
sudo X -configure
```
I have no idea whether that will work. If it doesn't, pastebin your /var/log/Xorg.0.log

---

