---
title: "[SOLVED] Why oh why dosnt fglrx like my card!"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by SPW06 on 2007-07-25
Hello. I need fglrx for compiz and games to run smoothly on my desktop. But, ever since feisty, X claims my card wont work with fglrx so no suitable devices were found. Thats what happens when I try it  manually. restricted-drivers-manager dosent even pick it up!

My card is:

01:02.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:02.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)

(TV output i guess...not needed)

Any thoughts?

---

### Post by w4ett on 2007-07-25
That card is not supported by fglrx....you will have to use the xorg-driver-ati.....(I have the same card).  fglrx supports the 9550 and above cards..

It's a shame too..the 9200 is a good budget card in another (unnamed O/S) :)

---

### Post by SPW06 on 2007-07-25
It worked on edgy...

Does xorg-driver-ati soppord hardware accelleration?

How do i set up this driver in X

---

### Post by w4ett on 2007-07-25
> **SPW06 said:**
> It worked on edgy...

Does xorg-driver-ati soppord hardware accelleration?

How do i set up this driver in X

setup will be:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

Select ati ar your driver.

I get 3d on mine:

> w4ett@w4ett-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2


> w4ett@w4ett-desktop:~$ glxgears
4163 frames in 5.0 seconds = 832.504 FPS
4163 frames in 5.0 seconds = 832.441 FPS
4162 frames in 5.0 seconds = 832.264 FPS
4164 frames in 5.0 seconds = 832.714 FPS
4163 frames in 5.0 seconds = 832.445 FPS



---

