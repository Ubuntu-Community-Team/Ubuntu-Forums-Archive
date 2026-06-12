---
title: "Hardy + Xinerama + Wacom Bamboo + HELP!!"
date: 2008-05-09
forum: Hardware
---

### Post by flaviusxvii on 2008-05-09
Alrighty.. I followed neko's fine instructions for getting my tablet to work in Hardy (which worked perfectly in Gutsy btw).

It all 'works' except for a strange problem with offset and jumping. When using the stylus, even just as you'd use it for general pointing, it pointer will ONLY exist in the outer two halves of my two monitors. When it gets to the center of one monitor it jumps to the center of the other monitor, like the middle half of the dual screens doesn't exist.

When I do use something like inkscape or the gimp, there seems to be about a quarter screen horizontal offset from the pointer and where the effects actually are.

Help would be greatly appreciated with this.

---

### Post by ogden_freen on 2008-08-27
I have the same problem.
Just bumping the thread.
Any solutions?

[Edit]
FWIW, I just tried TwinView (which only works with the nvidia driver), and now it works in all areas of both screens.

Success!
Kind of, in that it will only help nvidia customers, and also...

Ideally it would be great to specify which area the tablet covers. Right now I have a my 4:3 tablet working across a 4:3 and a 16:9 screen and it makes it very hard to draw a circle.

(If only wacom would release the equivalent of nvidia-settings for tablets!)

[Edit]
By reading [this page]("http://www.taiabati.com/linux/Wacom_ArtPad_in_Fedora_Core_2.php"), I realised that putting the line:
```
Option        "KeepShape" "1" 
```
in the input device section of xorg.conf for the cursor, stylus and eraser, causes it to hold its shape.

:)

---

### Post by Xanmar on 2010-06-04
No solution yet? It seems that barely anybody has this problem, but I can't get it fixed... D:

Edit: Oh, I'm in Lucid, not Hardy. But it's the same problem.

---

### Post by inthemood on 2010-09-08
Hi everybody. 

Im having the very same problem with the jumping cursor. 

Since I want to use 1 monitor in landscape and 1 in portrait twinview is not an option, I have to use xinerama.

I found this topick on [gmane.org]("http://thread.gmane.org/gmane.linux.drivers.wacom/4770/focus=4773") but I don't know how to use the patch.

I tried several other how-tos where i used xsetwacom set [device] bottomX [value], same with bottomy, but it didn't change a thing.

The jumping from the middle of one monitor to the middle of the other monitor is independent from my turning 1 monitor. Emerges too, if both are landscape.

I want to use absolute mode, not relative

I use Lucid. Would be nice, if the tablet could be mapped to the whole area like it works in Windows.

If you found a workaround or a solution feel free to post :p.

Edit: this is the Link of the bug report post with some suggestions to solve, but didn't work for me :-/ [bugreport]("https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/298707")

---

