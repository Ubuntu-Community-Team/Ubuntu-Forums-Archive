---
title: "Touchy Touch Pad on Sony VAIO"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by boozker on 2007-07-12
I have been using Ubuntu from 6.10 to 7.04 and it has always had a touchy touch pad. It's super sensitive and none of the setting for the mouse do anything. I read about other brands of computers and what to do, but since I am fairly new to programming with Linux I didn't know if settings should be different for a Sony rather then an HP for example. My laptop is running Ubuntu 7.04 and my laptop is a Sony VAIO PCG-7N2L. Also I don't know what Synaptic has to do with my touch pad, but I have read about changing things in it. This one of the only problems I have and last time i posted this which was close to a year ago no one replied. If this were fixed I wouldnt get anymore nasty cramps from trying so hard not to click everything haha.

---

### Post by kerry_s on 2007-07-12
i think it's the sony touchpad itself, it seems to just be built to be sensitive, some would consider that a quality thing, you know as in they use better touchpads, like how now when you buy a laser mouse and it has the dpi the higher the dpi the less you have to move it. any how i use a old vaio pcg-f430 this thing is old and the touchpad is still sensitive, even after years of use. i just turn the tapping off and use the buttons(press both for middle click).

anyways first you need to get and setup the touchpad program.

**sudo apt-get install gsynatics**

**gksu /etc/X11/xorg.conf**
add this line to the touchpad section.

```
Option		"SHMConfig"	        "on"
```


here's a pic, i use qsynaptics, cause i don't use gnome.

---

### Post by boozker on 2007-07-12
OK i did that installed it and everything. I gained root access and edited that file and saved it. But whenever i go to system > preferences > touchpad it says:

"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

so instead of on i wrote true and saved it and it still came up with the same error. What do i need to do. I put it under the right place where it says:

```
Identifier	"Synaptics Touchpad"
```


Also you were saying it has always been sensitive, but when I bought this it had Windows on it and the touchpad was never like this.  Ughhhh.

---

### Post by kerry_s on 2007-07-12
My bag i forgot, you need to restart X.
Logout and press ctrl+alt+backspace

---

### Post by boozker on 2007-07-13
**THANK YOU**

This has been such a pain ever since I can remember and it was actually a quick fix.

---

