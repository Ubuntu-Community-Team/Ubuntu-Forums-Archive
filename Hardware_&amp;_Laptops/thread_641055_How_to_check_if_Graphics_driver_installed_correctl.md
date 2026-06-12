---
title: "How to check if Graphics driver installed correctly?"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by magnifica on 2007-12-14
Hi all.  Firstly, I'm very new to Linux; installed yesterday. I'm quite impressed so far with its simplicity of use and ease of application installation.  I hope to continue using it!

My question is about drivers.  Basically everything seems to be working pretty well (was confused about not having to install drivers!) except that the graphics while I play a video seems to be a bit more grainy/blocky than what I'm used to.

My Graphics card is a Intel Graphics Media accelerator 900 (i think!).  How can I check to make sure this is installed?  

I looked in the device manager already and see this:

[[IMG]http://img156.imageshack.us/img156/8429/screenshotuu2.th.png[/IMG]](http://img156.imageshack.us/my.php?image=screenshotuu2.png)

Also, I checked the screen resolution already and it seems to be correct.  

Any help would be appreciated!  Thanks!

---

### Post by Dark_Stang on 2007-12-14
Run glxgears and if you're gears aren't all choppy and crappy looking it worked.

---

### Post by magnifica on 2007-12-14
Thanks for your reply Dark_Stang

Yup, I actually did that already (I did search before posting!) and the gears look fine.  

Is there another way to check?  (I'm not convinced that that's the best video picture quality I can get!  :(  )

---

### Post by Dark_Stang on 2007-12-14
Other ways would be to play graphically intense games. Do you have your card setup for 24 bit or 16 bit color? If it's starting to feel slow you could drop it to 16 bit to get some more speed out of it.

---

### Post by magnifica on 2007-12-15
Oh!  I think I worked it out!  I've been watching in VLC.  I looked around in the Video settings and turned "deinterlacing" to "blend" and it looks a lot better!

In VLC:  Video>Deinterlace>Blend

Thanks for your reply Dark_Stang and everyone for talking your time to help others!  I hope to be able to return the favour sometime.

Cheers!  :guitar:

---

### Post by Dark_Stang on 2007-12-15
You can return the favor by helping others out. Take it easy.

---

