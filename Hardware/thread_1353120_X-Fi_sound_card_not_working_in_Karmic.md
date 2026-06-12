---
title: "X-Fi sound card not working in Karmic?"
date: 2009-12-12
forum: Hardware
---

### Post by shadowdude77 on 2009-12-12
Supposedly X-Fi cards work out of the box (I have an XtremeGamer), but I'm getting nothing. So I went to System --> Preferences --> Multimedia Systems Selector. With default output set to ALSA and device on Front/WaveIn I get an annoying continuous beeeeeeeeeeeeeep noise when I hit test (so I know the sound card is being detected). Output set to ALSA and device set to IEC958 Non-Audio gets me these annoying sporadic clicks. No other options work. Playing audio through Rhythmbox with any option in this manager gives me nothing. I tried compiling the Linux drivers on Creative's site. The README says to simply cd to the directory and as root, run make and make install. Running make gives me this:
```
kevin@kevinlinux:~/Desktop/xfi$ make
make -C /lib/modules/2.6.31-14-generic/build M=/home/kevin/Desktop/xfi
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
CC [M] /home/kevin/Desktop/xfi/xfi.o
/home/kevin/Desktop/xfi/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/kevin/Desktop/xfi/xfi.c: In function ‘ct_card_probe’:
/home/kevin/Desktop/xfi/xfi.c:55: error: implicit declaration of function ‘snd_card_new’
/home/kevin/Desktop/xfi/xfi.c:55: warning: assignment makes pointer from integer without a cast
/home/kevin/Desktop/xfi/xfi.c: At top level:
/home/kevin/Desktop/xfi/xfi.c:118: fatal error: opening dependency file /home/kevin/Desktop/xfi/.xfi.o.d: Permission denied
compilation terminated.
make[2]: *** [/home/kevin/Desktop/xfi/xfi.o] Error 1
make[1]: *** [_module_/home/kevin/Desktop/xfi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2
```

sudo make doesn't do anything better. Just skipping right ahead to make install or sudo make install doesn't do anything. There's no configure file in the folder and the README said nothing about it.

Furthermore, my integrated Realtek sound card works perfectly fine. I installed gnome-alsamixer and ran it and found three tabs: Realtek ALC888 (integrated sound), USB mixer (who knows), and 20K1 (is that my X-Fi? I have no idea). I tried unmuting everything in every tab and dragging the sliders around while playing music and still, the only time I'd get output was from my Realtek card.

In fact, the only indication I have that my X-Fi is plugged in correctly is that it would make that beeping noise when I set the device to Front/WaveIn and that when I run "lsmod | grep x" I get one line that says something like "crtxfi" or something which must be my X-Fi (I'm not on my Linux box right now, so I don't have the exact details, but I know it shows up in lsmod).

I thought Karmic was supposed to work fine with X-Fi cards because of the new ALSA release? Is there something obvious I'm overlooking? Thanks in advance.

---

### Post by s3MA00RRNY on 2009-12-12
I haven't tried it recently, but Linux does not work with ANY X-Fi cards. I've been down this route before with my X-Fi notebook card. It's because Creative is stubborn and won't release their specs.

---

### Post by IcarusR on 2009-12-12
No longer true as stated here...

[http://en.wikipedia.org/wiki/Sound_Blaster_X-Fi#Linux_support]("http://en.wikipedia.org/wiki/Sound_Blaster_X-Fi#Linux_support")

The OP has downloaded & tried to compile craetive drivers for his X-Fi.

---

### Post by shadowdude77 on 2009-12-12
Supposedly though, there is [out-of-the-box support]("http://ubuntuforums.org/showthread.php?t=1211151") for X-Fi in Karmic's kernel.

And I know I've gotten my X-Fi to work with Linux before, so it is possible. I think that might have been Gutsy or Hardy? And it was only with very heavy tweaking.

---

### Post by raygj on 2009-12-14
the "alsa upgrade script" works well for my
X-Fi card.see 

[http://ubuntuforums.org/showpost.php?p=8497610&postcount=2]("http://ubuntuforums.org/showpost.php?p=8497610&postcount=2")

---

