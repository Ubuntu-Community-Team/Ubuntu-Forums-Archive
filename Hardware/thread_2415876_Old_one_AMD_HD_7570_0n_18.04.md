---
title: "Old one AMD HD 7570 0n 18.04"
date: 2019-04-02
forum: Hardware
---

### Post by stevehendo34 on 2019-04-02
I know that the old radion flx* drivers only went to **15.X**.
Dose anyone know how well the open source drivers radeon or amdgpu work.

I have three options.
[LIST]
[*] Install **Ubuntu 18.04** and use open source drivers.
[*]Install **Ubuntu 15.04** and use proprietary drivers.
[*]Install **Windows 10**, (I have an extra key).
[LIST]
[*]The A8-3800 apu dose have HD6620 integ. graph.
[*]The HD 7570 will run in dual graphics mode with it.
[/LIST]
[/LIST]

I cant decide will it be worthless to run the HD 7570 on the open source drivers. Hope you don't mind me asking for opinions!

---

### Post by Claus7 on 2019-04-02
Hello,

similar card here hd 5650. Using ubuntu 18.04.2 with open source drivers. General impression is that things are working pretty nicely. Applications, web browsers, internet, videos. I do not know if you are a gamer and how some games might behave. I think that if your demands are mostly related with the latter, ubuntu 15.10 might be the option for you. Other than that, 18.04 with open source drivers would be ok.

Regards!

---

### Post by Autodave on 2019-04-02
I would not recommend 15.10 since it is no longer supported!  Go with 18.04 and use the open source drivers.

---

### Post by mastablasta on 2019-04-03
status and available features of Radeon opensource driver are available here: [https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/)

here are some good tests using Phoronix test suite with latest kernels: [https://www.phoronix.com/scan.php?page=article&item=amdgpu-radeon-linux50&num=1](https://www.phoronix.com/scan.php?page=article&item=amdgpu-radeon-linux50&num=1)

looks like Radeon is quite similar to official AMD drivers in performance. maybe juts my poor eye sight but i really can't tell the visual difference between 110 FPS or 115 FPS. i also can't see much differenc eon the TV between HD ready (720p), HD (1080p) or 4K

if you are into serious gaming or you have a need for GPU then at the moment windows 10 might be a better choice, although radeon driver progressed a lot in the past few years.

---

