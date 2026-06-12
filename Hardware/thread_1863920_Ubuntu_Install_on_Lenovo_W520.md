---
title: "Ubuntu Install on Lenovo W520"
date: 2011-10-18
forum: Hardware
---

### Post by simeonipicker on 2011-10-18
Hi,

I'm a new user to ubuntu and I've decided to dualboot it with Win7 on my Lenovo W520. It's i7 Vpro, 8GB of RAM and Nvidia Quadro 1000m

Ok - so initially I tried to install ubuntu 11.10 x64 to make use of my 8Gb of ram. Install was fine but for the life of me, I couldn't get stutter free youtube video, it was either down to flash or the Nvidia driver but after 3 days of trying different things and mucking up my xconf I decided to go to 32bit.

After installing 32bit I installed the PAE kernel to try and make use of the 8GB, all went fine. Installed the Nvidia drivers and flash and finally stutter free video!

I had a strange intermittent problem where the touchpad would not work a reboot would fix but then it would occur again. I download the synaptik manager and that has seemed to fix it.

So I was happy.. Until I booted this morning and I've got no internet! It connects to the wireless fine but it wont download any updates nor can I surf to any webpages.

I'm not sure where to start... What logs should I check? I've tried rebooting multiple times and the problem still persists. It was working fine before, so I'm not sure what has caused this?

Any help would be much appreciated...

---

### Post by houserparker on 2011-10-21
Hey dude,

I've got the same Laptop and had similar problems on 11.04.

I'm now running 11.10 x64 and occasionally it doesn't connect on boot and after suspend but I normally just do sudo ifconfig wlan0 down to restart it and away it goes.

When I was using 11.04 apparently there was a bug in the firmware that stops the card working reliably on wireless N. I'm not sure whether it has been fixed since then and you are facing another problem but here's the fix anyway.

Create a new file:-
```
sudo gedit /etc/modprobe.d/inteldisablen.conf
```And place the following in it:-
```
options iwlagn 11n_disable50=1 11n_disable=1
```Reboot.

I would have done this to my machine but I prefer to have the inconvenience than miss out on wireless N 

Hope this helps.

---

### Post by simeonipicker on 2011-10-23
Thanks for the reply! 

I think I'm going to just restart it each time like you do. I don't like the idea of no wireless N! Is there anywhere this bug is already reported? Just want to see if I can track status of a fix.

Regards

---

### Post by houserparker on 2011-10-24
I got back to Uni today and sure enough the problem has reared it's head again. Below is the bug and all though they mention the 6200 it still applies to the 6205.

They mention by upgrading to 3.1.0-0301rc9-generic fixes the problem but I haven't tried it yet.


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/871254](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/871254)

---

### Post by houserparker on 2011-10-27
I just installed the kernel I mentioned above and it seems to have done the trick. Will report back when I have connected at Uni as the connection there was always more problematic.

---

### Post by mörgæs on 2011-10-27
Moved to Hardware and Laptops.

---

