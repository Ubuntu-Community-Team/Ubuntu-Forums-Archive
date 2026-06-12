---
title: "Digital Video Camera support"
date: 2005-10-29
forum: Hardware &amp; Laptops
---

### Post by KLineD on 2005-10-29
Hello!

Today I got a Sony digital video camera (DCR-TRV380) borrowed from my brother in law. He wanted to transfer some videos stored in the camera to the pc and burn them to DVD. The camera has USB support so I plugged it to my ubuntu box but the output of dmesg was telling me that it was an unsupported device (ubuntu recognized something was on the usb port but didn't knew what it was).

I plugged the camera in another box (a winxp box) and it couldn't find suitable drivers so I went to [www.sony.com](www.sony.com) to download the drivers. After some searching I found them and installed the camera. The quality of the video is rather dissapointing but I'm reading that this might be because of the usb port speed (but I dont have firewire).

What I want to ask is this: Is there a way to capture video using this camera under ubuntu (maybe Kino or something else) ?? also please if someone has experience with digital video cameras and linux share your opinions, I'm thinking on getting one for christmas... nothing fancy I just want to be able to record video and then transfer it to my linux box and burn it to dvd but with superior quality than the sony handycam (it looked like webcam video) possibly using the usb port? (I only have usb2 ports, no firewire here)

Thanks a lot!

---

### Post by claydoh on 2005-10-29
AFAIK video transfers via USB are not supported in linux at all for Sony handycams. I have not looked to see if there has been any developments in that area since I got my TRV17 a few years ago. I think they use USB 1.1 which would make video transfers rather cumbersome and slow.

Firewire and Kino work really well though :)

USB video wold be nice as in windows I could use the camera as a webcam, it would be nice to have that in linux.

---

### Post by KLineD on 2005-10-29
So as I see it it's only two ways

[LIST=1]
[*]Get a capture card and transfer via RCA cables
[*]Get some Firewire ports into this box and use Kino
[/LIST]

What do you think is best? and what about the camera itself, it doesn't has to be supported as long as either the capture card or the firewire are supported in linux?

---

### Post by xmastree on 2005-10-29
[QUOTE=KLineD]The quality of the video is rather dissapointing but I'm reading that this might be because of the usb port speed (but I dont have firewire).[/QUOTE]Yeah, if it's like my JVC it uses the camera's built-in mpeg converter.
If you're going to splash out on a DV cam then you might as well buy a DV (firewire) card. They're not expensive these days, and AFAIK kino will do what you require.

One thing does concern me though. Your PC only has two USB ports? That would suggest it's only a P3 or lower. What's the spec? For video you need something with a bit of muscle.

---

### Post by KLineD on 2005-10-29
No, for usb2 I meant USB 2.0 

My computer has many more USB ports and tho it's no supercomputer it's pretty ok of handling this kind of job I think (P4 1.8GHz and 512 ram) I know they are not amazing specs but it should be enough isn't it?

---

### Post by xmastree on 2005-10-30
[QUOTE=KLineD]No, for usb2 I meant USB 2.0[/QUOTE]Ah, ok. My mistake. I guess I read that wrong. Your system should be ok for video.

---

