---
title: "Tracking eVGA nVidia 8600gt"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by kuosion on 2008-02-06
This is the second time I have installed Ubuntu from scratch today. First time the graphic drivers were broken or something. I know this problem is solvable, I ran this graphics card on Ubuntu a few months ago  after messing around a little bit. This time I just can't seem to get it work. I guess this post is for me and anybody else that is trying to get this card to work. Until then I will keep scavenging the forums.

[COLOR="Red"]DEBUNKED: Well I'm guessing the first install was a fluke and something went wrong. Although I did take some steps differently. First time I installed the restricted drivers first and updated everything and restarted all together. After I rebooted the system would only recognize one horrible screen resolution of 640x480. Second time I took things one at a time. I installed the updates first. Rebooted. Then I activated the restricted drivers. Rebooted. And everything is working just peachy.[/COLOR]

**Clean Install**:
*note: Restricted Driver not Activated yet.*
Westinghouse 24" 1920x1200 - Running Perfect
Auto Detect range:
1920x1200 
1920x1080 
1680x1050 
1280x1024 
1440x800 
1280x800 
1280x720 
1024x768 
800x600 
640x480
```
glxinfo | grep "direct rendering"
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```


**Installing ALL updates:**
*note: Restricted Driver not Activated yet.*
Westinghouse 24" 1920x1200 - Running Perfect
Auto Detect range:
1920x1200 
1920x1080 
1680x1050 
1280x1024 
1440x800 
1280x800 
1280x720 
1024x768 
800x600 
640x480
```
glxinfo | grep "direct rendering"
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```


**Activated nVidia's Restricted Drivers:**
*note: Obviously this is the step that goes wrong.*
Westinghouse 24" 1920x1200 - Running Perfect
Auto Detect range:
1920x1200 
1920x1080 
1680x1050 
1280x1024 
1440x800 
1280x800 
1280x720 
1024x768 
800x600 
640x480
```
glxinfo | grep "direct rendering"
direct rendering: Yes
```

---

