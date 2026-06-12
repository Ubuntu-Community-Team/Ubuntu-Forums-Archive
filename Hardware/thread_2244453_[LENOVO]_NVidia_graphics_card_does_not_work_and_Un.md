---
title: "[LENOVO] NVidia graphics card does not work and Unity will no longer log in."
date: 2014-09-16
forum: Hardware
---

### Post by blackbird34 on 2014-09-16
Hi, 

Typing from the horrors of Windows 8. Please help ;)
I installed Ubuntu 14.04 on a Lenovo Z50-70, everything went fine except that it did not pick up the NVidia GeForce 820M graphics card. In System Settings > Details, it only picked up the Intel Haswell integrated graphics from the i5 processor.
I tried to install the contents of the xorg-edgers ppa and the system broke, it now hangs on login. I am going to reinstall from scratch and I would like to know how you all got your NVidia cards to work. Please:p

---

### Post by gifford on 2014-09-16
Did you try using the Nvidia driver 331.38 that Ubuntu installs?
My recommendation would be to install this from software and updates, additional drivers.
It worked for my Quadro 4000.

---

### Post by papibe on 2014-09-16
Hi blackbird34.

You may have an hybrid graphic system (2 graphic cards always available).

Could you open a terminal, run this commands and post back the results (you can copy/paste the text)?
```
lspci -nnk | grep -iA2 vga

lsmod | grep -E 'nvidia|i915'
```
Regards.

---

### Post by blackbird34 on 2014-09-16
I am currently on a live system. I'll post again in a few minutes when it finishes but the live system should be the same as the end result no?

```

ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b)
    Subsystem: Lenovo Device [17aa:380d]
    Kernel driver in use: i915
ubuntu@ubuntu:~$ lsmod | grep -E 'nvidia|i915'
i915                  783485  5 
i2c_algo_bit           13413  2 i915,nouveau
drm_kms_helper         52758  2 i915,nouveau
drm                   302817  7 ttm,i915,drm_kms_helper,nouveau
video                  19476  2 i915,nouveau





```

I did try Additional Drivers before the install got borked, but it didn't offer me anything.

---

### Post by grahammechanical on 2014-09-16
Nvidia was very, very slow producing a Linux graphic driver for its Optimus technology. This link shows just how recent Nvidia developers got working on it. The Link relates to Ubuntu 13.10 and things have moved a little bit by the release of Ubuntu 14.04

[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

[http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html)

See, section 7 Nvidia Optimus Tweaks

[http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html)

And a Ubuntu wiki

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Regards.

---

### Post by blackbird34 on 2014-09-17
Well thanks very much grahammechanical!! I'll try that. Long time since i was on this forum much (basically last time i got Ubuntu onto a computer, as a noob, and ironed out all the problems at the time), happy to see you're still all so helpful :)
Installing it now, will reboot before bed to have a look. I'd seen that webupd8 article but i think i combined all the wrong bits of Andrew's advice in the worng ways, installing conflicting packages, etc.
Good night, until i report back.
bb34

Edit: success! Now to keep it that way. And to find out where the switch between Nvidia and Intel graphics has hidden itself. EDIT: i'd forgotten to install prime-indicator from Synaptic.

---

