---
title: "New USER to UBUNTU, got 1 question"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by scossio on 2007-08-10
Okay So I finally installed Ubuntu on my laptop. But my display settings is not what i think its suppose to be at. Everything is not as crisp & clear as i thought it would be. I think it has something to do with the visual settings but I dont know how to get to them.

My Laptop is currently on 1024 X 768
Refresh Rate: 60 Htz
Rotation Normal.

How can i make sure though its 32 bit instead of 16? Im not getting the picture quality im suppose to, can any one shine some light on this issue?

---

### Post by jacob01 on 2007-08-10
i don't think ubuntu even supports 16 bit but not sure
are you using the correct drivers

---

### Post by kast on 2007-08-10
go to **System -> Preferences -> Screen resolution** i think the bit options are under there. you could also try running **dpkg-reconfigure xserver-xorg** if you think that the install didn't capture the right settings for your hardware.

---

### Post by kostkon on 2007-08-10
I think you don't use the native resolution of your laptop's TFT monitor. The best thing you can do is to boot in Windows, and see what resolution it is used there. If you don't have Windows, you have to check the manual for your laptop or the net to see what is the native resolution.

Then just go to **System -> Preferences -> Screen resolution** and change the resolution there accordingly.

Or as *kast* said, you can try to reconfigure your X server, it will maybe then pick up the right settings for your monitor.

First, better try to find which is the native resolution. If you can't find any info and you want help on how to reconfigure X, then just ask.

---

### Post by pbcartwright on 2007-08-10
you might try to install 915resolution. That got me 1280X1024 resolution..
sudo apt-get install 915 resolution

---

### Post by scossio on 2007-08-11
> **pbcartwright said:**
> you might try to install 915resolution. That got me 1280X1024 resolution..
sudo apt-get install 915 resolution

I Was able to install it just like you said, but when I go to the resolution it still gives me 1024x768
I rebooted & still the same thing. How do I get to that resolution.....to make things more smoother and a crisper picture.?

---

