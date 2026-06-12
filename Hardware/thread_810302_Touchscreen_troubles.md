---
title: "Touchscreen troubles"
date: 2008-05-28
forum: Hardware
---

### Post by r0b0h0b0 on 2008-05-28
Hello community

After days of effort, and with a lot of help from these forums, I've managed to get my little touchscreen to co-operate...somewhat. Here's a picture of the touch screen in question:

[IMG]http://www.gps-coords.co.za/touchscreen/ts_small.jpg[/IMG]

and [this link (click me)]("http://www.gps-coords.co.za/touchscreen/ts_big.jpg") will take you to a bigger version of the image.

**cat /proc/bus/input/devices** tells me that it's an **eGalax Inc. USB Touchscreen**. (Just incase you are curious, the computer it's connected to is an eBox 4851-S with 512MB RAM, and Ubuntu is running from a 4GB compact flash. The computer doesn't have a HDD)

The problem I'm having now is that I get a kind of a 'grid' of touch points.

[IMG]http://www.gps-coords.co.za/touchscreen/dragHorz.jpg[/IMG]

When I drag the stylus horizontally, the cursor doesn't follow the tip of the stylus, it jumps.

[IMG]http://www.gps-coords.co.za/touchscreen/dragVert.jpg[/IMG]

When I drag the stylus vertically, the cursor doesn't follow the tip of the stylus, it jumps.

[IMG]http://www.gps-coords.co.za/touchscreen/gridBig.jpg[/IMG]

So, I have a matrix of 'touch points', 10 by 8 points. I've been able to tweak it so that I get a grid of 10 x 9, but that's it.

[IMG]http://www.gps-coords.co.za/touchscreen/gridScaled.jpg[/IMG]

When I tweak the min/max extents in my **xorg.conf** file, I end up with a smaller matrix.

This does not seem right. I would have expected the cursor to follow the stylus tip pixel-for-pixel.

Can anyone help me out here? What did I miss?

---

### Post by r0b0h0b0 on 2008-05-31
As it turns out, installing and using a touch screen is actually not a big issue after all. Being a linux ubernoob, it is a daunting task, and not having a single reply to my original post is disappointing (esp. considering that a lot of 'converts', like myself, need help). I digress. Having gained valuable insight into the workings of the OS, it is now...dare I say...simple. And wonderful. Within a short time of getting the screen going, my test app came through with flying colours, and needless to say, much fun ensued.

---

### Post by sis on 2008-06-09
Hi r0b0h0b0,
I'm interested in your work with the touchscreen. My idea is to build a homemade HTPC with a little screen like yours. At the moment I'm just visiting web pages to see if it's possible (it seems quite complicated to set it all up)
Take a look to this link. It might be helpful
[http://zalman.ostergaard.net/](http://zalman.ostergaard.net/)

Have you a more explained version somewhere of your project?

---

