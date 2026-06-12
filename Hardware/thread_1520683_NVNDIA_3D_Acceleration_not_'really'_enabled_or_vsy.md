---
title: "NVNDIA 3D Acceleration not 'really' enabled or vsync issue"
date: 2010-06-29
forum: Hardware
---

### Post by nubfilter on 2010-06-29
Hi everyone.

Just coming back to Ubuntu on my desktop to give 10.4 a try.

Running 64-bit 10.4 LTS, NVidia 9800 gtx+ with 2 Dell 24" 1920x1080 monitors.

Right off the bat, I have to say the visual improvements are dramatic I love the new theme as the default.

My issue is that after enabling the Nvidia restricted drivers (current), 
although the following command:
```

glxinfo | grep rendering

```yields: 
```

direct rendering: Yes

```When I drag windows around it is very clear that 3D acceleration is either not 'really' working due to the intense tearing I can see or i need vertical sync. In Win 7 it's super smooth (and you can really tell it's 3D accelerated and sync'd) is there something other than glxinfo I can use to check if it's REALLY enabled? An if this type of checklist would be helpful, I've already followed several guides. 


Also, if someone is feeling extraordinarily helpful: on boot the 'splash' screen after grub no longer looks pretty with the appropriate resolution of 1920x1080 it looks like it's defaulting to 640x480. Do I need to enable some sort of new kernel extension?

I have spent the better part of two days googling but I must have an issue that is not uncommon.

Many thanks in advance,

Kevin

---

### Post by nubfilter on 2010-06-29
Just wanted to add that yes, I have Sync to VBlank checked in NVIDIA Settings.

---

### Post by nubfilter on 2010-06-29
SOLVED!

[http://ubuntuforums.org/showthread.php?t=705781](http://ubuntuforums.org/showthread.php?t=705781)
> 
Open CompizConfig and in the General Section click on the Display  Settings tab, and check the box for SyncToVblank. I'm not sure why the  SyncToVblank in the nvidia-settings has no effect on Compiz.

Someone should link these :)

---

