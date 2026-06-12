---
title: "Force higher resolution on Netbook"
date: 2009-05-26
forum: Hardware
---

### Post by ljamie82 on 2009-05-26
I've searched around on the net for this and have found the question asked but never answered.  I've got an HP Mini 1000 with a max vertical resolution in the 576 to 600 range (depending on os strangely enough).  What I'm hoping to accomplish is to get it to around 800 or so by forcing a higher resolution.  I know the hardware only had 600 pixels and that can't be changed, but i'm hoping to downplay quality a tad to fit in just a bit more screen space.  Any ideas?

---

### Post by linuxishard on 2009-07-25
I know this is a pretty old post, but i thought u mite like an answer, the truth is u cant force a higher resolution than ur monitor supports, i also have a netbook an hav searched for a solution to this issue, the only reason is that some apps just dont fit on ur screen, so often ur stuck an u cant click the apply button or whatever it may be, theres a way round it, if u have compiz installed (which it is by default) u just need to use the shelf plugin and perhapse the desktop zoom also, i use shelf to knock the window down in size an then zoom in till i can see it all nicely, the tab till i reach the button im after...
hopefully with the increase in the amount of netbooks out ther the software will eventually catch up an deal with the issue by being resizable for netbook resolutions, this problem is fixable in linux, but windows might take years to catch up.

---

### Post by josvanr on 2009-11-05
or you can try xrandr:

[http://ubuntuforums.org/search.php?searchid=66309561](http://ubuntuforums.org/search.php?searchid=66309561)

didn't get it to work with kde yet though, only xfce

josvanr

---

### Post by Aearenda on 2009-11-05
You can always hold down the ALT key and then drag a window from anywhere inside it, not just the title bar, to get access to bits that are off the screen. 

I use a netbook with an external screen, keyboard and mouse when at home, and just put up with the low resolution when mobile as the price paid to extreme lightness and long battery life.

---

### Post by josvanr on 2009-11-08
it also works with gnome, really amazing. I have a 1280x800 12'' screen and now I usually work on 1560x1040 'mapped' resolution. But when I draw in gimp I like to scale the resolution up to 2432x1520. Text gets a bit small this way, but for drawing it's perfect. No clogging of the screen with gimp's clumsy tool dialogs. (see screen shot). One can switch resolutions without leaving the session...

---

### Post by massong on 2010-11-08
Hi,

I have been trying to use xrandr to scale my desktop resolution to do what you guys are talking about.  

I would like to fit a 1024x768 resolution onto my 1024x600 display (I don't mind if it looks a bit distorted).  I think I do this by using the xrandr --scale option.  

However, when I do use it, it looks like my graphics scale but I end up with a desktop still take 1024x600 pixels and the bottom 168 pixels of my screen are just blank space.  I can move my pointer into this area, so it's valid, but gnome doesn't resize to take advantage of the now available 1024x768 scaled pixels.

Here is the command I am using:

xrandr --output LVDS1 --mode 1024x600 --scale 1.00x1.28

I know I am close to having this work, if I could only resize the Gnome Desktop to take up the black space near the bottom of the screenshot.

If you folks can help that would be great!!!

Gary

---

### Post by massong on 2010-11-08
Wow.. Not 5 seconds after I posted I just realized how to do this!

So, for those who stumble upon this post wondering the same thing, here is how you do it!

xrandr --output LVDS1  --mode 1024x600 --scale 1.00x1.28 --panning 1024x768

That's all there is to it, you can fit a nice 1024x768 set of pixels on your 1024x600 display on your netbook!

Now my kids can play Webkinz on my netbook! ROFL

Fantastic!

Gary

---

### Post by greatbal on 2011-05-01
thanks for this. I have been looking for this. Now I placed a startup command:

xrandr --output LVDS1 --mode 1024x576 --scale 1.10x1.10

to force my system to have a just a little bit higher resolution than the native resolution of 1024x576. I scaled both the height and width so as to keep the 16:9 aspect ratio.

Again thanks.

---

### Post by greatbal on 2011-05-04
[B]Running a startup command:

$ xrandr --output LVDS1 --mode 1024x576 --scale 1.25x1.25

did the trick to increase the native resolution of my netbook running Ubuntu 10.10 from 1024x576 to 1280x720.

Finally, I can see "more" on my screen. :)[/B]

---

### Post by urata on 2012-06-26
I am using Ubuntu 12.04 and on a Samsung nc110.

This is getting really close to solving(working around) my issue. In fact it already helps quite a bit to be able to see more pixels this way. However my mouse cursor won't go below the 600 pixel line still. Is there a way to get past this?

---

### Post by Aearenda on 2012-06-27
Sounds like [this bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/883319")

---

### Post by urata on 2012-06-29
I'm beginning to think this is a bug with some part of ubuntu. I've been messing around with this a lot and it's behaved strangely.

In Ubuntu 12.04 when I essentially zoom out and display a higher resolution on my 1024x600 screen by using something like:

```
xrandr --fb 1024x768 --output LVDS1 --mode 1024x600 --scale 1.00x1.11
```

I get a screen that looks just right, perfect for what I want it to do. The only problem is my mouse cursor won't leave the bounds of the original 1024x600 pixel area.

The weird thing is I started plugging this netbook into an external LED TV and playing with xrandr to mirror my desktop the best way I could. When I have it plugged into that TV I use:

```
xrandr --fb 1360x768 --output LVDS1 --mode 1024x600 --scale 1.32x1.11 -VGA1 --mode 1360x768
```

And it comes out perfect. It's a bit blurry on my netbook screen but perfect on my TV screen and the mouse goes wherever I tell it to go.

But I still want it to just be able to pretend it's 1024x768 since it's such a default resolution for computers. 

It works in Bodhi Linux 1.40. (xrandr v 1.3.2 RandR version 1.3)

My video card is Intel, if I should post any more information I will.

---

### Post by urata on 2012-06-29
> **Aearenda said:**
> Sounds like [this bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/883319")

I didn't see your post before I made my second one. Yeah it's not just panning that it interferes with though. It holds my cursor inside the bounds of the actual resolution when I am "emulating" a higher resolution.

I'm kinda a newbie can you tell? ;)

---

