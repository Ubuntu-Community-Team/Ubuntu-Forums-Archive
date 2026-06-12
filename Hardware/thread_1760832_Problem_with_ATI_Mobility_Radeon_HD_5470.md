---
title: "Problem with ATI Mobility Radeon HD 5470"
date: 2011-05-17
forum: Hardware
---

### Post by EmasXP on 2011-05-17
Hi!

I am not a native english speaking person, and I am not even sure how I would explain this in my own language. But Im going to give it a try.

I have a laptop with an ATI Mobility Radeon HD 5470 graphics card. When I watch videos, it feels like the video has a very low FPS. Plus the image often flickers. I have attatched an example image of this flickering effect to this post. It is not a screenshot, I have just used gimp to mimic the effect. The same thing happens when I scroll in a web browser.

I have installed the proprietary hardware drivers that Ubuntu wants me to install. I have also downloaded the Catalyst drivers. I am not sure if I have configured it right though.

By the way, I had Windows 7 on this laptop before I installed Ubuntu 11.04, and I had no problems there. I have not used any other Ubuntu installs on this laptop so I cant say if this is 11.04 specific.

---

### Post by ghostborg on 2011-05-17
I had an ATI HD3200 onboard graphics and this worked for me.
Everything seemed slow with the desktop and had choppy video.
Try disabling "Sync to VBlank" in OpenGL.
You will find this in the Compiz Config Settings Manager under the General category.
You may have to install Compiz config settings manager in Synaptic package manager, also but not sure, it may be in the Ubuntu software center and search for Compiz.

Also in the ATI cataylst control center I enabled Tear-free. I had that problem but you might not.

Hope that works for you.

---

### Post by EmasXP on 2011-05-17
> **ghostborg said:**
> I had an ATI HD3200 onboard graphics and this worked for me.
Everything seemed slow with the desktop and had choppy video.
Try disabling "Sync to VBlank" in OpenGL.
You will find this in the Compiz Config Settings Manager under the General category.
You may have to install Compiz config settings manager in Synaptic package manager, also but not sure, it may be in the Ubuntu software center and search for Compiz.

Also in the ATI cataylst control center I enabled Tear-free. I had that problem but you might not.

Hope that works for you.

Wow! Everything works great now. Thanks a lot! :)

---

### Post by Good_Newz on 2011-05-23
Awesome. Also removing vblank option solved my compiz slowdowns. Thanks.

---

### Post by kfoe on 2011-05-24
Still very low fps for me 
```
$ fgl_glxgears
Using GLX_SGIX_pbuffer
1801 frames in 5.0 seconds = 360.200 FPS
1940 frames in 5.0 seconds = 388.000 FPS
1943 frames in 5.0 seconds = 388.600 FPS
1945 frames in 5.0 seconds = 389.000 FPS
1937 frames in 5.0 seconds = 387.400 FPS
1941 frames in 5.0 seconds = 388.200 FPS
```


My card is: 
```
lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series

```

Thanks

---

