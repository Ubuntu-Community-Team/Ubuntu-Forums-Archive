---
title: "Output Video"
date: 2015-12-19
forum: Hardware
---

### Post by fafabone on 2015-12-19
Hi All,
I have an intel Nuc5cpyh connected via hdmi to Samsung Hd Ready LE32S71B (32").
I installed Gnome Ubuntu 14.04, with 4.2 Linux Kernel. Wireless driver for NUC needs Linux 4.2.
The monitor is recognized as 7" 1920x1080. How can I adjust monitor size and resolution?
Thanks

---

### Post by TheFu on 2015-12-19
xrandr, **lxrandr**, arandr are the easiest.

---

### Post by fafabone on 2015-12-21
> **TheFu said:**
> xrandr, **lxrandr**, arandr are the easiest.
I've already tryed with xrandr with mode 1920x1080 and with the other possible modes but he screen is too big. Is it possible to add a mode bigger than 1920x1080? Is it possible to choose the screen size and let the resolution or dpi be adjusted automatically?
Thanks for your reply

---

### Post by SeijiSensei on 2015-12-21
I've found some displays don't report the correct size, but they work anyway.  Do you only get a 7" diagonal picture if you choose 1920x1080?

---

### Post by TheFu on 2015-12-24
You can manually add modes. There's a guide for this i ubuntu.  Web search for 'xorg ubuntu modes' and choose the help.ubuntu.com link.  Did this a few days ago myself.

---

### Post by Vladlenin5000 on 2015-12-24
For Samsung LE32S71B you want _less_ resolution, not more. Its native resolution is **1366 x 768** and, as usual with "HD Ready" screens, it can take 1080P and then perform the required downscaling, but not higher than that.
The native resolution is always the best option.

What do you mean by "too big" (with 1080P)?
If it bleeds out of the borders then it's the well known overscanning issue many TVs have. You're supposed to adjust it in the TV itself. For instructions download the [user's manual]("http://downloadcenter.samsung.com/content/UM/200607/20060717101438609_BN68-01001J-01-L07-0613.pdf") and go to page 15 in the PDF (page 13 in the actual document) -> Changing the Picture Size.

---

### Post by fafabone on 2015-12-26
Thanks for replies.
The screen is detected as 7" and the resolution is not correct. I'll try to send you an image. I'm not able to change the resolution of the screen via xrandr: I select an existing mode, 1366x768, but the xrandr -q give me back:
HDMI2 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080      60.0*+   50.0     59.9     30.0     25.0     24.0     30.0    
I try to add a new mode and I see it in the posible modes for HDMI2 output, but when I restart, the mode is cancelled.
Can you send a possible configuration of xorg.conf or .profile' (I haven't .xprofile)?
Thanks.

---

### Post by Vladlenin5000 on 2015-12-26
Here we go again with the size... It doesn't matter.

1. Quoting SeijiSensei, *"some displays don't report the correct size, but they work anyway"*. I can add I had a couple of 26" reporting as 72", a 32" reporting as 19", a 32" reporting as 72" - an HD Ready just like yours working beautifully at 1080P, etc. etc. It doesn't matter!
2. xorg.conf is no longer used.
3. Resolution does matter... Either its native 1366x768 or 1920x1080 (1080P) can be used with pretty much the same end result, the latter being reprocessed to 1080i by the TV/monitor itself (just like the aforementioned example.

That said, what is the problem? Post a photo (as an attachment) if you must but please explain what you (think) is wrong, besides the reported 7", of course...

---

### Post by fafabone on 2015-12-26
[https://drive.google.com/file/d/0BxGE6sXo4ZLcaU80TXNXVGZlM3c/view?usp=sharing](https://drive.google.com/file/d/0BxGE6sXo4ZLcaU80TXNXVGZlM3c/view?usp=sharing)
[https://drive.google.com/file/d/0BxGE6sXo4ZLcSW11UXlpYUlOYWc/view?usp=sharing](https://drive.google.com/file/d/0BxGE6sXo4ZLcSW11UXlpYUlOYWc/view?usp=sharing)
The windows are too big. This is with 16:9 setting on the monitor. With Zoom setting I can squeeze a little the screen, but it is not sufficient.
With the resolution 1280x720 the visualization get worst, the window bigger.
There is not the resolution of 1360x768 in xrandr or Ubuntu settings.
How do you suggest to resolve the problem?
Thanks.

---

### Post by Vladlenin5000 on 2015-12-26
> **fafabone said:**
> How do you suggest to resolve the problem?

I believe I already did -> Post#6

---

### Post by fafabone on 2015-12-26
[[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1468732")Thanks for your reply, Vladlenin5000, but is not possible to adapt the window with Zoom setting of the monitor. Auto-adjust is disabled with HDMI or VGA output.
Any other tips?

---

### Post by Vladlenin5000 on 2015-12-26
Each device is different. I don't know yours, just following the manual. My job here was to point you to the right direction instead of the outdated and cumbersome methods that do not apply to modern digital connections which, I believe, is what you're using. If not, if you're using VGA, you should change to HDMI or at least DVI.

That said please consult page 24 of your user's manual. Even if there's no setting that automatically makes the image fit as it should - Auto Adjustment - you can always use the manual settings mentioned in the same page. The Auto Adjustment mode should just work though.

---

### Post by TheFu on 2015-12-26
xorg.conf isn't required for most people anymore, but in some situations, it is still useful. It may not be used in bleeding edge releases 14.10+, but for LTS, it is definitely still used.
14.04 with a 4.2 kernel? That doesn't compute for me. Isn't 14.04 on 3.13?

---

### Post by fafabone on 2015-12-26
No, the kernel is 4.2. I've updated it in order to install wireless driver for Intel NUC.
I'm not able to adjust screen with monitor settings

---

