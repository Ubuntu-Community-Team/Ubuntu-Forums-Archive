---
title: "webcam not detected on Lenovo Yoga Duet7 13ITL6 with ubuntu 20.04.3 LTS and 21.10"
date: 2022-01-13
forum: Hardware
---

### Post by ndonio on 2022-01-13
Dear all,

I have a Lenovo Yoga Duet7 13ITL6. I installed ubuntu 20.04.3 LTS and then I installed ubuntu 21.10 from scratch with the hope to solve the following issue but without success. With both ubuntu versions, rear and front integrated webcams were not recognized. lspci and lsusb commands didn't show anything indicating the presence of a webcam and no /dev/video* link were created. I followed the advices of several forums suggesting to install uvcvideo and load it manually with modprobe but it didn't work. I then decided to start from scratch to avoid possible issues due to the many trials I did. So now I have a fresh installation of ubuntu 21.10. Could someone guide me step by step to try to solve the problem?
Thanks a lot in advance!

Antonio

P.S.: I created another post about a problem with the integrated speakers in the same computer with the same versions of ubuntu.

---

### Post by philemine on 2022-10-31
Did you manage to fix it? 
I face the same issue. Tried Ubuntu 22.04 and I can see that there is `/dev/video0`, but neither cheese nor vlc or firefox can use the webcam.

---

