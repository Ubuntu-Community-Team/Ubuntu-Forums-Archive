---
title: "Intrepid With nvidia-glx-180"
date: 2009-01-17
forum: Hardware
---

### Post by edwin11 on 2009-01-17
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]Hi all,

i am using the nVidia GeForce 9500 GT card.

Currently, i'm have the binary Xorg driver nvidia-glx-177 installed from the repository.

i can see, also, that nvidia-glx-180 is available, but not installed.

Should i be installing that one (from the repository, through synaptic)?



Thanks and Regards,
Edwin
[/COLOR][/SIZE][/FONT]

---

### Post by mikewhatever on 2009-01-17
It's really up to you. How is the current 177 driver working for you?

---

### Post by macadavy on 2009-01-17
I too, am having problems with the GeForce 9500 GT. Its not listed as one of the supported cards in the 177 module READ ME - although the 9400 & 9600 GT cards are - go figure. I'm going to do a search of this forum for all posts on the 9500 GT to see if there's a fix - you might try doing likewise. Good luck!

---

### Post by edwin11 on 2009-01-17
Hi,

Well, according to [https://bugs.launchpad.net/ubuntu/intrepid/+source/nvidia-graphics-drivers-180/+bug/297543](https://bugs.launchpad.net/ubuntu/intrepid/+source/nvidia-graphics-drivers-180/+bug/297543), one of the thing 180 does is

* Fixed an image corruption issue seen in FireFox 3

but that is more of an irritation than an actual inconvenience.

Another thing is that i'm facing this problem:
[http://ubuntuforums.org/showthread.php?t=1016449](http://ubuntuforums.org/showthread.php?t=1016449)

Further investigations on that issue show that the screensaver (ColorSaver) caused the problems, but i still couldn't solve it, so was also hoping that it's a graphics driver issue and that this new driver would solve it.


Actually, my main concern is, if it's ok to just go to synaptic, select this package (nvidia-glx-180) and install it and let synaptic manage the dependencies and conflicts. Any potential pitfalls/risks?

Also, how come the system (i don't know, maybe the Hardware Drivers control) did not flag this as a possible upgrade?



Thanks and Regards,
Edwin

---

### Post by macadavy on 2009-01-17
Edwin, I did a pretty thorough search of this forum (I won't list all the threads!)
and found this link helpful:  [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
This handy search box turned up the nVidia 180.22 module (the nvidia-glx-180 module listed in the repositories is 180.11 if you check the version - it does *not* support the 9500 GT!). Now all I have to do is install it - it does come with complete instructions so as soon as I figure out how to change the Ubuntu runlevels so the Xorg server doesn't start I can do so... (goes back to seaching forum...)

---

### Post by macadavy on 2009-01-18
Well that settles it: the 9500 GT goes back to the store to be exchanged for a card that is supported.
Lesson learned: do my homework and only purchase a card which is supported by already existing modules (drivers) in the Ubuntu repositories. 
Anything else is asking for more grief than I care to suffer.
(Posted, regrettably, from windoze).

---

### Post by mikewhatever on 2009-01-18
I think it's worth trying 180.11, not sure about 180.22.
Technically speaking, 180.11 is not in the regular Intrepid's repository, but in Intrepid-updates. I can only guess that the reason for such separation is that the new driver is not deemed essential for the majority of users, yet can solve problems for those with new hardware.

---

### Post by edwin11 on 2009-01-18
Hi Mike,

Thanks, i'll give nvidia-glx-180 a go then! Just to confirm that it's safe to just let synaptic handle the dependencies and conflicts?

macadavy: i think you may be mistaken. Yes, even though it's not listed as a supported card even in 177, i have no problems with it save for the 2 irritations that i mentioned. So i can say that it's working rather well for me.



Thanks and Regards,
Edwin

---

### Post by mikewhatever on 2009-01-19
From the description of the packages, nvidia-glx-180 and nvidia-180-kernel-source, it looks like they replace the corresponding 177 versions. Looks pretty safe to me.

---

### Post by Merovius on 2009-01-19
I did it with Synaptic and it worked fine. Using 180.11 now.

---

### Post by cb951303 on 2009-01-19
180.11 is a beta release whereas 180.22 is a stable release. why include 180.11 but not 180.22?

---

### Post by edwin11 on 2009-01-21
Hi all,

Just to add that i have installed 180 from the repository and it's working. Now the irritating image corruption in Firefox is gone.

hmm... not sure why 180.11 is included instead of 180.22 though...



Thanks and Regards,
Edwin

---

