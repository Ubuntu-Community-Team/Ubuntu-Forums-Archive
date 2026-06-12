---
title: "How to make sound buttons work on a laptop"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by alanmzifa on 2007-04-16
Hi, I have Ubuntu 6.06 installed on an old **Dell Latitude L400 laptop**. 

Mostly everything works fine but the volume up/down buttons don't seem to work **(Fn button + F5 or F6)** so I'm without sound.
The speaker in the laptop does work as I can force it to beep during BIOS boot.

Does anyone have any suggestions? Ubuntu seems to recognise an internal sound device, namely a **Cirrus 4281** which ALSA is supposed to support from what I can see.


thanks in advance

---

### Post by Grout58 on 2007-04-16
Sorry to talk off topic, but I also have an L400 with Ubuntu but I find it a bit sluggish.  I have the 700mhz p3 with 256 megs of ram in mine.  Is there anything you do to speed it up?  My sound works out of the box with edgy so Im not sure, never tried the sound buttons.

---

### Post by alanmzifa on 2007-04-16
Grout58, My specs are exactly the same (except for the versiobn of Ubuntu).

 It's an old machine that I bought 2nd hand just for my partner to use when she wanted to browse the internet so for that it's as fast, if not faster, than my XP machine.
[B]
**Can you confirm that your volume works as per above Fn + F5/F6?**

Also, how did you install as the L400 has no CD drive? [/B]I bought a 2nd hand one of those too but was unlucky as it doesn't seem to work. Ubuntu can't see it and the drive seems defective. In the end I had to install Ubuntu by temporarily putting the laptop drive in my desktop machine and then swapping over and making some guesses to get X configured.

---

### Post by Grout58 on 2007-04-16
When I get home I will check to see if the volume keys work.  I installed it using pxe netboot install.  The images are here. 
[http://mir2.ovh.net/ftp.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/](http://mir2.ovh.net/ftp.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/)

set up a tftp server with those images and it will download ubuntu and install it.  It works awsome.

---

### Post by alanmzifa on 2007-04-16
> **Grout58 said:**
> When I get home I will check to see if the volume keys work.  I installed it using pxe netboot install.  The images are here. 
[http://mir2.ovh.net/ftp.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/](http://mir2.ovh.net/ftp.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/)

set up a tftp server with those images and it will download ubuntu and install it.  It works awsome.

You lost me at "work."...I'm no Linux/PC guru as you can tell. Do you know anywhere where there are detailed instructions of how to do this. I searched but couldn't find any that were for the current version or detailed enough for me to make sense of.

p.s. thanks for checking the buttons out

---

### Post by marcelo.matos on 2008-02-19
Dear **_Grout58_**, did you tried the sound buttons? I have the same laptop, and the sound buttons doesn't seem to work.

The sound wasn't working but i made something using alsamixer and it's working. Don't ask me what I did. I really don't know. I tried every tutorial and nothing worked. One day it the sound was made. :P

I noticed that the sound doesn't work when the laptop is on the docking station. I mean,  the internal speaker, neither the phone jack and neither the docking station audio out. Even the mic die. Altough the system config remains untouched (and apparently ok).

**_alanmzifa_**

I used a second hand drive too. I noticed that the bios setup (press F2 on boot) have an option to boot using a network. I'm not sure if you can use this to boot using the other lan computer drive.

Trying to help, I was searching for a way to help you. Then, I noticed how old is this thread, and a post of yours where you say you used a net install. Could you tell me how you made it? It can help others. 8)

--------------------------------------------
Other stuff
--------------------------------------------

I also have problems with cpufreq, battery management, and usb hub. If anyone can help me with these, I would apreciate. :)

Thanks!

---

