---
title: "Radeon display drivers"
date: 2018-11-24
forum: Hardware
---

### Post by DaveMiller on 2018-11-24
I have a zoostorm box with Radeon R5 Kaveri graphics onboard. I'd like to use more than 1024x768 but neither Settings/Screen nor xrandr see any higher.
I've installed Ubuntu 18 LTS
The internet tells me that Radeon needs amdgpu stuff.
The packages xserver-xorg-video-amdgpu 18.0.1-1 and libdrm-amdgpu1 are installed. (also -radeon packages)
There is a 10-amdgpu.conf

I have done dmesg | egrep 'drm|radeon' and it seems to be happy with VGA/DVIHDMI connectors, last line says "amdgpu kernel modesetting enabled"
The internet is full of references to all kinds of gibberish abut rebuilding the world.
Is there a simpler way to just give me more pixels??
I don't need and fancy graphics.

Yes, the monitor handles higher res. It's on a KVM with my elderly fedora boxes which do higher res.....
I've been around the block in computing and these days I just want stuff to work.
I want to love linux more but this stuff really makes it a pain for the general masses.

---

### Post by DaveMiller on 2018-11-24
Search finds me this article

[https://ubuntuforums.org/showthread.php?t=2406377&highlight=radeon](https://ubuntuforums.org/showthread.php?t=2406377&highlight=radeon)

If I type in the commands given "it works" and I get a higher resolution.
Now I just need to work out where to put the example config file...

---

