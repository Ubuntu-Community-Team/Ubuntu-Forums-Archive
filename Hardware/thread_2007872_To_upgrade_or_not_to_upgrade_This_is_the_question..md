---
title: "To upgrade or not to upgrade? This is the question."
date: 2012-06-21
forum: Hardware
---

### Post by gesti on 2012-06-21
Dear Forum readers and Linux users,

I would like to get advice on some computer specs, as I'm kinda out of touch with the hardware side of our common interest/hobby. And can't decide if I should upgrade the current one or I should buy a laptop or maybe just over clock the current one.
I just started to use [OpenShot Video Editor]("http://www.openshotvideo.com/") to edit and convert FullHD videos form my camcorder :popcorn: and suddenly my once good computer seems very slow.

My current specs are:
Mobo: [Asus P5Q3]("http://www.asus.com/Motherboards/Intel_Socket_775/P5Q3/") (not the deluxe model...)
CPU: Intel Q6600 (not OC'ed)
GPU: ATI HD4750 (factory OC'ed)
Memory: 2 x 2Gb OCZ 1033Mhz
with 750W power supply

So, yep it's a bit old now.. would it make a lot of difference (when editing videos), if I would stick two sticks of 4Gb 1600Mhz RAM in it?

Or put more money in to it and upgrade to an Intel i5 (2500K?) kinda thing, but then would it be enough to only change the CPU and mobo plus RAM? Or I would need to change then the power supply and video card as well?

Or should I fork deeper and go for a Samsung NP700 laptop?

Thank you in advance

---

### Post by cortman on 2012-06-21
> **gesti said:**
> Dear Forum readers and Linux users,

I would like to get advice on some computer specs, as I'm kinda out of touch with the hardware side of our common interest/hobby. And can't decide if I should upgrade the current one or I should buy a laptop or maybe just over clock the current one.
I just started to use [OpenShot Video Editor]("http://www.openshotvideo.com/") to edit and convert FullHD videos form my camcorder :popcorn: and suddenly my once good computer seems very slow.

My current specs are:
Mobo: [Asus P5Q3]("http://www.asus.com/Motherboards/Intel_Socket_775/P5Q3/") (not the deluxe model...)
CPU: Intel Q6600 (not OC'ed)
GPU: ATI HD4750 (factory OC'ed)
Memory: 2 x 2Gb OCZ 1033Mhz
with 750W power supply

So, yep it's a bit old now.. would it make a lot of difference (when editing videos), if I would stick two sticks of 4Gb 1600Mhz RAM in it?

Or put more money in to it and upgrade to an Intel i5 (2500K?) kinda thing, but then would it be enough to only change the CPU and mobo plus RAM? Or I would need to change then the power supply and video card as well?

Or should I fork deeper and go for a Samsung NP700 laptop?

Thank you in advance

Computer hardware can last years and years, if you treat it right (i.e., don't take a sledgehammer to it) and run a slim OS.
My question would be what DE are you running? If Gnome or KDE or Unity maybe you should try installing a lightweight WM like Openbox or even Awesome, and boot into that when you want to do a lot of video editing.
Before you upgrade any hardware (and your hardware is still plenty adequate and up-to-date) install and run htop while crunching video to see if it is indeed your processor or RAM that tanks during editing.

---

### Post by gesti on 2012-06-22
For editing I run Archlinux with Gnome. Awesome looks good, will give it a try, just little bit afraid of it as actually my wife is the one who does the video editing and she's kinda in war with computers :D

---

### Post by gesti on 2012-06-22
Gave awesome a try but it didn't help much. Even I shut down most of the unnecessary services (like gdm, apache, mysql). And still I couldn't feel any different compared to when I run OpenShot in gnome3.
Looked at OpenShot in htop. When I loaded **10 minutes** worth of full HD - **AVCHD format** - videos and started to play around with them (cutting, moving on time line, stretch them) OpenShot was eating **400Mb (10%) of memory** and avarage **50%** of load on all four CPU cores - when stretching videos all four cores went up to **80-90%**.
So it looks to me that video editing with OpenShot is a sledgehammer to my PC... :)
Or maybe I'm doing some thing wrong and shouldn't be editing raw videos, but converted ones?

---

### Post by cortman on 2012-06-22
> **gesti said:**
> Gave awesome a try but it didn't help much. Even I shut down most of the unnecessary services (like gdm, apache, mysql). And still I couldn't feel any different compared to when I run OpenShot in gnome3.
Looked at OpenShot in htop. When I loaded **10 minutes** worth of full HD - **AVCHD format** - videos and started to play around with them (cutting, moving on time line, stretch them) OpenShot was eating **400Mb (10%) of memory** and avarage **50%** of load on all four CPU cores - when stretching videos all four cores went up to **80-90%**.
So it looks to me that video editing with OpenShot is a sledgehammer to my PC... :)
Or maybe I'm doing some thing wrong and shouldn't be editing raw videos, but converted ones?

I don't know anything about video editing, to be honest, so I can't recommend raw vs converted.
Interesting htop test. It looks like getting more RAM would be a waste of money, but a processor upgrade might be the ticket. AFAIK though that's only possible with a desktop. An i5 or i7 with plenty of cores would probably help you out a lot.  Check to make sure the socket is compatible first though.
Good luck!

---

### Post by Yellow Pasque on 2012-06-22
First, make sure you're running 64-bit Ubuntu.

> An i5 or i7 with plenty of cores would probably help you out a lot.
The mobo is Socket 775, so it's not possible to use Core i3/i5/i7 chips. There are some faster quad cores for S775, but OC'ing the Q6600 would be a lot cheaper..

> Samsung NP700
That model has hybrid/Optimus graphics using an Nvidia GTX675, which currently doesn't work with Bumblee/nvidia drivers. Avoid it like the plague at the moment.

---

### Post by cortman on 2012-06-22
> **Temüjin said:**
> 
The mobo is Socket 775, so it's not possible to use Core i3/i5/i7 chips.

Thanks for doing the checking I should have done. :-?

---

### Post by gesti on 2012-06-23
> **Temüjin said:**
> First, make sure you're running 64-bit Ubuntu.
Yep, I'm running the 64-bit version of Archlinux.


> **Temüjin said:**
> There are some faster quad cores for S775, but OC'ing the Q6600 would be a lot cheaper..
Unfortunately the faster core that I could buy (Q8300 2.5Ghz) is just slightly cheaper then an i5 2400 (3.1Ghz) core. So I'll first try to OC. :)

> **Temüjin said:**
> That model has hybrid/Optimus graphics using an Nvidia GTX675, which currently doesn't work with Bumblee/nvidia drivers. Avoid it like the plague at the moment.
Good to know. Thank you.


Thanks for the advice guys, now I know what to do. :)
1. Try OC-ing this might not work as I don't have a top quality RAM, then try OC-ing again with better RAM that would be even good if I decide to upgrade the mobo and CPU.
2. If OC-ing is a no go, then upgrade to i5

---

### Post by gesti on 2012-07-03
Hey Guys,

Just thought to give an update on what has happened with this issue of my.

I've over clocked the CPU (Q6600 originally @2.4Ghz) to 3Ghz. With this I've reached 1470 Mhz on the memory. :) Will take it further, just need to get water cooling and for that I need to save money first. :)

After this little modification I've tested photo "editing" (darktable) and video editing (OpenShot) and it was like having a new PC. Thanks to the OC they run nearly like dream.

---

