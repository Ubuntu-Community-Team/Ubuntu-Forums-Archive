---
title: "Frozen system on the web browser opening"
date: 2018-10-22
forum: Hardware
---

### Post by antdcs on 2018-10-22
Hello, i am not new on ubuntu, and i never had a problem like this before. First i had to say that my cpu is a intel q6600 and my gpu is a radeon r7 260x. The problem is i cant open a web browser because in the moment i do it the system is fronzen and i have to reboot manually. I don´t belive this only afect me so maybe some one can help me a little.

---

### Post by hackerb9 on 2018-10-22
I had a laptop that had similar symptoms, although it wasn't just the web browser that could crash it. I believe anything that used OpenGL over a certain resolution (was it 800x600?) would make it immediately hang. After many reinstalls and much gnashing of teeth, I finally discovered that the problem was the hardware: the specific graphics chip I had was actually known to go bad over time as it burned itself out from overheating. Since it was a laptop, there was nothing I could do but send the laptop to the e-cyclers. 

Have you tried setting the resolution lower (xrandr -s 800x600)? If it stops freezing, I'd bet it's a hardware problem and only a replacement will actually fix it. 

Alternately, maybe try a different browser or, if you can, configure it to not use the GPU.

---

### Post by antdcs on 2018-10-22
Well it can be hardware but this hardware its working perfect on windows so .... it maybe posible the drivers on linux don´t use the fans correctly.

---

### Post by hackerb9 on 2018-10-22
Could be a fan issue, but then it'd crash if you did something like: ```
( yes & yes & yes & yes & yes & yes  & yes & yes) >/dev/null
``` . Does it? (Of course, "pkill yes" to stop the test).

It's possible the ACPI system is acting differently if it detects Microsoft Windows. What's the make and model of the computer?

Also, are you sure the computer is actually completely frozen? Have you tried ssh'ing in remotely? What about the Magic SysRq key?

Also, what version of Ubuntu are you running? If it's 16.04, it may be running Linux 4.4.0 which apparently was [buggy ]("https://help.ubuntu.com/community/AMDGPU-Driver")with the R7 260.

---

### Post by ajgreeny on 2018-10-22
If it is only the browsers that cause the problem try renaming the configuration folders in your home for those browsers (with them closed, of course), then tyr running them again.

Bad configuration can often cause web-browsers to crash, though I can not promise that is your problem, but it is the first and easiest step to try first.

---

### Post by antdcs on 2018-11-03
OK, i try tu put the fans at maximun whit fan control and i can see is not the temp of the grafic. I have windows 10 working perfectly on this pc, so must be something on the drivers.

---

