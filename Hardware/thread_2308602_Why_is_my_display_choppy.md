---
title: "Why is my display choppy?"
date: 2016-01-04
forum: Hardware
---

### Post by formatc2013 on 2016-01-04
I am using Xubuntu 14.04 on an ASUS X55V(i3 CPU and Nvidia 610m GPU).  I installed the recommended proprietary driven in the GUI (352.63). 

 When I am playing a video on  Youtube or in VLC I can see it uses my GPU. I installed Nvidia settings as well, and it lets me choose between the Intel and the Nvidia GPU (but as the picture shows, it  does not use video engine... does it have anything to do with it?).

I also ticked the ani-aliasing checkboxes, which include the following settings:

  
[LIST]
[*]Enable FXAA(ticked)
[*]Antiostrolpic filtering(override app settings-ticked)
[*]Texture quality(texture sharpening-ticked)
[/LIST]
  I installed the Ubuntu restricted extras, well.
 And lastly, I found this:
[http://blog.riswan.com/2012/05/how-to-fix-slow-choppy-video-playback.html](http://blog.riswan.com/2012/05/how-to-fix-slow-choppy-video-playback.html)
I followed all the instructions, with no luck.   
  ```
formatc2013@formatc2013-X55VD:~$ lspci|grep VGA
[00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M \[GeForce 610M\] (rev a1)][1]
```

```
lspci -vnn | grep -i VGA -A 12
```
This command gives me, that the kernel driver is the actual Nvidia one.

I installed Ubuntu Gnome, and I am facing the same problem here, too. I guess, that is not occuring when I am playing HD videos, 
but it is going on all the time. 
  I would like to know, what is the reason of this screen tearing, and what commands to run in order to fix it! Many thanks

---

