---
title: "'Uknown Graphics' in Ubuntu 12.10"
date: 2012-11-08
forum: Hardware
---

### Post by anirbanghosh on 2012-11-08
I am using ***Ubuntu 12.10*** ***64bit***  in ***Dell XPS 8500***. It has ***AMD HD 7770  ***Video Card. I am facing few problems.

1. In 'About This Computer' it says 'Unknown graphics'
2. Video Playback is not smooth 
3. Sometimes in Unity 3D, Panels and Side Dock vanish for sometime and again come
     back.
4. Most of the time something or the other crashes.

Any idea please about what is going wrong in here. Any help would be greatly appreciated.

---

### Post by nwalkey on 2012-11-08
Try getting the graphics driver from AMD? My computer also says unknown graphics but my graphics card is working and I have no problems with unity 3d.

---

### Post by anirbanghosh on 2012-11-08
Yes I did but during installation there was some problem which I do not remember now. I think there is some problem related to graphics in the computer.

---

### Post by Wilker on 2012-12-12
i think ubuntu 12.10 doesnt come with linux-headers and linux-source in the default installation.
without it, it may be problematic if you want to activate proprieraty drivers from "software sources".
maybe install the two packages mentioned and then install the proprietary drivers, reboot and etc...

---

### Post by cprofitt on 2012-12-12
As far as it telling you your graphics card is unknown under 'details' or System Information the issue is not with drivers, but mesa-utils not being installed.

See this [askubuntu.com]("http://askubuntu.com/a/85322/2022") answer for more details.

---

