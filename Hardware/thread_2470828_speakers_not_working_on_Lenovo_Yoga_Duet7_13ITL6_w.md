---
title: "speakers not working on Lenovo Yoga Duet7 13ITL6 with ubuntu 20.04.3 LTS and 21.10"
date: 2022-01-13
forum: Hardware
---

### Post by ndonio on 2022-01-13
Dear all,

I have a Lenovo Yoga Duet7 13ITL6. I installed ubuntu 20.04.3 LTS and then I installed ubuntu 21.10 from scratch with the hope to solve the following issue but without success. With both ubuntu versions, I can hear the sound only if I plug the headphones but I can't hear anything from the integrated speakers. I checked alsamixer and pavucontrol and all the volumes are at the maximum. In pavucontrol and in the system settings -> sound I can see the volume bar monitor moving, as if the sound were properly going out from the speakers. I followed the advices of several forums but without success. I then decided to start from scratch to avoid possible issues due to the many trials I did. So now I have a fresh installation of ubuntu 21.10. Could someone guide me step by step to try to solve the problem?
Thanks a lot in advance!

Antonio

P.S.: I created another post about a problem with the integrated webcams in the same computer with the same versions of ubuntu.

---

### Post by ndonio on 2022-01-15
To have it working, I found around that the sof-firmware-signed must be installed too; however, with ubuntu 21.10 it is not compatible with the package linux-firmware. This is documented here

[https://bugs.launchpad.net/ubuntu/+source/firmware-sof/+bug/1930868](https://bugs.launchpad.net/ubuntu/+source/firmware-sof/+bug/1930868)

I then upgraded to ubuntu 22.04. Still the speakers were not working, although the monitor bar in pavucontrol was indicating that the sound was going out from the speakers. I  then modified the /etc/pulse/default.pa file by commenting the line

load-module module-suspend-on-idle

as suggested here

[https://forums.linuxmint.com/viewtopic.php?f=49&t=335242&start=40](https://forums.linuxmint.com/viewtopic.php?f=49&t=335242&start=40)

and it worked for me. I mark the post as solved.

---

