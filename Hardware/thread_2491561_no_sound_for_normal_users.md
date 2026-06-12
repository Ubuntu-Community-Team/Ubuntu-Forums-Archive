---
title: "no sound for normal users"
date: 2023-10-13
forum: Hardware
---

### Post by uwe3 on 2023-10-13
[FONT=courier new]I need some help according the sound system on my notenbook.

# chk OS version[/FONT]
[FONT=courier new]uwe@tux2:~$ lsb_release -a[/FONT]
[FONT=courier new]No LSB modules are available.[/FONT]
[FONT=courier new]Distributor ID:    Ubuntu[/FONT]
[FONT=courier new]Description:    Ubuntu 22.04.3 LTS[/FONT]
[FONT=courier new]Release:    22.04[/FONT]
[FONT=courier new]Codename:    jammy

# within settings 
I can select internal speakers and internal mic only
no sound with test buttons (left/right)

# with aplay I can hear the sound as root
[/FONT][FONT=courier new]uwe@tux2:~$ sudo aplay /usr/share/sounds/alsa/Noise.wav[/FONT]
[FONT=courier new]Wiedergabe: WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono

[/FONT]
[FONT=courier new]# no sound as normal user
uwe@tux2:~$ aplay /usr/share/sounds/alsa/Noise.wav[/FONT]
[FONT=courier new]Wiedergabe: WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono[/FONT]
[FONT=courier new]
# checked my permission in /etc/group
[/FONT][FONT=courier new]audio:x:29:uwe,pulse

# checked /dev
[/FONT][FONT=courier new]uwe@tux2:~$ ls -la /dev/ | grep snd[/FONT]
[FONT=courier new]drwxr-xr-x   3 root audio            280 Okt  6 09:47 snd

# tried to beep 
[/FONT]uwe@tux2:~$ beep
beep: Error: Could not open any device
[FONT=courier new]
Every hint is wellcome!

Uwe[/FONT]
[FONT=courier new]
[/FONT]

[FONT=courier new]
[/FONT]
[FONT=courier new]

[/FONT]
[FONT=courier new]



[/FONT]

---

