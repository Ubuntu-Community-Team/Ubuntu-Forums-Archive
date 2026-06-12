---
title: "Asus laptop fan (and maybe other components) stay on when lid-close or suspend!"
date: 2017-07-12
forum: Hardware
---

### Post by maze88 on 2017-07-12
Hi,
I am experiencing various problems with my **Asus Zenbook UX410UQ**. It has a single-boot configuration only with Ubuntu, and contains _integrated  graphics_ (intel HD620) _and dedicated graphics_ (GeForce 940MX).
For some further system details that could be relevant for the issue, see **sysdetails.txt** in the attached zip file.
I suspect the problems may be related to a single cause or mis-configuration, or from my multiple attempts to configure the system to work properly with Prime and/or Bumblebee.

_ Symptom list:_
[LIST=1]
[*][COLOR=#a52a2a][Major][/COLOR] Sometimes during lid-close or suspend command from menu bar the laptop appears to suspend (black screen) but the fan (and perhaps other components?) remains on. The first time this occured was very scary, because I already put my laptop in its case...when reopening I was welcomed by a worrying gust of hot air.
Log files:[INDENT]• ***syslog**.1.suspendWithHotFan* (in the attache zip fle) - occured around 11AM, I would guess/suggest grepping `grep -i -E '(error|fail)'` as a start of analysis focus.
• ***kern.log*** for the suspendWithHotFan crash is about 1GB big, and mainly contains this line spammed (in about 6 million lines):
```
`Jul  2 11:32:07 ux410uq kernel: [190460.311490] nouveau 0000:01:00.0: fifo: PBDMA0: 00006000 [GPFIFO GPPTR] ch 4 [007f9ad000 Xorg[4527]] subc 0 mthd 0000 data 00000000`
```
if you want me to grep or isolate anything else from that log, just say.
[/INDENT]
 
[*][COLOR=#a52a2a][Major][/COLOR] Sometimes on user switch the laptop locks up, leaving a black screen with a '_' sign. **Ctrl+Alt+[F7-F1,Del]** do not appear to affect the system. I end up doing either a hard reboot (power button) or magic *SysRq* key combo **Alt+SysRq+R,E,I,S,U,B**.
Log files:
• ***syslog**.2.crash1040ishOnUserSwap* (in the attache zip fle) - 10:40 was the time the user swap that jammed the system occured. 
[*][COLOR=#ff8c00][Minor][/COLOR]  When resuming from suspend (if the system didn't lock up as described above) screen flickering occurs (on integrated and external monitors). This can easily be stopped if I "wipe" a window or maximize or full-screen (F11)  Size  across the screen to sort of "refresh" it. 
[/LIST]

This is my first post in the forums, and I am a relatively new Linux  user and learning. Let me know if I should provide any other data!

---

### Post by maze88 on 2017-07-13
Is *bumping* a thread legal here?

---

