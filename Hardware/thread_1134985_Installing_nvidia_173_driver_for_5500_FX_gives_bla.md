---
title: "Installing nvidia 173 driver for 5500 FX gives black screen after reboot"
date: 2009-04-24
forum: Hardware
---

### Post by ofir_k on 2009-04-24
Hello,

I am using nvidia geforce 5500fx on my machine. When trying to install the nvidia driver (version 173), I always get a black screen after reboot.

I have tried installing the driver with the "Hardware Driver" on kubuntu jaunty final release fresh install, and with Evny (uninstalling the driver between).

To repair X, I just reboot to the non-graphic mode and choose xfix and when it is done, normal boot.

I experienced this problem (of black screen) also in Hardy (I upgraded to Jaunty mainly for fixing this issue). In Hardy, I also tried with the "Restricted Drivers" on gnome, and with Envy with no success in both.

Xorg.conf after installing the driver, and Xorg logs after the black screen occurs are attached. Note that the logs are from the reboot after the black screen (when I run xfix).

Thanks in advanced,
Ofir

---

### Post by ofir_k on 2009-04-24
I investigated it a little bit more, and found that the X server was failed to load (when I got the black screen I tried to turn on the LEDs in my keyboard by pressing Caps-Lock or Num-Lock buttons.They didn't turn on, so I figured out that it is not nvidia driver problem).

I have a TV card of Hauppauge. After disconnecting it, everything got back to work.


Is there any one who knows why the TV card caused this issue?

---

### Post by ofir_k on 2009-07-13
I can't solve this problem.

Everytime I install the nvidia driver (173) and reboot, I get a black screen and nothing works. The screen is dead (black), the keyboard, the mouse - everything!

I feel like the money spent on the nvidia card is worthless!

Please help me. I really don't know what to do next.

---

### Post by ofir_k on 2009-07-29
I found a post saying that the nvidia driver startup is very slow and xorg server timeout is too short:
[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/a708e81cbeddd59e](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/a708e81cbeddd59e)

I followed his instructions:
```
To resolve the problem I set in /etc/kde4/kdm/kdmrc: 
 
    [X-*-Core] 
     ServerTimeout=120 
```However, the problem still persists. After I followed the instructions, enabled the nvidia driver and rebooted, I got this screen:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=122869&stc=1&d=1248899456&thumb=1[/IMG]

And it just stayed that way.


I really appreciate any help/advise!

---

### Post by ofir_k on 2009-07-29
I just read two xorg logs from different times and found that the xorg log always ends with:
```
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized AGP GART.
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00000000, 0x00000624)
(WW) NVIDIA(0): WAIT (1, 6, 0x8000, 0x00000000, 0x00000624)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(WW) NVIDIA(0): WAIT (2, 1, 0x8000, 0x00000000, 0x000006e0)
(WW) NVIDIA(0): WAIT (1, 1, 0x8000, 0x00000000, 0x000006e0)
(II) Loading extension NV-GLX
```

Loading the nvidia driver is the last thing the xserver does before it crashes.
The WAIT seems to be something bad that shouldn't happen.

---

