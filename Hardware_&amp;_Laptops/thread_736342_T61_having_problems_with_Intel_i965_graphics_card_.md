---
title: "T61 having problems with Intel i965 graphics card (Kubuntu 8.04)"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by DrMX on 2008-03-26
Dear all,

I just got a new laptop at work, T61 with Intel i965 graphics controller. I installed Ubuntu 7.10 and if I suspended the laptop, when it was coming back, the screen would be too dark. So I decided to install the Alpha 5 release of Kubuntu 8.04. It solved the problem of suspending it but I cant send a signal for a projector.I also noticed that the birghtness controls (Fn+ ...) dont work. I went to System Settings and realized that it has detected a Generic VESA card. When I try to select the Intel i965, it appears fine the selection, but still the signal wont go out to the projector. If I restart the laptop, then I get graphics problems and it boots in Console mode. I have to start with Recovery mode at boot in order to get to my desktop.

Any ideas on how i can fix this problem? I really need the function of using my screen and an external projector as I am a teacher. 

Thanks in advance. This is my first post, so if this problem was already solved, please give me the link. I did search the site but couldnt find an answer.

---

### Post by DrMX on 2008-04-01
Bump.

Just to add to my previous message. I still can't use the external monitor directly by pressing Fn+F7 , but after trying different things, i found out the following:

1. With Ubuntu 8.04 Beta, in live mode, I can send the signal to my external monitor (fn +f7), althoug the resolution changes to 1024 x 768 and I have to scroll on the LCD of the laptop to see the bottom of the screen (on the external monitor I see it fine). 

2.- If I install Ubuntu 8.04 beta (after seeing that works fine in live mode), then I get problems, as I can't send the signal out to the external monitor unless I logout and login with the monitor already connected. 

3,. After a suspend, the screen becomes very dark... an issue that I don't know if it has been solved already. 

4.- Kubuntu 8.04 in live mode does not allow to send the signal to the external monitor, as Ubuntu does.

5.- Kubuntu 8.04 does not have the issue of the dark screen after a "suspend".

Hope this info could help somehow in finding what is wrong with this graphics card.

---

### Post by jblackhall on 2008-04-04
Your brightness button issues should be fixed with the newest kernel upgrades.

---

### Post by DrMX on 2008-04-07
Yep, the brightness buttons work now. 

As for the original problem:
In System Settings (kubuntu) i see 2 graphics cards, both recognized as the VESA generic driver. The first one having 2 monitors and the second one only one. The workaround I found in the forums is to Re-start the X server after pluging it the external monitor, that way, when I login again, the image is sent to the external monitor (although not at the proper resolution but at least I get image to give my lectures).

---

