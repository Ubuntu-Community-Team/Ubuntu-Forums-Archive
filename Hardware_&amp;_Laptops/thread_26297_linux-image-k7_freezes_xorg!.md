---
title: "linux-image-k7 freezes xorg!"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by infinito on 2005-04-12
Hi!

I'm moving from debian sid to hoary, and everything seems to be as great as expected... But there's something very wrong! Using linux-image-k7 (which installs linux-image-2.6.10-5-k7) just freezes xorg server. 

I'm using a Nvidia GeForce 2 MX400, using both drivers "nv" and "nvidia", and get the same result: total freeze of xorg after a few seconds of gnome activity.

Can anybody give an idea to solve this issue??

Of course, my cpu is an AMD Athlon 1400 (K7, you know!)

Thanks in advance!

---

### Post by nad on 2005-04-12
Yeah. I'm moving from hoary back to sid. There are just too many things broken. Blame the six month release cycle. I was hoping that ubuntu could do it, but there is just too much.

These two distros are now incompatible. See Ian Murdochs' blog re ubuntu.

Dan M

---

### Post by ntd on 2005-04-12
[QUOTE=infinito]Hi!

I'm moving from debian sid to hoary, and everything seems to be as great as expected... But there's something very wrong! Using linux-image-k7 (which installs linux-image-2.6.10-5-k7) just freezes xorg server. 

I'm using a Nvidia GeForce 2 MX400, using both drivers "nv" and "nvidia", and get the same result: total freeze of xorg after a few seconds of gnome activity.

Can anybody give an idea to solve this issue??

Of course, my cpu is an AMD Athlon 1400 (K7, you know!)

Thanks in advance![/QUOTE]


I have the same problem, except my processor is an Athlon XP 2100+, and it is a straight up Ubuntu install, never had Debian

It does it randomly too...sometimes immediately, sometimes after a while.

---

### Post by infinito on 2005-04-13
I thought it was my GeForce2 the one who was causing the trouble, but with windows xp everythings is ok.

I've switched back to debian, and with kernel 2.6.10 i also get those random freezes, so rigth now i'm not sure what's going on....

Everthing seemed ok back in my debian days, but now every linux os fails... Very strange.... very strange....

I've got this syslogs errors:
```

kernel: 2.6.11-soho
nvidia: 7174

Apr 11 13:34:55 localhost kernel: spurious 8259A interrupt: IRQ7.
Apr 11 13:39:34 localhost kernel: Unable to handle kernel NULL pointer dereference at virtual address 000000bc
Apr 11 13:39:34 localhost kernel:  printing eip:
Apr 11 13:39:35 localhost kernel: f9175930
Apr 11 13:39:35 localhost kernel: *pde = 00000000
Apr 11 13:39:35 localhost kernel: Oops: 0000 [#1]
Apr 11 13:39:35 localhost kernel: PREEMPT 
Apr 11 13:39:35 localhost kernel: Modules linked in: binfmt_misc tuner bttv video_buf firmware_class i2c_algo_bit v4l2_common btcx_risc tveeprom videodev 8250 serial_core via686a i2c_sensor i2c_isa i2c_core nvidia
Apr 11 13:39:35 localhost kernel: CPU:    0
Apr 11 13:39:35 localhost kernel: EIP:    0060:[pg0+953035056/1068938240]    Tainted: P      VLI
Apr 11 13:39:35 localhost kernel: EFLAGS: 00210202   (2.6.11.6-soho) 
Apr 11 13:39:35 localhost kernel: EIP is at _nv005283rm+0x64/0x134 [nvidia]
Apr 11 13:39:35 localhost kernel: eax: 00000008   ebx: f3482ce0   ecx: 00000008   edx: 00000000
Apr 11 13:39:35 localhost kernel: esi: c1d0000d   edi: 00000000   ebp: f4de5dac   esp: f4de5d84
Apr 11 13:39:35 localhost kernel: ds: 007b   es: 007b   ss: 0068
Apr 11 13:39:35 localhost kernel: Process XFree86 (pid: 2849, threadinfo=f4de4000 task=f6adc5c0)
Apr 11 13:39:35 localhost kernel: Stack: f5357800 c1d0000d 02050000 f9084836 c1d0000d 00000011 f4de5dcc f9086cce 
Apr 11 13:39:35 localhost kernel:        f3482da0 f3ab7340 f4de5e1c f908dd1a f5357800 f6901a00 c1d0000d 02050000 
Apr 11 13:39:35 localhost kernel:        f368be80 00000000 f4de5e1c f908dd05 c1d0000d 0000000b 00000000 00000000 
Apr 11 13:39:35 localhost kernel: Call Trace:
Apr 11 13:39:35 localhost kernel:  [pg0+952047670/1068938240] _nv007621rm+0x1a/0x58 [nvidia]
Apr 11 13:39:35 localhost kernel:  [pg0+952057038/1068938240] _nv007608rm+0x16/0x38 [nvidia]
Apr 11 13:39:35 localhost kernel:  [pg0+952085786/1068938240] _nv001239rm+0x162/0x1e0 [nvidia]
Apr 11 13:39:35 localhost kernel:  [pg0+952085765/1068938240] _nv001239rm+0x14d/0x1e0 [nvidia]
Apr 11 13:39:35 localhost kernel:  [pg0+952047670/1068938240] _nv007621rm+0x1a/0x58 [nvidia]
Apr 11 13:39:35 localhost kernel:  [pg0+952084639/1068938240] _nv001246rm+0x67/0x260 [nvidia]
Apr 11 13:39:35 localhost kernel:  [pg0+952184566/1068938240] _nv001740rm+0x12/0x18 [nvidia]
Apr 11 13:39:35 localhost kernel:  [pg0+953366120/1068938240] _nv004169rm+0x88/0x94 [nvidia]
Apr 11 13:39:35 localhost kernel:  [pg0+952065867/1068938240] _nv002889rm+0x33/0xa0 [nvidia]
Apr 11 13:39:35 localhost kernel:  [pg0+952065922/1068938240] _nv002889rm+0x6a/0xa0 [nvidia]
Apr 11 13:39:35 localhost kernel:  [pg0+952215901/1068938240] _nv001201rm+0x3d/0x618 [nvidia]
Apr 11 13:39:35 localhost kernel:  [pg0+952216387/1068938240] _nv001201rm+0x223/0x618 [nvidia]
Apr 11 13:39:35 localhost kernel:  [pg0+952211959/1068938240] rm_ioctl+0x23/0x38 [nvidia]
Apr 11 13:39:35 localhost kernel:  [do_debug+89/240] do_debug+0x59/0xf0
Apr 11 13:39:35 localhost kernel:  [pg0+954345280/1068938240] nv_kern_ioctl+0x38c/0x3df [nvidia]
Apr 11 13:39:35 localhost kernel:  [do_debug+89/240] do_debug+0x59/0xf0
Apr 11 13:39:35 localhost kernel:  [do_ioctl+111/160] do_ioctl+0x6f/0xa0
Apr 11 13:39:35 localhost kernel:  [do_debug+89/240] do_debug+0x59/0xf0
Apr 11 13:39:35 localhost kernel:  [vfs_ioctl+101/480] vfs_ioctl+0x65/0x1e0
Apr 11 13:39:35 localhost kernel:  [do_debug+89/240] do_debug+0x59/0xf0
Apr 11 13:39:35 localhost kernel:  [sys_ioctl+69/160] sys_ioctl+0x45/0xa0
Apr 11 13:39:35 localhost kernel:  [do_debug+89/240] do_debug+0x59/0xf0
Apr 11 13:39:35 localhost kernel:  [sysenter_past_esp+82/117] sysenter_past_esp+0x52/0x75
Apr 11 13:39:35 localhost kernel:  [do_debug+89/240] do_debug+0x59/0xf0
Apr 11 13:39:35 localhost kernel: Code: c0 00 00 00 ff d0 83 c4 20 85 c0 0f 85 b5 00 00 00 83 c4 f8 8b 03 50 8b 45 10 50 e8 6f 16 f1 ff 89 c1 83 c4 10 85 c9 74 38 89 f6 <8b> b1 b4 00 00 00 8b 55 14 39 11 75 23 83 c4 fc 8b 41 08 8b 51 

```

---

### Post by nocturn on 2005-04-13
[QUOTE=infinito]Hi!

I'm moving from debian sid to hoary, and everything seems to be as great as expected... But there's something very wrong! Using linux-image-k7 (which installs linux-image-2.6.10-5-k7) just freezes xorg server. 

I'm using a Nvidia GeForce 2 MX400, using both drivers "nv" and "nvidia", and get the same result: total freeze of xorg after a few seconds of gnome activity.

Can anybody give an idea to solve this issue??

Of course, my cpu is an AMD Athlon 1400 (K7, you know!)

Thanks in advance![/QUOTE]


Strange, I have the same kernel and a GeForce2 MX card, no problems whatsoever.
What happens if you try the 686 kernel? (it should work fine on a Athlon)?

---

### Post by kuleali on 2005-04-13
I had the same problem with hoary, I then moved back to warty. 
Hopefully the new nvidia driver will solve the problem.

---

### Post by infinito on 2005-04-13
I've solved my problem! It seemed that ubuntu don't like my 512mb ram module positioned the last of the 3 i've got. I'vhe changed it to first ram slot and everything seems perfect (by now...)!

---

