---
title: "Optoma HD70 120hz"
date: 2010-08-26
forum: Hardware
---

### Post by bean72 on 2010-08-26
Hi there,
I have the Optoma HD70 DLP projector connected through RGB to my media server running Ubuntu 9.10. Right now it's running at 60hz, but the projector is capable of running at 120hz. I got an nvidia card in my system. I don't have the option for 120hz in nvidia-settings, but the specs for the projector say it is 120hz capable:

[Optoma HD70 Specifications - 0-1000 Lumen Projector, Projector]("http://www.superwarehouse.com/Optoma_HD70_DLP_Projector/HD70/ps/1494304")


Is it possible to force X to run at 120hz?
Also my screen isn't properly centered, I have to adjust the horizontal position on my projector every time I turn it on. Sometimes its off to the left a bit, sometimes to the right.

Any ideas?

Thanks

---

### Post by jastonas on 2010-09-24
Looking for an answer also. Did you manage to make it work??

---

### Post by bean72 on 2010-09-24
no unfortunately :(
I tried modifying my xorg.conf to force 120hz but my projector still runs at 60hz. I'm not sure what the next step to take is.

Do you have the problem where you have to readjust your horizontal position every time you switch to d-sub?
It's not just one computer that does it, I have tried multiple computers, both with Windows and Ubuntu and I never get a properly centered screen.

---

### Post by jastonas on 2010-09-24
> **bean72 said:**
> no unfortunately :(
I tried modifying my xorg.conf to force 120hz How did you do that??

---

### Post by efflandt on 2010-09-24
I think you misunderstand which Hz is which.  It is natively 720p which would be 60 Hz (except maybe in countries where it is 50 Hz).  According to page 41 of its manual the vertical frequencies it accepts @ 1280x720 (or 1280x768 ) digital or analog are 60,70,75,85 Hz (less or different ranges at other resolutions).

So not sure why you think it is capable of 120 Hz at its native resolution.  None of the resolutions list anything higher than 85 Hz.  And higher than 60 Hz may be out of sync with most recorded video content.  I think flash is 30 Hz max and regular DVDs are effectively 30 Hz due to interlacing unless something interpolates the interlacing to 60 Hz.  70,75,85 Hz would be out of cadence with that.

---

### Post by bean72 on 2010-09-28
Sorry I bought the projector second hand, I dont have a manual so I can't see what resolutions goes with what maximum Hz. I guess the specs I saw in the link I posted earlier was incorrect. Is there any way of getting the projector to display 85Hz at its native resolution, if its capable?
I tried following the thread [http://ubuntuforums.org/showthread.php?t=1572268]("http://ubuntuforums.org/showthread.php?t=1572268") and Lucid does not seem to respond to any changes in the xorg.conf file. I know that the later distros of Ubuntu doesn't need a xorg.conf file, so does Lucid ignore the fact that a conf file exists?

> According to page 41 of its manual the vertical frequencies it accepts @ 1280x720 (or 1280x768 ) digital or analog are 60,70,75,85 Hz (less or different ranges at other resolutions).
Does this mean I should set my resolution to 1280x768 if i connect to my projector through RGB? I'm trying to figure out why the sides of my screen are cut off when my nvidia drivers are installed.

---

### Post by bean72 on 2010-09-28
Nvm, I tried changing the resolution to 1280x768 and I got no cut off anymore. Thanks for your help!

---

