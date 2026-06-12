---
title: "Serious install problem??"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by dougalkerr on 2009-02-08
My Ubuntu died today - would not boot. I rebooted into Windows XP, doh... and tried to install Xubunto 8.10. Bad move as Xubuntu will not boot. I have the same problem as another user had almsot 2 years ago and there was no cure posted. I have tried a fresh cd with Xubuntu but, still no joy. The checksums are okay and the install appears to go well. The liveCD works but, like I say once installed it will not boot. I think there is a problem in 8.10 because I have exactly the same problem if I upgrade from Ubuntu 7.04 to 8.10 Intrepid Ibex.
What's happening?
Think I'll post this as a new thread again as I have done before without anyone answering with a positive suggestion.

---

### Post by dougalkerr on 2009-02-08
My Ubuntu died today - would not boot. I rebooted into Windows XP, doh... and tried to install Xubunto 8.10. Bad move as Xubuntu will not boot. I have the same problem as another user had almsot 2 years ago and there was no cure posted. I have tried a fresh cd with Xubuntu but, still no joy. The checksums are okay and the install appears to go well. The liveCD works but, like I say once installed it will not boot. The boot proceeds for a short time and then stops.
I think there is a problem in 8.10 because I have exactly the same problem if I upgrade from Ubuntu 7.04 to 8.10 Intrepid Ibex.
What's happening? I can use Ubuntu 6.06 no problem but, would seriously love to move on with my limited system and this is why I chose Xubuntu because of the less need for system resources.
My system is an Acer Travelmate 630 with 30Gb drive and 512Mb RAM. I have an NVidia graphics card with only 16Mb memory but, I don't believe this is a real problem because the liveCD works no problem.
Any ideas are more than welcome. I am still fairly new with Linux but, I can't see anything wrong with my system and the error messages I have seen in the past tend to point toward the memory allocations at boot time.
Some one please help as I have to use Windows XP to get anything worthwhile done. I seriously want to use Linux for everything especially my photo work which is a serious hobby but, I have too many problems with the linux environment to get work done. I like the Gimp to work with but, at the moment the only relief I have is using within Windows... yuk!!

---

### Post by bapoumba on 2009-02-08
Moved your other post from unrelated thread in here.
Could you please specify what happens? Does grub load ? What error messages do you get ?

---

### Post by bapoumba on 2009-02-08
If ubuntu loads but stops during the splash screen, you should try booting without it (before the kernel boots up, on the kernel line in grub, hit "e" and then change splash to nosplash). If it works, you can make it permanent by editing /boot/grub/menu.lst and changing the kernel line accordingly.
(Please do not PM for support questions, so that everyone can benefit/help you, thanks).
What is the exact nvidia version you have ?

---

### Post by dougalkerr on 2009-02-08
Thanks bapoumba. The NVidia card is a GeForce 2 Go. ENVY sorts the graphics out perfectly once I get through to the desktop environment but, I don't know how to employ ENVY via a command line. Anyways I'll give the Grub 'e' option a go and see where it gets me...
Thanks for the heads up about posting...

---

### Post by Partyboi2 on 2009-02-08
> **dougalkerr said:**
> Thanks bapoumba. The NVidia card is a GeForce 2 Go. ENVY sorts the graphics out perfectly once I get through to the desktop environment but, I don't know how to employ ENVY via a command line. Anyways I'll give the Grub 'e' option a go and see where it gets me...
Thanks for the heads up about posting...
To start envyng from a terminal use
```
envyng -t
```

---

### Post by bapoumba on 2009-02-09
Once you get the desktop to load, you may want to try the restricted drivers too (there should be a menu entry for them).

---

