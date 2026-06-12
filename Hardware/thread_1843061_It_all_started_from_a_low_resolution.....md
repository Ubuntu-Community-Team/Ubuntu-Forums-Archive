---
title: "It all started from a low resolution...."
date: 2011-09-12
forum: Hardware
---

### Post by Tyson D on 2011-09-12
Good day all,

So I turned my desktop on today and noticed that all the resolution was very low as if I was using a special abilities computer....upon checking System>Preferences>Display it told me it was set at 1024x768 which is the highest resolution listed. It also no longer recognized my screen, used to be Samsung 17" now its listed at Unknown. After playing around to try and fix it,with no success, I hit the forums looking for hints and clues. What I found and tried was changing the xorg.conf file and simply adding higher resolutions under Modes in a subsection under Screen. I backed it up made the changes and reboot(Ctrl+shift+backspace didnt work). Now my comp starts up and gets hung up indefinitely on a black screen with a very small underscore at the top left. I have no way of getting into my computer and its stressing me out beyond belief. Please experts, enthusiasts and ubuntu gods help me get my computer back.

---

### Post by Tyson D on 2011-09-12
Is there some sort of terminal I can access upon start up so I may switch back to my old xorg.conf file?

---

### Post by Tyson D on 2011-09-12
I've managed to get back into my computer, now if I could only fix these enormous settings.....

---

### Post by Tyson D on 2011-09-13
Ive solved it using xrandr and this website

[https://wiki.ubuntu.com/X/Config/Resolution#Three_methods_to_setup](https://wiki.ubuntu.com/X/Config/Resolution#Three_methods_to_setup)

however the changes are not permanent, upon reboot they resume there previous settings...

---

### Post by foresthill on 2011-09-13
+ 100 points for a compelling thread title. One of the best I've ever seen here.

Did you happen to load any updates before this happened? Especially kernel updates? These will mess up your display driver in many cases, especially if it's a proprietary one like ATI's or Nvidia's.

What is your graphics card / chip? This would be helpful to know.

Have you tried booting into a previous kernel from the Grub screen? If that works, then it looks like you need to go hunting for a driver that will work with your new kernel.

---

