---
title: "[SOLVED] Leadtek WinFast TV 2000 ... strange problem"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by unimatrix on 2007-02-03
Hi

I have a Leadtek WinFast TV 2000 card that has a bit of a problem on my Ubuntu 6.10 (Edgy Eft) 64-bit version. It does though work under Windows platforms, so I can be sure it's not a hardware malfunction. The problem is that the software can only find max 3 channels, in really low quality, without any sound. I have tried this with every TV-tuner application possible, but it was mostly always same.

I suspect there might be a problem with the drivers. Here is my "lsmod |grep tv" output:
> 
bttv                  222196  2 bt878
video_buf              33156  1 bttv
ir_common              31876  1 bttv
compat_ioctl32         11264  1 bttv
i2c_algo_bit           11784  1 bttv
v4l2_common            20352  3 tuner,bttv,compat_ioctl32
btcx_risc               7304  1 bttv
tveeprom               20112  1 bttv
videodev               14208  2 bttv
i2c_core               29312  13 i2c_ec,w83627hf,eeprom,i2c_isa,nvidia,tuner,tda9887,bttv,i2c_algo_bit,tveeprom,i2c_ali1535,i2c_ali15x3,i2c_ali1563


AFAIK, this TV-tuner should work. So what's the problem? If anyone has any ideas, then please let me know! Thanks!

---

### Post by unimatrix on 2007-05-01
OK, Problem solved (partially)
Thanks to [Erlander]("http://ubuntuforums.org/member.php?u=209027") I was pointed to this thread:
[http://ubuntuforums.org/showthread.php?p=923127](http://ubuntuforums.org/showthread.php?p=923127)
Containing this website:
[http://www2.truman.edu/~dat725/htpc2.html](http://www2.truman.edu/~dat725/htpc2.html)

I still can't get my sound working.
I've tried multiple configurations, the soundcard is connected with the TV-tuner, every slider in mixer is up to the max, but I still don't get any sound.

---

