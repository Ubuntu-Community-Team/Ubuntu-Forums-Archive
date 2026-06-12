---
title: "Another Mplayer Problem"
date: 2004-12-29
forum: General Help
---

### Post by jozmak on 2004-12-29
I have just compiled and installed mplayer from source with  gui enabled. All  went smoothly. Mplayer works fine from the command line but i cannot use it with graphical interface. When i try, i get the following massage. 


root@ubuntu:/mnt/hardDrive # gmplayer 041205bugar.wmv
MPlayer 1.0pre6-3.3.4 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Athlon Thunderbird (Family: 6, Stepping: 2)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx
vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)

And nothing happens.
Skin and fonts are also installed.

Any help would be appreciated.

jozsefmak

---

### Post by emperor on 2004-12-29
Did you configure mplayer prior to the make step with the gui enabled?
 
 $ tar -xjf MPlayer-1.0pre5.tar.bz2
       $ cd MPlayer-1.0pre5
       $ ./configure --enable-gui
       $ make
       $ sudo make install

---

### Post by jozmak on 2004-12-29
I did configure. But yesterday i uninstalled the 1.0pre6 and reinstalled the previous version of Mplayer, 1.0pre5 following the exact  insturctions on  ubuntu FAQ page;  this time I got the following error.

root@ubuntu:/home/mak # gmplayer
MPlayer 1.0pre5-3.3.4 (C) 2000-2004 MPlayer Team

CPU: Advanced Micro Devices Athlon Thunderbird 897.2 MHz (Family: 6, Stepping: 2)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx

Reading config file /usr/local/etc/mplayer/mplayer.conf: No such file or directory
Reading config file /root/.mplayer/config
[cfg] read config file: /root/.mplayer/gui.conf
Reading config file /root/.mplayer/gui.conf: No such file or directory
vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
Reading /root/.mplayer/codecs.conf: Can't open '/root/.mplayer/codecs.conf': No such file or directory
Reading /usr/local/etc/mplayer/codecs.conf: 73 audio & 180 video codecs
font: can't open file: /root/.mplayer/font/font.desc
Font /usr/local/share/mplayer/font/font.desc loaded successfully! (233 chars)
Using Linux hardware RTC timing (1024Hz).
Can't open input config file /root/.mplayer/input.conf: No such file or directory
Input config file /usr/local/etc/mplayer/input.conf parsed: 53 binds
SKIN dir 1: '/root/.mplayer/Skin'
SKIN dir 2: '/usr/local/share/mplayer/Skin'

Any idea?

jozmak

---

### Post by emperor on 2004-12-30
I am not running as root and do not have the RTC setup.
 
 Here's what gmp[ayer prints on the console on my system:
 ====================================
 MPlayer 1.0pre5-3.3.4 (C) 2000-2004 MPlayer Team
 
 CPU: Advanced Micro Devices Athlon 4 /Athlon MP/XP Palomino 1467 MHz (Family: 6, Stepping: 2)
 Detected cache-line size is 64 bytes
 CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
 Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE
 
 Reading config file /usr/local/etc/mplayer/mplayer.conf: No such file or directory
 Reading config file /home/lee/.mplayer/config
 [cfg] read config file: /home/lee/.mplayer/gui.conf
 Reading config file /home/lee/.mplayer/gui.conf
 vo: X11 running at 1152x864 with depth 24 and 32 bpp (":0.0" => local display)
 Reading /home/lee/.mplayer/codecs.conf: Can't open '/home/lee/.mplayer/codecs.conf': No such file or directory
 Reading /usr/local/etc/mplayer/codecs.conf: Can't open '/usr/local/etc/mplayer/codecs.conf': No such file or directory
 Using built-in default codecs.conf.
 Font /usr/local/share/mplayer/font/font.desc loaded successfully! (206 chars)
 Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
 Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
 Using usleep() timing
 Can't open input config file /home/lee/.mplayer/input.conf: No such file or directory
 Input config file /usr/local/etc/mplayer/input.conf parsed: 53 binds
 SKIN dir 1: '/home/lee/.mplayer/Skin'
 SKIN dir 2: '/usr/local/share/mplayer/Skin'
 Font /usr/local/share/mplayer/font/font.desc loaded successfully! (206 chars)

---

