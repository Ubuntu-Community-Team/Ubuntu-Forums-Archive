---
title: "Refresh rate too low!"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by Rhapsody on 2007-02-18
I've posted [fairly recently](http://ubuntuforums.org/showthread.php?t=363162) about this problem and another, but since I'm getting desperate with no responses at all, I'm reposting the most urgent under a new title in the hope of getting some help.

I've recently a got a new a PC with an ASRock K8NF6G-VSTA motherboard with integrated graphics and sound. The manual for the motherboard lists the graphics as "Integrated NVIDIA GeForce6-class graphics DX9.0 VGA".

My problem is that the only refresh rate KDE will list is 60Hz, which is totally unacceptable. I'm using a CRT monitor, and anything below 85Hz gives me massive eyestrain eventually developing into frontal headaches. In fact, it would probably be plausible that using a monitor at 60Hz for some years was a major contributing factor to my severe myopia.

This problem is very severe and I'm desperate for a solution. I know this monitor can handle at least 85Hz at 1024x768 (the only resolution I want to use) and the video hardware must be able to, though I just need to convince Kubuntu of that!

---

### Post by solar george on 2007-02-18
Change the vertical refresh rate in your /etc/X11/xorg.conf file to 85.

---

### Post by Rhapsody on 2007-02-18
I had to adjust HorizSync to match, but that seemed to work. Thanks!

---

