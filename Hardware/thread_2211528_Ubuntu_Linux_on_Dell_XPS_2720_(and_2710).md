---
title: "Ubuntu Linux on Dell XPS 2720 (and 2710)"
date: 2014-03-16
forum: Hardware
---

### Post by youri2 on 2014-03-16
[COLOR=#000000][FONT=Arial]Hi,[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I just wanted to share my experience on using Ubuntu on a Dell XPS 2720. The 2720 is a All-in-one computer (everything in the screen, one cable to plug) similar to an iMac. I also owned a Dell XPS 2710 before having this one so some tips might apply too.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The full specifications for this machine can be found on Dell&#8217;s website: [/FONT][/COLOR][COLOR=#1155CC]_[www.dell.com/fr/p/xps-27-2720-aio/pd]("http://www.dell.com/fr/p/xps-27-2720-aio/pd")_[/COLOR]

[COLOR=#000000][FONT=Arial]_**Installation**_:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]This machine comes with a SSD mSata disk (32gb) and a 2TB mechanical disk. The SSD is meant to be used as a cache with Intel SRT. It seems hard to get this thing to work with a dual boot so I simply disabled it and installed Linux on the SSD. I only boot on Windows for games so it is fine for me.[/FONT][/COLOR][INDENT]
[/INDENT]
[COLOR=#000000][FONT=Arial]To disable Intel SRT, boot on Windows and use Intel&#8217;s application to disable the SSD as cache. Then in the BIOS, disable it there too and use AHCI mode instead of RAID mode for SATA devices (not sure that I needed to do that actually). I think I also disabled UEFI boot to use legacy.[/FONT][/COLOR][INDENT]
[/INDENT]
[COLOR=#000000][FONT=Arial]Then I used a standard Live-USB installation of XUbuntu. But I experienced a kernel panic similar to [/FONT][/COLOR][COLOR=#1155CC]_[https://bugs.launchpad.net/ubuntu/+source/linux-ec2/+bug/614853](https://bugs.launchpad.net/ubuntu/+source/linux-ec2/+bug/614853)_[/COLOR][COLOR=#000000][FONT=Arial] (SMP divide error with a stacktrace related to nouveau). To be able to boot the live USB I had to change the boot line to add nomodeset option as explained here [/FONT][/COLOR][COLOR=#1155CC]_[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)_[/COLOR][COLOR=#000000][FONT=Arial].[/FONT][/COLOR][INDENT]
[/INDENT]
[COLOR=#000000][FONT=Arial]I then installed Ubuntu on the SSD as / partition, also created a small swap partition on the SSD (we never know 16gb might not be enough&#8230;). [/FONT][/COLOR][INDENT]
[/INDENT]
[COLOR=#000000][FONT=Arial]The bootloader was installed on the SSD disk directly to avoid messing with Windows bootloader. It means that I&#8217;m using the BIOS boot devices menu to choose between Windows or Linux which is ok for me because I rarely use Windows. On the previous machine, I installed Grub on the UEFI partition, it worked but sometimes Windows updates broke Grub and I had to reinstall it manually.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]**_Configuration_**:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]_Graphics_:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]This machine has an Intel GPU and a nVidia GPU. For Intel I installed the latest drivers from [/FONT][/COLOR][COLOR=#1155CC]_[https://01.org/linuxgraphics/](https://01.org/linuxgraphics/)_[/COLOR][COLOR=#000000][FONT=Arial] which allowed me to use the native resolution of the screen (QHD).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]For nVidia, I used x-swat PPA to get the latest drivers from nVidia and bumblebee/optirun. [/FONT][/COLOR][INDENT]
[/INDENT]
[COLOR=#000000][FONT=Arial]Both GPUs seems to work OK, I&#8217;m always using the Intel&#8217;s one.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]To access the nVidia settings use : 
```
optirun -b none nvidia-settings -c :8 [/[/FONT][/COLOR][COLOR=#000000][FONT=Arial]CODE[/FONT][/COLOR][COLOR=#000000][FONT=Arial]]
(magic command I had a hard time to find).[/FONT][/COLOR][INDENT]
[/INDENT]
[COLOR=#000000][FONT=Arial]By the way there is no OSD for brightness adjustment on the display, it seems to be known by Dell and happens even on Windows. But the display buttons still work.[/FONT][/COLOR][INDENT]
[/INDENT]
[COLOR=#000000][FONT=Arial]The touch screen works by the way but seriously, touch touch a 27&#8221; display? The greasy marks you leave on the glass panel are just so niiiice&#8230; It is just not usable, you don&#8217;t want to use your computer with your arms in the air&#8230; (Note that I originally bought the 2710 without a touch display, see below).[/FONT][/COLOR][INDENT]
[/INDENT]
[COLOR=#000000][FONT=Arial]_Keyboard_:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Works out of the box.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]An issue I had was that when I was typing alt_gr+pipe and then space, the character inserted for space was not space but another whitespace weird character. It happened because I was actually typing alt_gr+space that happens a lot when you type fast. This also probably will happen to French user only because of the Azerty layout. To solve it I used xmodmap to rebind the space key : [/FONT][/COLOR][CODE][COLOR=#000000][FONT=Arial]keycode 65 = space space space space space space space space[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]Even If a modifier is pressed, space will only produce space.[/FONT][/COLOR][INDENT]
[/INDENT]
[COLOR=#000000][FONT=Arial]I also wanted to the square key (located above tab key on my keyboard) to popup the terminal (ala quake) but it messes up XFCE keyboard settings so I had to remap this key using xmodmap again:[/FONT][/COLOR]```
[COLOR=#000000][FONT=Arial]keycode 49 = XF86LaunchA[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]And then I configured XF86LaunchA to run xfce4-terminal --drop-down[/FONT][/COLOR][INDENT]

[/INDENT]
[COLOR=#000000][FONT=Arial]_Mouse_:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Works out of the box.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The mouse with the 2720 looks like it is a five button mouse but it is not, the side buttons are for Windows actions. You have to press one of them and move the mouse to produce a specific action. On Linux for instance I can type a &#8216;c&#8217; with a left drag&#8230;. Well they are pretty much useless (xev does not show anything when I press the button). [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The wheel button (button 3) can go left or right so I used for backward/forward which is handy when browsing. I used imwheel to do that : [/FONT][/COLOR][COLOR=#1155CC]_[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)_[/COLOR][INDENT]

[/INDENT]
[COLOR=#000000][FONT=Arial]_Network_:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Wifi/Cable works out of the box.[/FONT][/COLOR][INDENT]

[/INDENT]
[COLOR=#000000][FONT=Arial]_Sound_:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Works out of the box. The keyboard media keys for sound level work too.[/FONT][/COLOR][INDENT]

[/INDENT]
[COLOR=#000000][FONT=Arial]_Webcam_:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Works out of the box.[/FONT][/COLOR][INDENT]

[/INDENT]
[COLOR=#000000][FONT=Arial]_Bluetooth_:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I had to install pulseaudio-module-bluetooth to connect my Philips SHB9001 headset. It refuses to the audio sink, my workaround is:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]to kill pulseaudio, let it restart (pulseaudio -k)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]and then to connect the headset to the audio sink and choose AD2P profile[/FONT][/COLOR][INDENT]
[/INDENT]
[COLOR=#000000][FONT=Arial]_Fans/Sensors_:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]lm-sensors / fancontrol detected several sensors (mostly CPU I think, not sure) and managed to control 2 fans (CPU and GPU I think). But in the end I left the job to the BIOS (did not want to fiddle with fancontrol settings to find proper steps).[/FONT][/COLOR]

**_[COLOR=#000000][FONT=Arial]XFCE specific:[/FONT][/COLOR]_**

[COLOR=#000000][FONT=Arial]I&#8217;m using XUbuntu that is Ubuntu with XFCE desktop environment. One issue I had related to XFCE:[/FONT][/COLOR][INDENT]
[/INDENT]
[COLOR=#000000][FONT=Arial]Dashed borders on Windows, see :  [/FONT][/COLOR][COLOR=#1155CC]_[http://askubuntu.com/questions/312986/dashed-borders-of-my-window-manager-xfce](http://askubuntu.com/questions/312986/dashed-borders-of-my-window-manager-xfce)_[/COLOR]
[COLOR=#000000][FONT=Arial]Then I had to disable Chrome native Flash plugin.[/FONT][/COLOR]


**_[COLOR=#000000][FONT=Arial]Things that do not work very well:[/FONT][/COLOR]_**

[COLOR=#000000][FONT=Arial]When it starts my keyboard does not have numlock on (I don&#8217;t understand why) and even if I use numlockx in XFCE autostart items it does not work. I still don&#8217;t understand what is going on.[/FONT][/COLOR][INDENT]
[/INDENT]
[COLOR=#000000][FONT=Arial]Bluetooth, very fragile, very easy to crash pulseaudio.[/FONT][/COLOR]


_**[COLOR=#000000][FONT=Arial]Some personal notes about the machine itself:[/FONT][/COLOR]**_

[COLOR=#000000][FONT=Arial]Originally I owned a Dell XPS 2710 that was ok but sometimes the screen was just not turning on on cold start (meaning the first boot of the day). I lived with that for almost a year but eventually it became more frequent and the warranty was expiring so I contacted Dell. The other issue was I had a few dead pixels. I sent the machine for repair, they replaced the motherboard and the hard drive, the boot issue was fixed. But the dead pixels were not, I sent it back a second time and they replaced the LCD panel. There were still a few dead pixels and some dust behind the glass panel. It was already almost two months of daily emails between me and Dell (they always leave 24hrs between emails so it not fast to get something fixed&#8230;). I complained again and they offered to send me a new machine. I agreed, especially since i was getting the new model with better specifications. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The XPS 2720 comes with a unusable (by design) touch functionality. It also take more space on the desktop (the stand is bigger, deeper). I noticed that the fans were also noisier than the XPS 2710. The display is also not properly aligned (a bit off), the screen&#8217;s arm allows move the screen a bit (up/down) but the maximum height is still the same so for me I won nothing. The stand seems just more fragile and the vibrations produced when I type on the keyboard make the screen vibrate a bit too.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]But the worst is now the display, the colours are just off, the white and black seems a bit too yellow. I had both 2710 and 2720 side by side for a few days and you could see the difference right away. I tried to play with gamma, brightness, warmth and did not find a proper setting. I don&#8217;t know if it comes from the touch thing, I&#8217;m still trying to get some info from Dell. See for yourself here [/FONT][/COLOR][https://drive.google.com/folderview?id=0B2huEiIuWDmFTUJ1eGZ0LXpQcUU&usp=sharing](https://drive.google.com/folderview?id=0B2huEiIuWDmFTUJ1eGZ0LXpQcUU&usp=sharing) .
[COLOR=#000000][FONT=Arial]And by the way the glass panel looks nice, colors used to be sharp and nice (was a lot better on the 2710). But it is just too much reflection, watching movies is not very nice during the day or with a light on. For browsing/coding it is ok.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The mouse is worst too. It is a 2000&#8364; machine and you get a cheap plastic mouse. The keyboard is ok.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I&#8217;m really disappointed because I love the concept of All-in-one, I did not want a Mac because I prefer to use Linux. This machine looked great because of the hardware (quad core, SSD, large amount of RAM, GPU usable to play). It is just a shame that for this amount of money you don&#8217;t get proper quality... I'm just very sad because Dell seems to have interesting products like Ultrasharp screens or the Ubuntu laptop but this bad experience means that I will just not buy from Dell anymore...

My rant is finished :). I hope that the technical details will be useful for other users. Do not hesitate to ask question.

Youri[/FONT][/COLOR]

---

### Post by mapk on 2014-08-08
Hey any chance you can explain exactly how you got the video working at high res?  

I have a XPS 2720, nVidia 750M, Intel integrated graphics. I installed the Linux Graphics drivers but the best I can get for resolution is 1024x768 ! Ouch. 

Chipset is "Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)"

I don't care about using the nVidia GPU, so I left the default nouveau drivers installed and blacklisted the kernel module in the /etc/modprobe.d/blacklist.conf file

Any idea how to get the high res going on the Intel integrated video?

---

### Post by youri2 on 2014-08-08
[FONT=courier new]I used the drivers from Intel: [/FONT]https://01.org/linuxgraphics/
[FONT=courier new]But it seems that even with nouveau driver the QUADHD resolution was working.

~$ dpkg -l | grep intel[/FONT]
[FONT=courier new]ii  intel-gpu-tools                                             1.5-0intel2                                         amd64        tools for debugging the Intel graphics driver[/FONT]
[FONT=courier new]ii  intel-linux-graphics-installer                              1.0.4-0intel1                                       amd64        Intel graphics drivers update utility[/FONT]
[FONT=courier new]ii  libdrm-intel1:amd64                                         2.4.53+git20140420.d4083dc7-0ubuntu0ricotz~saucy    amd64        Userspace interface to intel-specific kernel DRM services -- runtime[/FONT]
[FONT=courier new]ii  libdrm-intel1:i386                                          2.4.53+git20140420.d4083dc7-0ubuntu0ricotz~saucy    i386         Userspace interface to intel-specific kernel DRM services -- runtime[/FONT]
[FONT=courier new]ii  xserver-xorg-video-intel                                    2:2.99.910-0ubuntu1                                 amd64        X.Org X server -- Intel i8xx, i9xx display driver


[/FONT][FONT=courier new]~$ lsmod | grep video[/FONT]
[FONT=courier new]uvcvideo               80885  0 [/FONT]
[FONT=courier new]videobuf2_vmalloc      13216  1 uvcvideo[/FONT]
[FONT=courier new]videobuf2_memops       13362  1 videobuf2_vmalloc[/FONT]
[FONT=courier new]videobuf2_core         40664  1 uvcvideo[/FONT]
[FONT=courier new]videodev              134688  2 uvcvideo,videobuf2_core[/FONT]
[FONT=courier new]video                  19476  1 i915[/FONT]
[FONT=courier new]
[/FONT]

---

### Post by mapk on 2014-08-08
I'm trying to get Kubuntu 14.04 installed. 

I went through many different configs trying to get the video working beyond 1024.x768. Finally decide to stick with stock drivers. So I reintalled the OS, the installed Linux Graphics drivers, and at some point it occurred to me that maybe it was "nomodeset" in grub might be the problem because based on the xorg.0.log it can't find a mode higher than 1024x768. 

So I added a new grub entry without nomodeset and rebooted and it worked. Then I was installing software, messed up my MySQL install stuff and decided to simply reinstall the entire OS since I was just getting started anyway.  From that point one I can't get the high res video working again. I don't remember how I got it working initially other than me removing nomodeset from grub, but it still won't fire up in high res. 

Right now I still have nomodeset in the grub because without it I get the boot splash, then a blank screen during boot and it won't get past that to the login screen. The boot sequence freezes up. 

Here's my info comparible to yours - with only the Linux Graphics drivers installed and nouveau, and this is a 32-bit install. Any ideas why it's not working? 

```

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)

```


```

lsmod | grep video
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
videodev              108503  2 uvcvideo,videobuf2_core
video                  18903  2 i915,nouveau
```
```


dpkg -l | grep intel
ii  intel-gpu-tools                            1.7-1                                  i386         tools for debugging the Intel graphics driver
ii  intel-linux-graphics-installer             1.0.6-0intel1                          i386         Intel graphics drivers update utility
ii  libdrm-intel1:i386                         2.4.54-1                               i386         Userspace interface to intel-specific kernel DRM services -- runtime
ii  libegl1-mesa:i386                          10.2.2-0intel1                         i386         free implementation of the EGL API -- runtime
ii  libegl1-mesa-drivers:i386                  10.2.2-0intel1                         i386         free implementation of the EGL API -- hardware drivers
ii  libgbm1:i386                               10.2.2-0intel1                         i386         generic buffer management API -- runtime
ii  libgl1-mesa-dri:i386                       10.2.2-0intel1                         i386         free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:i386                       10.2.2-0intel1                         i386         free implementation of the OpenGL API -- GLX runtime
ii  libglapi-mesa:i386                         10.2.2-0intel1                         i386         free implementation of the GL API -- shared library
ii  libgles1-mesa:i386                         10.2.2-0intel1                         i386         free implementation of the OpenGL|ES 1.x API -- runtime
ii  libgles2-mesa:i386                         10.2.2-0intel1                         i386         free implementation of the OpenGL|ES 2.x API -- runtime
ii  libopenvg1-mesa:i386                       10.2.2-0intel1                         i386         free implementation of the OpenVG API -- runtime
ii  libosmesa6:i386                            10.2.2-0intel1                         i386         Mesa Off-screen rendering extension
ii  libva-intel-vaapi-driver                   1.3.0-1ubuntu1                         all          VAAPI driver for Intel G45 & HD Graphics family (transitional package)
ii  libwayland-egl1-mesa:i386                  10.2.2-0intel1                         i386         implementation of the Wayland EGL platform -- runtime
ii  libxatracker2:i386                         10.2.2-0intel1                         i386         X acceleration library -- runtime
ii  xserver-xorg-video-intel                   2:2.99.911-0intel1                     i386         X.Org X server -- Intel i8xx, i9xx display driver


```

---

### Post by mapk on 2014-08-08
I've narrow this down to a bug in nouveau, and I reported it to the devs. 

If I keep rebooting every time is freezes then eventually the system will boot and I do get the high res mode.  So it does seem to be a bug in xserver-xorg-video-nouveau 1:1.0.10-1ubuntu2 that causes intermittent freezes. 

Hopefully they track this down and fix it soon

---

### Post by youri2 on 2014-08-09
It is true I might had to play with grub settings at some point, but not anymore.
Weird that you have a 32bits install for a machine with 8 to 16 GB of memory :)

So for me it probably works as I'm not using nouveau at all.

---

