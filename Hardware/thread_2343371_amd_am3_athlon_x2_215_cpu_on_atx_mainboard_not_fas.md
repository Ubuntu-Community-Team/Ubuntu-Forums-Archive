---
title: "amd am3 athlon x2 215 cpu on atx mainboard not fast enough for youtube?"
date: 2016-11-15
forum: Hardware
---

### Post by ubto66 on 2016-11-15
Pc had an amd athlon x2 250 3ghz cpu. The psu got damaged and the cpu. I assumed the mainboard as such got destroyed. I obtained a new psu and an used athlon x2 215 2.7ghz. Then the pc worked again. With the athlon 250 cpu watching hd youtube videos worked. With the athlon 215 displaying hd videos the cpu gets close to 100%. After displaying several hd videos video begins to stutter. All applications begin to stutter. If pc is idle, system monitor shows that one cpu core is close to 100% and the other about 20%. Cores are shifting these values. In resources xorg has a higher value than the others. Tested with graphics card radeon hd 4200 and nvidia 8400. Same result with both. Is the cpu not fast enough? Suggestions to correct it? Thank you.

---

### Post by mastablasta on 2016-11-16
top or htop command shoul dshow you what porcess is eating the CPU. 

in both mentioned cases the GPU should take care of youtube videos. so something else seems to be wrong. hard ot say what. also check the system logs (there hsoul dbe a logviewer preinstalled) for any errors.

regarding HD 4200- test if you have 3D hardware acceleration as you should have it: > **Testing the driver**


To look for boot messages/errors, check 
```
dmesg | egrep 'drm|radeon'
```
To see your OpenGL information, you can run the commands below. Make sure your OpenGL renderer string does not say "software rasterizer" or "llvmpipe" because that would mean you have no 3D hardware acceleration: 
```
sudo apt-get install mesa-utils
LIBGL_DEBUG=verbose glxinfo
```

more here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

nvidia 8400 might require a proprietary driver for that (3D HW accel).

---

### Post by ubto66 on 2016-11-17
Thank you.

Tested dmesg | egrep 'drm|radeon' on radeon 4200 and nvidia 8400.
Both did not result in error messages.

Tested LIBGL_DEBUG=verbose glxinfo on radeon 4200 and nvidia 8400.
Both resulted in no software rasterizer or llvmpipe message.

Something makes the xorg cpu usage high.

---

### Post by mastablasta on 2016-11-18
then it really must be something else not the GPU. check top or htop next to see what it is.

try switching the browser.

make sure adobe flash is propperly installed.

---

### Post by ubto66 on 2016-11-18
Thank you. Command top says, that xorg is using more on resources than the others. 
Isn't top the same as system monitor?

It was a good suggestion to test another browser. I tested youtube hd videos on the midori browser. nvidia 8400 graphics card, the card I prefer. After playing several videos, no video or other program begins to stutter. On firefox videos and other programs begin to stutter. You say the graphics card manages the video. However it must be affecting the cpu too. If I play a youtube hd video on firefox both cores' performance are close to 100%. If midori is playing youtube hd videos, both cores' are about 70%. After closing all programs, both cores goes down. Not like on firefox where one core is about 100% performance and the other about 20% and then the cores shift these values.

About flash, youtube does not use flash?
On linux I install flash on firefox. After that flash is updated via software updater.

Ubuntu's homepage says 2ghz duo core should do.

---

