---
title: "Grainy / Blurrred / Distorted screen with nv 1024x768 - 800x600 fine"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by Who on 2008-04-20
I have some weird screen distortion going on using the nv driver, and I am reluctant to use the nvidia one because it breaks suspend for me...

The display looks like it has been 'greyed out' in a windows 95 style - except the cursor looks fine.... What I mean by this: the text looks a bit like it has had a layer of dots placed over it and so it is hard to read - it gives a blurred and grainy appearance. 

This is on a Samsung X10 with an nvidia GeForce FX Go 5200 64mb. Other people seem to have this working on other distros in the past. I am using 8.04 daily build from 20th April

The vesa and nvidia drivers can do this fine at all resolutions. The nv driver looks fine at 800x600 but terrible at 1024x768.

I have tried turning off the composite extension, and not loading the glx module, but no love. I installed with WUBI.

Any help would make me _very_ happy!

Who

---

### Post by nicedude on 2008-04-21
I had trouble with Ubuntu's Nvidia driver with my 8400M in my acer laptop. Then I found a program called "envy" whose sole function is to download the newest driver for your particular chipset from Nvidia and then compile and install it for you. There are people that it doesn't work for, but it sure worked for me. Thought I would tell you about it in case you hadn't heard of it. You can just google envy to find it. Hope you get your situation resolved.

---

### Post by Who on 2008-04-21
> **nicedude said:**
> I had trouble with Ubuntu's Nvidia driver with my 8400M in my acer laptop. Then I found a program called "envy" whose sole function is to download the newest driver for your particular chipset from Nvidia and then compile and install it for you. There are people that it doesn't work for, but it sure worked for me. Thought I would tell you about it in case you hadn't heard of it. You can just google envy to find it. Hope you get your situation resolved.

Thanks, but I'm trying to avoid the Nvidia driver because of the suspend issues. I will try envy in case this fixes them, but I don''t have high hopes :P

Anyone with any nv related ideas?

---

