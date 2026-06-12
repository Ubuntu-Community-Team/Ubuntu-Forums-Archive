---
title: "720p display using Nvidia card in Jaunty"
date: 2009-05-05
forum: Hardware
---

### Post by sandy8925 on 2009-05-05
Hi I'm using Jaunty right now. I've connected my comp to my LCD TV and am using an Svideo to component converter that came along with my graphics card (Geforce 6600 GT).

I was unable to  get 720p resolution working until I added an option I found in the readme for the 180 drivers. The option is:

Option         "TVStandard" "HD720p"

I am able to get 720p resolution now but the problem is that the desktop is actually slightly larger than the screen i.e some parts on all 4 sides are not shown. In Windows XP I was able to use the resize option from the Nvidia control panel to resize the display but there doesn't seem to be any such facility here. Can anyone help me ?

---

### Post by mikedep333 on 2009-05-05
You are using an s-video to component converter?

If your graphics card can only output s-video, then that is standard def and cannot be converted to HD component.

If it is the awkward looking port that looks like s-video, then we can try to help you.

Anyway, I would imagine that you can output your graphics card to 1360x768 with the TV. That is actually a little higher than 720P. See if that works. And use the nvidia-settings utility.

---

### Post by sandy8925 on 2009-05-06
Oh I didn't know SVideo could only output standard video. By the way I am using the nvidia-settings program and it never shows anything above 1024x768. After inserting the 720p option in xorg.conf I got a 1280x720 resolution option.

In Windows the Nvidia conrol panel detects my TV and displays the high definition resoluions that my TV supports (720p and 1080i).

My graphics card which is a Geforce 6600 GT has 3 output ports:  The normal thing which you connect to a CRT monitor(i think it's called VGA), an Svideo output and a DVI output.

The Svideo converter came along with the graphics card.It's not exactly a converter; at one end it has an Svideo connector and at the other end it has 4 connectors :a normal composite Video connection as well as 3 connectors for component video.

---

