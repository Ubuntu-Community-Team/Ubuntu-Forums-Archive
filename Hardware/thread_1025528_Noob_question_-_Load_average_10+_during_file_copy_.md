---
title: "Noob question - Load average 10+ during file copy? why?"
date: 2008-12-30
forum: Hardware
---

### Post by luckyluke699 on 2008-12-30
Hello,

I think this might be my first post? so I'm sorry if I am not in the right forum?:D

Anyway I've been fumbling my way through Ubuntu for close to a year now, but only really recently starting to really get into it. I wanted to seperate my 'data' from my O/S, as being a bit of a clot I still manage to break my box from time to time while learning/playing with Ubuntu!

I had a 1 terrabyte hard drive, and 2x500 gig hard drives to play with, so decided to partition them and set them up as follows...

    Main 1TB hdd     - SDA1 - O/S partition         232 gig
                     - SDA2 - Extended SWAP         9.3 gig
                     - SDA3 - 'DATA' partition      689 gig

    RAIDED 2x500 gig - MD0  - RAID partition consisting of SDB1 & SDC1

I don't know if this is the best way to do it (or if the sizes seem a bit excessive etc) but I figured it would give me some unraided space to play with, and then also some raided space for my really important data I didn't want to lose no matter what? The RAID drive was set up using MDADM with the command sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sd[bc]1

Anyway (I'm rambling again :P), I was copying some data (about 400 gig) from my SDA3 data partition, to my MD0 radided drives, when I noticed something...

I started a firefox session and it was extemely unresponsive (kept going grey every so often etc). The system monitor applet loaded in my panel showed my cpu was basically idle, my ram was barely utilised, and even the disks were under '50%' utilised, yet my load average was over 10 and the machine was not as responsive as it usually is (as you'd expect from such a load average)?

I ran a 'top' command which confirmed that my CPU was 67% waiting for I/O to complete.


Now here comes my (probably very noobish) question - 

If my hard drives, cpu or ram etc aren't causing my system to be slow, then what is? Is this slowdown the I/O controllers or fsb or something on the motherboard and how in more depth can I tell what was causing this (though I know I won't be copying that amount of data in one go every day ;P)??


My spec is as follows (I think it should be quite a capable machine)...
cpu:   Intel Quad Q9550 @ 2.83 ghz
ram:   8gb DDR2 800 mhz
mobo:  Gigabyte GA-EP35-DS3L
gfx:   Asus 8600 GT 


In case it helps, I've copied a 'top' below from during the copy/

top - 11:26:58 up 13:27,  2 users,  load average: 10.08, 9.04, 7.75
Tasks: 164 total,   1 running, 163 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.1%us, 10.7%sy,  0.0%ni, 16.7%id, 67.7%wa,  0.1%hi,  0.7%si,  0.0%st
Mem:   8183088k total,  8137532k used,    45556k free,    36524k buffers
Swap:  9767480k total,     5416k used,  9762064k free,  6933008k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                  
 6859 luke      20   0  635m 273m  17m S   29  3.4  26:07.04 nautilus                 
19300 root      15  -5     0    0    0 D    7  0.0   2:08.45 kjournald                
 6414 root      20   0  441m  65m  15m S    7  0.8   8:59.76 Xorg                     
  224 root      15  -5     0    0    0 S    4  0.0   2:51.25 



thanks in advance :D

---

### Post by luckyluke699 on 2008-12-30
I got bored and decided to start another copy, but this time command line based using cp command....

for a reason I can't explain, the load average was halved, and the wa% reduced from 67.7% down to 12.9%.... 


top - 17:56:34 up 39 min,  3 users,  load average: 4.57, 4.46, 3.28
Tasks: 158 total,   4 running, 154 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.7%us,  8.0%sy,  0.0%ni, 77.5%id, 12.9%wa,  0.1%hi,  0.8%si,  0.0%st
Mem:   8183088k total,  8136076k used,    47012k free,    15324k buffers
Swap:  9767480k total,     5408k used,  9762072k free,  7387760k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                          
 8405 root      20   0 13604 1020  796 R   18  0.0   2:49.09 cp                                                                               
 4718 root      15  -5     0    0    0 D    5  0.0   0:51.47 kjournald                                                                        
 4180 root      15  -5     0    0    0 D    4  0.0   0:58.00 md0_resync                                                                       
 8554 root      20   0     0    0    0 D    3  0.0   0:07.94 pdflush                                                                          
  224 root      15  -5     0    0    0 R    3  0.0   0:20.38 kswapd0                                                                          
 4179 root      15  -5     0    0    0 S    3  0.0   0:44.45 md0_raid1  



Can anyone help me out :confused:?

thanks....

---

