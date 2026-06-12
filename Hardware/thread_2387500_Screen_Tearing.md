---
title: "Screen Tearing"
date: 2018-03-19
forum: Hardware
---

### Post by lowkrsbhs on 2018-03-19
Hello all,

I have been trying to fix my screen tearing issue on my laptop for a while now. I tried to follow many tutorials (like this one: [https://cubethethird.wordpress.com/2016/06/14/eliminate-screen-tearing-with-amd-gpu-on-ubuntu/](https://cubethethird.wordpress.com/2016/06/14/eliminate-screen-tearing-with-amd-gpu-on-ubuntu/)), but then my laptop couldn't boot. Using Hardinfo, I have a Mobility Radeon HD 5430/5450/5470 (VGA compatible controller is the GPU, right?). If you need anything to help me resolve this issue, please let me know :).

I'm pretty new to Lubuntu, so please ignore my naivety :3.

Thanks!

---

### Post by ank2 on 2018-03-19
There is a man page for radion. Open that.

Also here I have a skeleton /usr/share/X11/xorg.conf.d/10-radeon.conf which should be a file you need to open as root. What you probably have to add or modify (if exists) is the line

Option "AccelMethod"

May be

Option "AccelMethod" "glamor"

already solves it. Otherwise use the lines and Google for other matches and try them out. But it can be tideous as after each change to have to reboot or at least restart the X Server.

Keep a backup of the original file, just in case.

---

### Post by lowkrsbhs on 2018-03-19
Hello,

Thanks for the suggestion! I tried and it didn't work :/. I was hoping for a quick solution because after each attempt, I have to go into recovery to change it, so it's kind of annoying.

Thanks!

---

