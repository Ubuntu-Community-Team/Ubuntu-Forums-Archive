---
title: "Webcam Help?"
date: 2009-04-30
forum: Hardware
---

### Post by omgseth on 2009-04-30
Anyone know how to make my webcam work? Camorama, Cheese, and Kino don't work...

---

### Post by omgseth on 2009-04-30
Correction, suddenly now it works in Cheese...

---

### Post by omgseth on 2009-04-30
And now it doesn't work in Cheese... hmm...

---

### Post by omgseth on 2009-05-01
I ran lsusb and it found the webcam...

Bus 001 Device 005: ID 19ff:0102 Dynex 1.3MP Webcam

It strikes me as strange that it worked in Cheese two times ( both times I was looking at the different effects, and then the camera stopped responding ). I intend to do a fresh install of jaunty later today, and hope to find a resolution to this problem before that :\ I'm still google-ing but with few results...

---

### Post by loell on 2009-05-01
it's probably a driver issue, your webcam is said to be using a **uvc** driver.

---

### Post by omgseth on 2009-05-01
Would that be a good or bad thing? Hopefully if it's bad it's easy to fix :)

---

### Post by omgseth on 2009-05-01
It worked at one time, so I just really need to find a way to make it work permanently really...

---

### Post by omgseth on 2009-05-01
Google is being terribly unhelpful :( Just pages and pages of unrelated information...

---

### Post by omgseth on 2009-05-01
Breakthrough!! I opened up the gstreamer properties and tried to adjust the video input ( for a while it just kept saying that it couldn't read or write to /dev/video0 ). Finally I decided that the only way was to take ownership of said file... suddenly, I click TEST and I'm staring at a big video of me ( doing a happy dance if truth be told ). However none of my apps are able to connect to it still... I may be on the verge of cracking this though... any ideas?

---

### Post by omgseth on 2009-05-01
video0 is now missing... does everything have to be like pulling teeth? I mean really!

---

### Post by omgseth on 2009-05-01
When I realized video0 was missing I also took note that it had been replaced by video1. Upon reboot, the file was video0 again. The problem seems to be that it doesn't want me to take ownership ( that's where the problem usually starts ). I chown the file, then am able to see video output from gstreamer properties. Camorama continues being hard headed and not connecting no matter what I do.

---

### Post by omgseth on 2009-05-01
Why won't Ubuntu let me keep ownership of video0?! The contents of the dev file are having a freaking seizure moving around and changing. Is this really usually this complicated?

---

### Post by omgseth on 2009-05-01
I don't suppose there's anyone with an easy solution to just make my webcam work?

---

### Post by loell on 2009-05-01
yeah, basically when it comes to webcam, you need to choose those more compatible ones, i tend to avoid UVC based webcams. and tend to choose those compatible with gspca.

---

### Post by omgseth on 2009-05-01
So there's no hope for it then?

---

### Post by loell on 2009-05-01
> **omgseth said:**
> So there's no hope for it then?

only a little, probably wait and hope the UVC devs will fix things, you may  also have to coordinate with them for a better chance of fixing the particular device.  other than that, probably choose a more comapable webcam.

it's a cumbersome process for those who just wants their particular device to just work. otherwise it's actually smooth sailing for those who choosed the right device from the start.

---

### Post by omgseth on 2009-05-01
I actually think I've found a driver that might help... any idea how to install a tar.gz file?

---

### Post by loell on 2009-05-01
if it's a module.  extract the tar file , then most probably execute 

```

./configure
make

sudo insmod name_of_module.ko
```

in any case there might a specifi instruction in the README file.

---

### Post by omgseth on 2009-05-01
Thanks... yeah it worked for just over a minute in Cheese, then stopped. Oh well.

---

