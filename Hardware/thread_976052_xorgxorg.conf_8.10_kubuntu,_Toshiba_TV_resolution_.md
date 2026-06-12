---
title: "xorg/xorg.conf 8.10 kubuntu, Toshiba TV resolution problems, Please help!"
date: 2008-11-08
forum: Hardware
---

### Post by SergeiFranco on 2008-11-08
Hi, I am trying to connect Toshiba Regza (42WL66A) to Kubuntu (8.10) box via DVI->HDMI cable (I have also tried normal VGA cable). The video card is nVidia FX5200.
I am having huge problems just setting things up just to get the picture on the screen.
The biggest issue is that it seems to me that xorg.conf is ignored (especially my modelines), also the resolutions that are detected have wrong timings as the picture is larger than the screen. Some resolutions detected do not work at all.
xvidtune has no effect at all, it says that my hardware does not support the modeline I am trying even if I don't move anything.
Before (at least in kde3) I could just go to screen settings and choose my screen of choice from the list which was close enough, and override auto detect, now there is no option.
Also the biggest issue is when I try and connect the TV instead of monitor all fonts become 2 pixel tall/wide. When I connect my LCD monitor the fonts are ok.
I have tried VGA cable, and that is worse, there are only 2 modes available for it 640x480 and 320x240, which sux, as the TV definitely supports higher than that (even says so in the manual). There is no gui option to override that.
What shell I do next?


Right now I will try nvidia driver instead of repository one.
Luckily vnc is not affected if resolution is out of range.....

Please help :(....

EDIT: It seems that NVIDIA-linux... driver fails to install (it does not like the kernel by looks of it, from nvidia-error.log)...

---

### Post by SergeiFranco on 2008-11-10
Hi, here is the update:
I have read more about this sort of problem and the picture size is due to overscan.

Now there is another problem: it forgets resolutions on reboot defaulting to 800x600 which obviously does not work with HDMI. It seems that it ignores, everything in xorg.conf.

Now this stupified system is worse than good old xorg.conf system as there at least I could define custom modes, and force certain things...

What even worse that advanced screen options that were in KDE3 now completely removed (before I could just add a screen device even if it was not detected). It looks like KDE4 went GNOME way in that department.

It is very tempting to install KDE3....

So is it possible to change that xorg relies more on xorg.conf than it does now? I want advanced configurations - this why I use linux and KDE, I want be able to change things around.

Or maybe KDE4 has all these settings, but kubuntu version doesn't? If so what repository shell I add to have a standard non kubuntu-fied KDE?

---

### Post by wgrant on 2008-11-10
Things are in a bit of flux at the moment, with all display configuration moving over to XRandR 1.2. You might want to look at [X resolution fixing documentation](https://wiki.ubuntu.com/X/Config/Resolution).

---

### Post by SergeiFranco on 2008-11-10
Thank you very much, this is what I was looking for... I will play with settings tommorow.

---

### Post by SergeiFranco on 2008-11-28
Ok, xrandr has no effect what so ever, I have tried it with nvidia driver and vesa. It comes with whole bunch of errors. I have googled and seems that nvidia driver does not support xrandr.

How can I force certain resolution under 8.10?
the system config GUI does not have any options to add resolutions.
The only way I could get resolutions to work is by having nvidia driver (only 173 works, I have tried 177 and 96) detect automatically.
This is quiet bad as I have to turn on TV and select the right input before booting up the PC. If I turn off EDID and try to put modlines in there it ignores them and boots 640x480, and there is no way to change the resolution.

In my opinion the resolution deal is seriously broken, do I log a bug or there is a fix in the pipe line?
There is no point having resolution options if you cannot change anything.

I am considering finding a 7.10 disc and installing that.   

Is there a way to switch off safe xorg.conf and make it work just like it used to before it got dumbed down? (why? I need to be in the control of my system other wise I might just install windows).

Here is the valid questions: what about people who have invalid EDID? Do they get stuck with low res?

Another question: how do I set the certain automatic resolution to be default one?

I need a button "I know what I am doing" in that resolution setting so I can set my modlines.
If I hose it big deal, it is not like a huge problem to emacs /etc/X11/xorg.conf.....

---

### Post by ideewoww on 2008-11-28
[img]http://www.ideewomen.com/cn/uploads/200811131739540.jpg[/img]The IDee fashion jewelry , accompany women&#8217; life-long beauty.The IDee brand connotation: Individuality, nature, fashion, romantic,

---

### Post by SergeiFranco on 2008-12-02
I have given up on KDE4 and 8.10.
It seems the combination of both is not the best thing.
KDE4 is not finished and very buggy, from random focus issues to just refusal to drag and drop.
I have installed KDE3/8.04 and everything worked fine out of the box. I could also fiddle with monitor settings among other things.

As for overscan, I could not find modeline that will work so I will try to reduce it via service menu....

---

