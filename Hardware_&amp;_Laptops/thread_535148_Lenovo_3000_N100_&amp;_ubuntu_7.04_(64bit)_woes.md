---
title: "Lenovo 3000 N100 &amp; ubuntu 7.04 (64bit) woes"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by Some_ux on 2007-08-26
Ok, so i bought a Lenovo 3000 N100, core 2 duo 1.73, 2Gigs of mem and a nvidia 7300GO card.
The machine came along with vista Home Premium which i intended to dual boot with ubuntu feisty (64).

I will try to describe my learning curve in the hope that it will aid others that find themselves in my predicament. This might also help support folks in understanding what goes in the mind of newbie.

Installation was smooth, (well, as smooth as it can get for someone who knows jack about linux).
So after getting over the shock of using a non MS OS, i noticed the sound was missing.
I read the forums, and luckily stumbled on a thread which solved my problem. The trouble is that for someone who knows nothing about linux, the forums are rather overwhelming, and contain a plethora of useful and useless discussions which more often than not end up being too technical and intimidating (yes, CLI is not for the feint hearted) 
This is not meant to sound as criticism, but rather an observation made by a layperson.

Anyway, back to the hardware issue, took me a while to understand that ubuntu uses a package system for all software related distributions, and even longer still to understand that drivers are created and maintained by various unrelated parties. Furthermore, some drivers are open source and others are restricted propriety software. Also, i figured that not all such packages are immediately available and that some are not even included in the official ubuntu 7.04 repository. (I find this odd, as some packages are absolutely essential for the OS to function and are not included)

I found that all sound related drivers are related to something called ALSA, and that new drivers were available on the ALSA project website and that those might address my problem. So I downloaded the latest driver (at the time .014) and discovered that i need another package which would allow me to compile the driver. (essential compilation stuff package)

Compiling stuff is not something which i consider a plug & play feature, nor is it something which anyone would feel comfortable enough to do (unless they wrote the code themselves) IMHO anyway.
OK, so i learned that there is a compilation system which uses make files which perform the actual compilation and linking of the various source files with the appropriate libraries of the correct version.

Compiling and installing seemed to have addressed the sound issue, After i rebooted the system.

OK, so now i wanted to make the nifty desktop effects work (ones which i heard ubuntu can do)

Once Again i was overwhelmed, apparently there are two projects called compiz and beryl which make the nifty windows (soon to be united apparently). I also learned that the ubuntu windows system, is comprised of various levels, at the bottom of which resides a client/server architecture called xwindows, formerly called X11 which is now xorg. Above it, there is a window manger (GNOME for ubuntu installation) and that compiz (for ubuntu installation) somehow manages to utilize 3d acceleration of modern graphics cards by using a 3d acceleration API called Open-GL (which is sort of a Non MS directX thinggy) which has a special version for the Xwindows system (xgl).

Here is where I stumbled, enabling desktop effects caused my laptop screen to go white for a few seconds then go back to normal without much change. I quickly searched the forums for anything nvidia 7300GO related but was not able to find anything which either confirmed or disproved that compiz can work with my card. I checked to see whether my card was using restricted drivers (non open source), but the restricted drivers manger did not show any such.

I don't know where to go from here, My educated guess is that nvidia 7300GO glx drivers are somehow not working properly, thus not allowing the desktop effects to function properly. But i don't know where to get the drivers, nor do i understand how to cause compiz to use them even if i did.

Finally, I don't know if it is related, but when i boot my laptop, i get:
PCI: Failed to load mem resource #6: bla bla...
At first i assumed it was an error which was related to some sort of unsupported device i have on my laptop (like the fingerprint reader) and dismissed it as a harmless annoyance (one which hopefully future ubuntu versions will address). 
But now i am not so sure, possibly nvidia cards create some sort of shared memory space which ubuntu fails to utilize thus messing up the glx drivers ? (a wild theory, but then, i have no idea how this stuff works)

Any help on the failed mem error message and the lack of desktop effects would be appreciated.

---

### Post by wjp.reg on 2007-08-26
here's a useful howto

[How to Install Beryl with latest nvidia drivers in Ubuntu Feisty Fawn]("http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html")

good luck

---

### Post by lil_niles on 2007-09-02
a word of encouragement: understanding how files are stored and how to build things from source with linux was the hardest thing for me to grasp. in other words, you've already tackled the most frustrating thing about linux (basically for us MS users, the major differences are the most frustrating). keep at it.

if you can't find any how to's on the ubuntu forum, don't be afraid to go onto google and try external how to's. NONE of the how to's solved my wireless card problems on the ubuntu forums , and the first external one i tried fixed it imediately. wish i could help more, but good luck!

---

