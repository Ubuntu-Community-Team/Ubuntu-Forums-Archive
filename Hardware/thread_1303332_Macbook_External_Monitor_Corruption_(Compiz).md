---
title: "Macbook External Monitor Corruption (Compiz)"
date: 2009-10-28
forum: Hardware
---

### Post by Daniel G. Taylor on 2009-10-28
Hey,

I seem to be running into an issue with both Ubuntu 9.04 and 9.10 where I experience horrible graphics corruption on my external monitor whenever desktop effects are enabled. The machine is a Macbook 2,1 with an integrated Intel video chip. The external monitor is a 24" that runs natively at 2048x1152. When desktop effects are disabled it works perfectly. When the external monitor resolution is set to 1024x768 and desktop effects enabled it works perfectly.

I know the maximum OpenGL texture size for this graphics card is 2048x2048 so I've disabled the internal LCD screen via both gnome-display-properties and directly via xrandr and in xorg.conf. After setting MonitorLayout to CRT,NONE and monitor-LVDS1 to Ignore in Xorg the internal LCD no longer shows up in xrandr or the gnome-display-properties. Only the external monitor shows and the resolution is 2048x1152, smaller than the maximum of 2048x2048.

Here a screenshot of the corruption, created by Applications -> Accessories -> Take screenshot and having it wait 5 seconds, enabling desktop effects, then waiting for them to be disabled again after 15 seconds:

[http://programmer-art.org/dropbox/CompizCorruption.png](http://programmer-art.org/dropbox/CompizCorruption.png)

```

$ glxinfo -l | grep GL_MAX_TEXTURE_SIZE
    GL_MAX_TEXTURE_SIZE = 2048

```

```

$ xrandr
Screen 0: minimum 320 x 200, current 2048 x 1152, maximum 4096 x 4096
VGA1 connected 2048x1152+0+0 (normal left inverted right x axis y axis) 510mm x 287mm
   2048x1152      59.9*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        60.0  
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)

```

Any idea as to what might be the issue here? I'm really missing my desktop wall, easy switching between virtual desktops, being able to use a dock and the scale/show desktop plugins set to screen edges...

Any help would be much appreciated.

---

### Post by Daniel G. Taylor on 2009-10-29
Is there anybody running desktop effects on a large external monitor that could post some information about their configuration here?

---

