---
title: "Installation troubles on Picobook Pro"
date: 2010-12-12
forum: Hardware
---

### Post by spoirier on 2010-12-12
Hello. I have a Picobook Pro, whose specifications can be seen at
[http://www.apricotcomputers.com/picobook_pro_spec.htm](http://www.apricotcomputers.com/picobook_pro_spec.htm)
with Suze Linux Professional preinstalled (the seller could not tell me the root password so I cannot do much with it), which seemed to work (including wifi).

I just tried to run on it (by usb, without installing) the last Ubuntu Netbook (10.10).
However several things failed:

[LIST]
[*]The video mode does not work but makes a scrambled display, so I managed to get a correct display only on an external screen. Then I went into the screen options, I tried to select the correct resolution, with both available frequencies, but none of them made a stable image.
[*]I could not get wifi (blank list of wifi networks)
[*]The sound does not work (I guess it can play sound, as the test made one, but it cannot receive it from mic)
[/LIST]
Is there any solution I can try with this Linux distribution, or should I try another Ubuntu, or another Linux distribution instead ? How can I know which distribution can work on this laptop ? Thank you very much.

---

### Post by Fafler on 2010-12-12
Are you sure Suse doesn't implement sudo the same way as Ubuntu? In that case, you can just sudo passwd root and set a new root password using you own user password. Or just use sudo for all your superuser needs.

Anyway, as for Ubuntu, copy your Xorg.conf from Suse and take the relevant parts and reuse them.

---

### Post by spoirier on 2010-12-12
Finally wifi works (maybe I did not check at the right place last time). In the Suse installation (where sudo does not help as it asks for password first), I found two files with that name: 
/etc/X11/xorg.conf 
/var/lib/sax/xorg.conf. 
Their contents have much in common but a few differences.
In Ubuntu working on the USB key, there is no file of that name in such folders. 
I copied the /etc/X11 one (there is no /sax/ there)
But it did not have any effect at the next reboot (or maybe to change the screen resolution in the intermediate step of choice of language and decision to install or run on usb, but it was still scrambled anyway).
And then I noticed that the new file was no more there (that must be because it only runs on usb).
Is it possible to try something without doing the installation ? Or can I trust that I can just do the installation, losing all what is in the suse one ? Thanks.

---

### Post by Fafler on 2010-12-12
This is from the top of my head.

Press ctrl+alt+f1. Login and

```
sudo /etc/init.d/gdm stop
cp /path/to/file/Xorg.conf /etc/X11/
sudo /etc/init.d/gdm start
```

Configuration files aren't saved between reboots when you use live systems.

On Suse, have you tried changing the password for your user with passwd? Or you could mount the root partition from Ubuntu and reset the root password by editing /etc/shadow. Remove the password hash and the password is cleared.

---

### Post by spoirier on 2010-12-12
After a lot of tries I finally managed to change the suse root password by the following method:
1) From ubuntu, delete the x of "mx" user from the etc/passwd file (I also deleted the hash from shadow but I guess it was unnecessary)
2) From suse, change user password
3) From ubuntu, restore the x in etc/passwd file, and copy the hash in etc/shadow from "mx" user to "root"
but then in suse I can't install programs because it asks for cd. 

Another thing is, when loading ubuntu netbook, there is an error message: "No required driver detected for Unity".
(I did not try yet your method to make use of xorg.conf)
I will continue tomorrow (check if there is any other way to install programs in suse...)

---

### Post by spoirier on 2010-12-15
Hello. Now back to trying, I just tried what you said: 
ctrl+alt+f1.
(no need to log in)

sudo /etc/init.d/gdm stop
cp /path/to/file/Xorg.conf /etc/X11/
sudo /etc/init.d/gdm start

But it made first a strange error message at the stop line, suggesting other ways to do this stop. I followed a suggestion but it seemed the stop was already done anyway.
The file I had copied before ctrl+alt+f1. was still there, no need to copy it again.
Finally, the start command seemed to block the computer: black screen with blinking cursor on the corner, for at least a minute. There seemed no way to do anything by any ctrl-alt-F... Then I shut down the laptop (it said then a process could not be stopped and had to be killed)..

---

### Post by Fafler on 2010-12-16
Sorry about the /etc/init.d/ thing. It was the way it used work until a few releases ago.

Does it boot now?

It would be quite interesting to know what happened. Take a look at your /var/log/Xorg.0.log and post anything you find relevant. Lines marked with (WW) are warnings and (EE) are errors.

---

### Post by spoirier on 2010-12-21
Now back to my laptop. No problem for restarting. Then I find the /var/log/Xorg.0.log 
It is very, very big, and I have no clue what to do with it. Here are excepts. If you like to have it full you can let me your email and can send you the files there.

[   537.540] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.

[   537.564] (II) VESA: driver for VESA chipsets: vesa
[   537.564] (II) FBDEV: driver for framebuffer: fbdev
[   537.564] (--) using VT number 8

[   537.581] (!!) VIA Technologies does not support this driver in any way.
[   537.581] (!!) For support, please refer to [http://www.openchrome.org/](http://www.openchrome.org/).
[   537.581] (!!) (development build, compiled on Tue 10 Aug 2010 10:07:16 EST)
[   537.581] (WW) Falling back to old probe method for vesa
[   537.581] (WW) Falling back to old probe method for fbdev

[   537.590] (EE) CHROME(0): Unknown Card-Ids (1122|1509|3002), Chipset: VX800/VX820; please report to openchrome-users at openchrome.org

[   537.707] (II) CHROME(0): <default monitor>: Using hsync range of 31.47-79.98 kHz
[   537.707] (II) CHROME(0): <default monitor>: Using vrefresh range of 56.25-75.03 Hz
[   537.707] (II) CHROME(0): Estimated virtual size for aspect ratio 1.2593 is 1280x1024
[   537.708] (II) CHROME(0): Clock range:  20.00 to 230.00 MHz
[   537.708] (II) CHROME(0): ViaValidMode: Validating 640x350 (Clock: 31500)
[   537.708] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.708] (II) CHROME(0): Not using default mode "640x350" (vrefresh out of range)
[   537.708] (II) CHROME(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[   537.708] (II) CHROME(0): ViaValidMode: Validating 640x400 (Clock: 31500)
[   537.708] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.708] (II) CHROME(0): Not using default mode "640x400" (vrefresh out of range)
[   537.708] (II) CHROME(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[   537.708] (II) CHROME(0): ViaValidMode: Validating 720x400 (Clock: 35500)
[   537.708] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.708] (II) CHROME(0): Not using default mode "720x400" (vrefresh out of range)
[   537.708] (II) CHROME(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
[   537.708] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 25175)
[   537.708] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.708] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   537.708] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
[   537.708] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.708] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   537.708] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
[   537.708] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.708] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   537.709] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 36000)
[   537.709] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.709] (II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
[   537.709] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   537.709] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 36000)
[   537.709] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.709] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   537.709] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 40000)
[   537.709] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.709] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   537.709] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 50000)
[   537.709] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.709] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   537.709] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 49500)
[   537.709] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.709] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   537.709] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 56300)
[   537.709] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.709] (II) CHROME(0): Not using default mode "800x600" (vrefresh out of range)
[   537.709] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   537.709] (II) CHROME(0): ViaValidMode: Validating 1024x768i (Clock: 44900)
[   537.709] (II) CHROME(0): Not using default mode "1024x768i" (interlace mode not supported)
[   537.709] (II) CHROME(0): Not using default mode "512x384i" (bad mode clock/interlace/doublescan)
[   537.709] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 65000)
[   537.709] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.709] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   537.709] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 75000)
[   537.709] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.709] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   537.709] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 78750)
[   537.709] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.710] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   537.710] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 94500)
[   537.710] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.710] (II) CHROME(0): Not using default mode "1024x768" (vrefresh out of range)
[   537.710] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   537.710] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 108000)
[   537.710] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.710] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   537.710] (II) CHROME(0): ViaValidMode: Validating 1280x960 (Clock: 108000)
[   537.710] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.710] (II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[   537.710] (II) CHROME(0): ViaValidMode: Validating 1280x960 (Clock: 148500)
[   537.710] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.710] (II) CHROME(0): Not using default mode "1280x960" (hsync out of range)
[   537.710] (II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[   537.710] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 108000)
[   537.710] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.710] (II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   537.710] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 135000)
[   537.710] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.710] (II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   537.710] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 157500)
[   537.710] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.710] (II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
[   537.710] (II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   537.710] (II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
[   537.710] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   537.710] (II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
[   537.710] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   537.710] (II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
...same with many other sizes...
[   537.711] (II) CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
[   537.711] (II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   537.711] (II) CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
[   537.711] (II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   537.711] (II) CHROME(0): ViaValidMode: Validating 832x624 (Clock: 57284)
[   537.711] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.711] (II) CHROME(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
[   537.711] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 81620)
[   537.711] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.711] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   537.711] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 96770)
[   537.711] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.711] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   537.711] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 104990)
[   537.711] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.712] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   537.712] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 119650)
[   537.712] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.712] (II) CHROME(0): Not using default mode "1152x864" (vrefresh out of range)
[   537.712] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   537.712] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 121500)
[   537.712] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.712] (II) CHROME(0): Not using default mode "1152x864" (vrefresh out of range)
[   537.712] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   537.712] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 143470)
[   537.712] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.713] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   537.713] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   537.713] (II) CHROME(0): Not using default mode "1360x768" (width too large for virtual size)
[   537.713] (II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[   537.713] (II) CHROME(0): Not using default mode "1360x768" (width too large for virtual size)
...same with many other sizes...
[   537.713] (II) CHROME(0): Not using default mode "1920x1200" (width too large for virtual size)
[   537.713] (II) CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
[   537.713] (II) CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
[   537.713] (II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   537.713] (II) CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
[   537.714] (II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   537.714] (II) CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
[   537.714] (II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   537.714] (II) CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
[   537.714] (II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   537.714] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 108000)
[   537.714] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.714] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 40000)
[   537.714] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.714] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 36000)
[   537.714] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.714] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
[   537.714] (II) CHROME(0): ViaFirstCRTCModeValid
...same with other numbers....
[   537.719] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
[   537.719] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.719] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 25175)
[   537.719] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.719] (II) CHROME(0): ViaValidMode: Validating 720x400 (Clock: 28320)
[   537.719] (II) CHROME(0): ViaFirstCRTCModeValid
[   537.720] (--) CHROME(0): Virtual size is 1280x1024 (pitch 1280)
[   537.720] (**) CHROME(0): *Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[   537.720] (II) CHROME(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   537.720] (**) CHROME(0): *Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
[   537.720] (II) CHROME(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   537.720] (**) CHROME(0): *Default mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
[   537.720] (II) CHROME(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   537.720] (**) CHROME(0): *Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[   537.720] (II) CHROME(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   537.720] (**) CHROME(0): *Default mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
[   537.720] (II) CHROME(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   537.720] (**) CHROME(0): *Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
[   537.720] (II) CHROME(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   537.720] (**) CHROME(0): *Default mode "1152x864": 105.0 MHz (scaled from 0.0 MHz), 67.6 kHz, 75.0 Hz
[   537.720] (II) CHROME(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
[   537.720] (**) CHROME(0): *Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
[   537.721] (II) CHROME(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
[   537.721] (**) CHROME(0): *Default mode "1152x864": 81.6 MHz (scaled from -0.0 MHz), 53.7 kHz, 60.0 Hz
....same with other numbers
[   537.722] (II) CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   537.722] (**) CHROME(0): *Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[   537.723] (II) CHROME(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   537.723] (**) CHROME(0): Display dimensions: (340, 270) mm
[   537.723] (WW) CHROME(0): Probed monitor is 200x110 mm, using Displaysize 340x270 mm
[   537.723] (**) CHROME(0): DPI set to (95, 96)

---

### Post by Fafler on 2010-12-29
```
[   537.590] (EE) CHROME(0): Unknown Card-Ids (1122|1509|3002), Chipset:  VX800/VX820; please report to openchrome-users at openchrome.org
```

This is probably the problem. You should get in touch with the developers. I think they would like to know stuff like your full /var/log/Xorg.0.log and the output of lspci -vv

[http://www.openchrome.org/trac/wiki/SupportedHardware](http://www.openchrome.org/trac/wiki/SupportedHardware) doesn´t give much info, but might still be interesting for you.

The "No required driver detected for Unity" thing you mentioned earlier could also become a problem later on. I think Unity (the Window manager used by the Netbook Remix) need a working OpenGl driver and chrome driver doesn´t support that. Maybe it works with the normal Gnome desktop enviroment?

---

### Post by spoirier on 2011-01-02
Does anyone know how to contact the developers of the driver ?
The invalid page you gave me in pm, [http://www.winischhofer.at/linuxsisvga.shtml](http://www.winischhofer.at/linuxsisvga.shtml)
is also absent from google cache, so that I'm afraid it won't be up again soon.
Thank you for your help.

---

### Post by Fafler on 2011-01-03
Man, this is why i want to keep everything in the thread. The link i gave you is for a completely different graphics chipsset. I'm involved in way too many threads to remember specific hardware details from time to time...

Theres a link to the list and their website in the error message from your Xorg.0.log:
```
[ 537.590] (EE) CHROME(0): Unknown Card-Ids (1122|1509|3002), Chipset: VX800/VX820; please report to openchrome-users at openchrome.org
```

The mailing list is located at:
[http://wiki.openchrome.org/mailman/listinfo/openchrome-users](http://wiki.openchrome.org/mailman/listinfo/openchrome-users)

Go to that site and sign up. You will now receive everything that is send to that list and anything you send to the list address is sent out to everyone on it. The traffic is probably quite low and you can unsubscribe after the issue is resolved. Send a detailed description of the problem to the list and hope for a reply. Even if the Unknown ID isn't really the problem, they might still have some useful information for you.

Or we could just figure the Suse password problem out. It's apparently working there and i think Suse is on par with Ubuntu when it comes to features and userfriendlyness.

Oh, and by the way, [www.winischhofer.at](www.winischhofer.at) is up again :-)

---

### Post by spoirier on 2011-05-09
I got the following reply:
> This should be fixed in trunk rev 904. You can either rebuild the driver
from an subversion checkout

[http://www.openchrome.org/trac/wiki/Installation#InstallfromSVN](http://www.openchrome.org/trac/wiki/Installation#InstallfromSVN)

or add
 Option "ForcePanel"
 to the device section of your xorg conf: if you have an xorg conf file (/etc/X11/xorg.conf), add
Option "ForcePanel"
below the line that says :
Driver      "openchrome"

afaik, Unity requires 3D driver but there's no free 3D driver for
Chrome9 chipsets. This shouldn't be a show-stopper though.
Long later I went on to try applying this:

[http://www.openchrome.org/trac/wiki/Installation#InstallfromSVN](http://www.openchrome.org/trac/wiki/Installation#InstallfromSVN)

First the system said I must install subversion, so I did it.
Then the command
./autogen.sh --prefix=/usr
gave the following reply
./autogen.sh: 9: autoreconf: not found

But it was because it needed to install the dependencies first, as described just below in the same page.
So finally at the next try I installed subversion, then the dependencies, then went on as described.
Now everything is OK, I could complete the installation.

---

