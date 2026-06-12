---
title: "No 3D accelaraion after upgrade to Lucid"
date: 2010-05-06
forum: Hardware
---

### Post by MrNatewood on 2010-05-06
I have an ATI Radeon HD5470 on a Dell Studio 1555 laptop.

During the upgrade the fglrx package failed to install. After searching a bit I found a workaround which was to first uninstall all "nvidia" packages and deleting /usr/share/ati.

Then I was able to install the ATI package. But I still don't have 3d working for some reason.

When trying to enable desktop effects I am given this error:
[IMG]http://img97.imageshack.us/img97/9506/desktopeffects.png[/IMG]

When trying to run a 3D game(penumbra):
```
./penumbra.bin: ./lib/libCgGL.so: no version information available (required by ./penumbra.bin)
./penumbra.bin: ./lib/libCg.so: no version information available (required by ./penumbra.bin)
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  13
  Current serial number in output stream:  14
Penumbra: Overture exited unexpectedly, please check
/home/shimi/.frictionalgames/Penumbra/Overture/hpl.log
for any error messages
Also try running
ulimit -c unlimited
And re-running Penumbra and try and recreate the error
then submit the generated core file or stack trace

```

Open Arena:
```
ioq3+oa 1.35 linux-x86_64 Dec 18 2009
----- FS_Startup -----
Current search path:
/home/shimi/.openarena/baseoa/wtf-q3a_v3.pk3 (1963 files)
/home/shimi/.openarena/baseoa/ut_subway.pk3 (169 files)
/home/shimi/.openarena/baseoa/TeamTemple_q3a.pk3 (177 files)
/home/shimi/.openarena/baseoa/simp4.pk3 (49 files)
/home/shimi/.openarena/baseoa/moonstone.pk3 (156 files)
/home/shimi/.openarena/baseoa/map-rjlctf2.pk3 (29 files)
/home/shimi/.openarena/baseoa/map-kellblack.pk3 (118 files)
/home/shimi/.openarena/baseoa/map-13vast.pk3 (83 files)
/home/shimi/.openarena/baseoa/LetGo_q3a.pk3 (71 files)
/home/shimi/.openarena/baseoa/leafland.pk3 (32 files)
/home/shimi/.openarena/baseoa/gon2.pk3 (64 files)
/home/shimi/.openarena/baseoa/ctctf.pk3 (251 files)
/home/shimi/.openarena/baseoa/bastir.pk3 (102 files)
/home/shimi/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (1042 files)
/usr/share/games/openarena/baseoa

----------------------
7427 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL using driver "x11"
Initializing OpenGL display
Estimated display aspect: 1.778
...setting mode -1: 1920 1080
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  13
  Current serial number in output stream:  14

```

Hardware Drivers screenshot:
[IMG]http://img30.imageshack.us/img30/1783/hardwaredrivers.png[/IMG]

compiz-replace:
```
compiz (core) - Fatal: glXCreateContext failed
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_2"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_1"

```

Trying to uninstall fglrx:
```

sudo dpkg --purge fglrx
(Reading database ... 306075 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--purge):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx

```
EDIT:
solution: installing the driver from AMD's website

---

### Post by enchesss on 2010-05-07
thanks Mr Natewood for the solution hint

having same prob and have tried this before

am trying again because the flgrx drivers are jumpy on video and i removed xorg to get reasonable video with ati drivers (opensource) but now am getting error like yours with openarena

will try to install ati from website but can you outline the steps you followed more closely in detail please

---

### Post by kapcom01 on 2010-05-07
how did you installed drivers from ATI's website?
can you help me? this is what i did [http://ubuntuforums.org/showthread.php?t=1476115]("http://ubuntuforums.org/showthread.php?t=1476115")

---

### Post by MrNatewood on 2010-05-08
First I removed the diversions by running:
```
sudo dpkg-divert --remove /usr/lib32/libGL.so.1.2
sudo dpkg-divert --remove /usr/lib/libGL.so.1.2

```

Than I was able to properly remove the fglrx package.

Than I downloaded this driver:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-4-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-4-x86.x86_64.run)
(don't click on the link... firefox will try to open as text file, "save as".)


```
sudo sh ./ati-driver-installer-10-4-x86.x86_64.run

```

Restart and done.

Downside is not getting driver updates from Update Manager.

---

### Post by niiiklas on 2010-05-27
Hey,

I've run into the same problem and I tried fixing it the way you did by installing the fglrx driver from ATI's site (catalyst 10.5). The installation itself went fine, openarena and other games work fine as well now. However, I now have a problem viewing videos. If I tell vlc to go into fullscreen it takes about two seconds until it reacts and the screen will stay black for another two seconds or so until the video finally shows up. Youtube videos for example behave similar, but also lag as hell. 

Any ideas how to fix this? If not, I'm considering going back to the fglrx driver that ran before despite the fact that I couldn't even set visual effects to normal with that one or play games. Watching videos properly just has a higher priority to me.

Thank you.

---

### Post by MrNatewood on 2010-05-28
> **niiiklas said:**
> Hey,

I've run into the same problem and I tried fixing it the way you did by installing the fglrx driver from ATI's site (catalyst 10.5). The installation itself went fine, openarena and other games work fine as well now. However, I now have a problem viewing videos. If I tell vlc to go into fullscreen it takes about two seconds until it reacts and the screen will stay black for another two seconds or so until the video finally shows up. Youtube videos for example behave similar, but also lag as hell. 

Any ideas how to fix this? If not, I'm considering going back to the fglrx driver that ran before despite the fact that I couldn't even set visual effects to normal with that one or play games. Watching videos properly just has a higher priority to me.

Thank you.

Since than I also experienced trouble with the driver from ati.com.
I did manage to remove it and get the fglrx working properly.
 
I'll try to re-create what I did though I might not remember 100%:
First of all I removed the Manually installed driver:
```
cd /usr/share/ati
sudo sh fglrx-uninstall.sh

```

Then I installed the fglrx package from Synaptic and made sure it installed properly(no errors), if there are errors you may want to repeat the diversions fix mentioned earlier.
And than:
```
gksu gedit /etc/X11/xorg.conf
```

and edited it so this was it's contents:
```
Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection
```
(copied over from the backed-up xorg.conf from before the upgrade)

---

### Post by ggorman on 2010-05-28
> **MrNatewood said:**
> First I removed the diversions by running:
```
sudo dpkg-divert --remove /usr/lib32/libGL.so.1.2
sudo dpkg-divert --remove /usr/lib/libGL.so.1.2

```Than I was able to properly remove the fglrx package.

Than I downloaded this driver:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-4-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-4-x86.x86_64.run)
(don't click on the link... firefox will try to open as text file, "save as".)


```
sudo sh ./ati-driver-installer-10-4-x86.x86_64.run

```Restart and done.

Downside is not getting driver updates from Update Manager.

Tried that, got this 
```

==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-22-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.BB9Ftx
ggo@ggo-laptop:~/Downloads/fglrx-8.583$ ls

```

Any suggestions?

---

### Post by kapcom01 on 2010-05-29
For me the installation completed successfully but when i run ATI CCC it says that there is no driver installed...
```
kapcom01@Manolis-PC:~$ aticonfig
aticonfig: No supported adapters detected

```

I have Radeon X800..

---

