---
title: "I need help connecting and using a wii remote in 12.04"
date: 2012-04-29
forum: Hardware
---

### Post by dpstatic on 2012-04-29
When I try to connect the remote with the standard bluetooth device setup, the wii remote disconnects as soon as the device setup starts, even if I am holding the 1 and 2 buttons down. I have been able to connect the wii remote with wmgui, and recognized it with lswm. I don't know whether or not connecting it with wmgui will allow me to actually use it. I can't find a program to map any of the buttons, but I am still rather new to ubuntu, and don't know what I can do with that.



Is there a way I can connect my wii remote through bluetooth, or is wmgui sufficient?
are there any programs that will allow me to map it's buttons in 12.04?


edit: solution: I got it to work using wminput which connects and maps, which I couldn't open before because it has to be opened using 'sudo wminput' rather than just 'wminput'.

---

### Post by cantormath on 2012-05-16
> **dpstatic said:**
> 
edit: solution: I got it to work using wminput which connects and maps, which I couldn't open before because it has to be opened using 'sudo wminput' rather than just 'wminput'.

for nonroot:
[https://help.ubuntu.com/community/CWiiD#Running_wminput_as_user_.28not_root.29](https://help.ubuntu.com/community/CWiiD#Running_wminput_as_user_.28not_root.29)

---

