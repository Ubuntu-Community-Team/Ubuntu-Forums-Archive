---
title: "Damaged Video Card (Laptop) Help installing Ubuntu to still use it."
date: 2018-07-15
forum: Hardware
---

### Post by rmartinezv on 2018-07-15
Hi guys.

To make a long story short, my Video card get damaged.

Windows cant run on it, because all the scratch and lines on the screen, BUT I tried with linux and runs perfect only if I use nomodeset on the grub.

The thing is, in Parrot works all fine, but cant make TOR working, in Ubuntu all is fine but I have this ugly 800x600 display resolution and there is no other option in the list for change it.

The idea is trying still using the laptop, because right now I'm paying medical bills and I'm broke.

There is any setup I can change on the grub to make this better?

I'll really appreciate any help you can get me.

Thank you.

---

### Post by mIk3_08 on 2018-07-15
Can you post your Laptop hardware specifications?

---

### Post by mIk3_08 on 2018-07-15
You can use this for your own risk to customize your screen resolution;

Custom Screen Resolution in Ubuntu Desktop [Click Here]("http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/")
or Here Custom Screen Resolution in Ubuntu Desktop [Click Here]("https://askubuntu.com/questions/754231/how-do-i-save-my-new-resolution-setting-with-xrandr")

---

### Post by Yellow Pasque on 2018-07-15
Maybe you can get 1024x768 by forcing the "vesa" driver (I'm guessing Ubuntu defaults to "fbdev" when you use nomodeset). Detailed write-up here:
[https://ubuntu-mate.community/t/set-sis-graphics-1024x768-l-ubuntu-mate-14-04-and-16-04-16-10/3553](https://ubuntu-mate.community/t/set-sis-graphics-1024x768-l-ubuntu-mate-14-04-and-16-04-16-10/3553)

> but cant make TOR working

Be more specific.

---

### Post by pqwoerituytrueiwoq on 2018-07-15
It may be possible to fix the gpu probably temporary, it may last a few months, a year; but, you could try a solder reflow aka baking the motherboard
at one point there was some mobile GPUs that got so hot the solder would start to melt and connection would get flaky
if that does fix it you may want to try to solve the heat issue is the heat sync is copper you could use liquid metal (it is not like normal thermal paste, do your research) to try to get the temps reasonable

---

