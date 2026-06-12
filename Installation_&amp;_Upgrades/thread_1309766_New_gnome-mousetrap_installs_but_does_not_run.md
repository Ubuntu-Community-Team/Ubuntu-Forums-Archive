---
title: "New gnome-mousetrap installs but does not run"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by a1call on 2009-11-01
Hi,

The title says it all. The new addition to ubuntu 9.10, gnome-mousetrap (accessibility software for webcam head-tracking)installed on a fresh installation as well as an upgrade. Both fail to start the app.
One hint to one issue (most likely not the only issue) is if you type mousetrap in the console it falls in a loop for missing python 2.5 (9.10 has python 2.6). Installing python 2.5 does not resolve the issue.:(

---

### Post by lachlanc on 2009-11-02
Hi,
I have been having the same issue and have filed a bug report[COLOR=RoyalBlue]_ [http://bugs.launchpad.net/ubuntu/+source/gnome-mousetrap/+bug/470193](http://bugs.launchpad.net/ubuntu/+source/gnome-mousetrap/+bug/470193)_[/COLOR]

---

### Post by a1call on 2009-11-02
Thank you for the reply and the bug report link lachlanc,

Let's hope this issue resolves soon so that the disabled can utilize it.
One note is that both my versions are 32 bit.

---

### Post by diego.pedrosa on 2009-11-05
Hi,

The same is happening with me, I tried to install the the phyton2.5 and still not working.
But there are two differents packages available on the karmic: gnome-mousetrap and mousetrap. I tried to install the mousetrap too by apt-get and I got a different message error.

*** buffer overflow detected ***: mousetrap terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0x301de8]
/lib/tls/i686/cmov/libc.so.6[0x300e20]
/lib/tls/i686/cmov/libc.so.6[0x300558]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0x28a59e]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x60a)[0x25e14a]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0x30060d]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0x30054d]
mousetrap[0x804b919]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x237b56]
mousetrap(__gxx_personality_v0+0x5d)[0x8049211]
======= Memory map: ========
00110000-0015e000 r-xp 00000000 08:05 86143      /usr/lib/libmikmod.so.2.0.4
0015e000-0015f000 r--p 0004e000 08:05 86143      /usr/lib/libmikmod.so.2.0.4
0015f000-00160000 rw-p 0004f000 08:05 86143      /usr/lib/libmikmod.so.2.0.4
00160000-00161000 rw-p 00000000 00:00 0 
00161000-00168000 r-xp 00000000 08:05 6041       /usr/lib/libvorbisfile.so.3.2.0
00168000-00169000 r--p 00007000 08:05 6041       /usr/lib/libvorbisfile.so.3.2.0
00169000-0016a000 rw-p 00008000 08:05 6041       /usr/lib/libvorbisfile.so.3.2.0
0016a000-001e0000 r-xp 00000000 08:05 5261       /usr/lib/libdirectfb-1.2.so.0.7.0
001e0000-001e1000 ---p 00076000 08:05 5261       /usr/lib/libdirectfb-1.2.so.0.7.0
001e1000-001e2000 r--p 00076000 08:05 5261       /usr/lib/libdirectfb-1.2.so.0.7.0
001e2000-001e3000 rw-p 00077000 08:05 5261       /usr/lib/libdirectfb-1.2.so.0.7.0
001e3000-001e4000 rw-p 00000000 00:00 0 
001e4000-001eb000 r-xp 00000000 08:05 527016     /lib/tls/i686/cmov/librt-2.10.1.so
001eb000-001ec000 r--p 00006000 08:05 527016     /lib/tls/i686/cmov/librt-2.10.1.so
001ec000-001ed000 rw-p 00007000 08:05 527016     /lib/tls/i686/cmov/librt-2.10.1.so
001ed000-001f2000 r-xp 00000000 08:05 5788       /usr/lib/libogg.so.0.6.0
001f2000-001f3000 r--p 00004000 08:05 5788       /usr/lib/libogg.so.0.6.0
001f3000-001f4000 rw-p 00005000 08:05 5788       /usr/lib/libogg.so.0.6.0
001f4000-001f6000 r-xp 00000000 08:05 5034       /usr/lib/libXau.so.6.0.0
001f6000-001f7000 r--p 00001000 08:05 5034       /usr/lib/libXau.so.6.0.0
001f7000-001f8000 rw-p 00002000 08:05 5034       /usr/lib/libXau.so.6.0.0
001f8000-001fc000 r-xp 00000000 08:05 5045       /usr/lib/libXdmcp.so.6.0.0
001fc000-001fd000 rw-p 00003000 08:05 5045       /usr/lib/libXdmcp.so.6.0.0
001fd000-0020b000 r-xp 00000000 08:05 58243      /usr/lib/libXext.so.6.4.0
0020b000-0020c000 r--p 0000d000 08:05 58243      /usr/lib/libXext.so.6.4.0
0020c000-0020d000 rw-p 0000e000 08:05 58243      /usr/lib/libXext.so.6.4.0
0020d000-00216000 r-xp 00000000 08:05 5041       /usr/lib/libXcursor.so.1.0.2
00216000-00217000 r--p 00008000 08:05 5041       /usr/lib/libXcursor.so.1.0.2
00217000-00218000 rw-p 00009000 08:05 5041       /usr/lib/libXcursor.so.1.0.2
00220000-00221000 r-xp 00000000 00:00 0          [vdso]
00221000-0035f000 r-xp 00000000 08:05 525356     /lib/tls/i686/cmov/libc-2.10.1.so
0035f000-00361000 r--p 0013e000 08:05 525356     /lib/tls/i686/cmov/libc-2.10.1.so
00361000-00362000 rw-p 00140000 08:05 525356     /lib/tls/i686/cmov/libc-2.10.1.so
00362000-00365000 rw-p 00000000 00:00 0 
00398000-0039a000 r-xp 00000000 08:05 526234     /lib/tls/i686/cmov/libdl-2.10.1.so
0039a000-0039b000 r--p 00001000 08:05 526234     /lib/tls/i686/cmov/libdl-2.10.1.so
0039b000-0039c000 rw-p 00002000 08:05 526234     /lib/tls/i686/cmov/libdl-2.10.1.so
00449000-00465000 r-xp 00000000 08:05 1898       /lib/libgcc_s.so.1
00465000-00466000 r--p 0001b000 08:05 1898       /lib/libgcc_s.so.1
00466000-00467000 rw-p 0001c000 08:05 1898       /lib/libgcc_s.so.1
00467000-00529000 r-xp 00000000 08:05 6810       /usr/lib/libasound.so.2.0.0
00529000-0052d000 r--p 000c1000 08:05 6810       /usr/lib/libasound.so.2.0.0
0052d000-0052e000 rw-p 000c5000 08:05 6810       /usr/lib/libasound.so.2.0.0
005d9000-006bf000 r-xp 00000000 08:05 4043       /usr/lib/libstdc++.so.6.0.13
006bf000-006c3000 r--p 000e6000 08:05 4043       /usr/lib/libstdc++.so.6.0.13
006c3000-006c4000 rw-p 000ea000 08:05 4043       /usr/lib/libstdc++.so.6.0.13
006c4000-006cb000 rw-p 00000000 00:00 0 
0071c000-00789000 r-xp 00000000 08:05 5024       /usr/lib/libSDL-1.2.so.0.11.2
00789000-0078a000 r--p 0006c000 08:05 5024       /usr/lib/libSDL-1.2.so.0.11.2
0078a000-0078b000 rw-p 0006d000 08:05 5024       /usr/lib/libSDL-1.2.so.0.11.2
0078b000-007b6000 rw-p 00000000 00:00 0 
0084d000-00888000 r-xp 00000000 08:05 97578      /usr/lib/libsmpeg-0.4.so.0.1.4
00888000-00889000 r--p 0003a000 08:05 97578      /usr/lib/libsmpeg-0.4.so.0.1.4
00889000-0088a000 rw-p 0003b000 08:05 97578      /usr/lib/libsmpeg-0.4.so.0.1.4
0088a000-008a6000 rw-p 00000000 00:00 0 
008a6000-009d0000 r-xp 00000000 08:05 5028       /usr/lib/libX11.so.6.2.0
009d0000-009d1000 ---p 0012a000 08:05 5028       /usr/lib/libX11.so.6.2.0
009d1000-009d2000 r--p 0012a000 08:05 5028       /usr/lib/libX11.so.6.2.0
009d2000-009d4000 rw-p 0012b000 08:05 5028       /usr/lib/libX11.so.6.2.0
009d4000-009d5000 rw-p 00000000 00:00 0 
00a0b000-00a1e000 r-xp 00000000 08:05 94488      /usr/lib/libSDL_gfx.so.13.5.1
00a1e000-00a1f000 r--p 00013000 08:05 94488      /usr/lib/libSDL_gfx.so.13.5.1
00a1f000-00a20000 rw-p 00014000 08:05 94488      /usr/lib/libSDL_gfx.so.13.5.1
00a20000-00a21000 rw-p 00000000 00:00 0 
00a33000-00a37000 r-xp 00000000 08:05 5049       /usr/lib/libXfixes.so.3.1.0
00a37000-00a38000 r--p 00003000 08:05 5049       /usr/lib/libXfixes.so.3.1.0
00a38000-00a39000 rw-p 00004000 08:05 5049       /usr/lib/libXfixes.so.3.1.0
00adc000-00af8000 r-xp 00000000 08:05 6037       /usr/lib/libvorbis.so.0.4.0
00af8000-00af9000 r--p 0001b000 08:05 6037       /usr/lib/libvorbis.so.0.4.0
00af9000-00b07000 rw-p 0001c000 08:05 6037       /usr/lib/libvorbis.so.0.4.0
00b9a000-00bc1000 r-xp 00000000 08:05 97593      /usr/lib/libSDL_mixer-1.2.so.0.2.6
00bc1000-00bc2000 r--p 00026000 08:05 97593      /usr/lib/libSDL_mixer-1.2.so.0.2.6
00bc2000-00bcb000 rw-p 00027000 08:05 97593      /usr/lib/libSDL_mixer-1.2.so.0.2.6
00bcb000-00bf5000 rw-p 00000000 00:00 0 
00c62000-00c7e000 r-xp 00000000 08:05 6078       /usr/lib/libxcb.so.1.1.0
00c7e000-00c7f000 r--p 0001c000 08:05 6078       /usr/lib/libxcb.so.1.1.0
00c7f000-00c80000 rw-p 0001d000 08:05 6078       /usr/lib/libxcb.so.1.1.0
00d90000-00da6000 r-xp 00000000 08:05 5259       /usr/lib/libdirect-1.2.so.0.7.0
00da6000-00da7000 r--p 00015000 08:05 5259       /usr/lib/libdirect-1.2.so.0.7.0
00da7000-00da8000 rw-p 00016000 08:05 5259       /usr/lib/libdirect-1.2.so.0.7.0
00db8000-00ddc000 r-xp 00000000 08:05 526235     /lib/tls/i686/cmov/libm-2.10.1.so
00ddc000-00ddd000 r--p 00023000 08:05 526235     /lib/tls/i686/cmov/libm-2.10.1.so
00ddd000-00dde000 rw-p 00024000 08:05 526235     /lib/tls/i686/cmov/libm-2.10.1.so
00e99000-00ea1000 r-xp 00000000 08:05 58255      /usr/lib/libXrender.so.1.3.0Aborted

Could you give a hand here??

Tks!!

---

### Post by a1call on 2009-11-05
Hi [diego.pedrosa]("http://ubuntuforums.org/member.php?u=947445"),

Mousetrap refers to an unrelated game and gnome-mousetrap is the accessibility software.

I could see some communications in google results regarding ubuntu asking the developers to prepare the software for python 2.6 and a reply that it is "done". But apparently not so.(from what I remember from googling a few days ago)

---

### Post by The End of The World on 2009-12-20
Hey 
this might be completely wrong :P but i just ran ```
sudo apt-get install python2.5
``` which sorted one problem, though now it comes up with:

```
dan@acerAspire:~$ mousetrap
DEBUG: mousetrap.mouse -> GNOME desktop has been detected
DEBUG: mouseTrap -> Settings have been loaded
DEBUG: mouseTrap -> DBus Service has been started
ERROR: mousetrap -> Main Gui load failed
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.5/mouseTrap/mouseTrap.py", line 171, in showMainGui
    [''])
  File "/usr/lib/pymodules/python2.5/mouseTrap/mainGui.py", line 41, in <module>
    from opencv import cv
ImportError: No module named opencv
This modules depends of opencv libraries
ERROR: mousetrap -> Camera Module load failed
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.5/mouseTrap/mouseTrap.py", line 188, in startCam
    [''])
  File "/usr/lib/pymodules/python2.5/mouseTrap/cam.py", line 41, in <module>
    import ocvfw
  File "/usr/lib/pymodules/python2.5/mouseTrap/ocvfw.py", line 46, in <module>
    class ocvfw:
  File "/usr/lib/pymodules/python2.5/mouseTrap/ocvfw.py", line 65, in ocvfw
    def cmAddMessage(self, message, font = cv.CV_FONT_HERSHEY_COMPLEX, poss = None ):
NameError: name 'cv' is not defined
ERROR: mousetrap -> Events Handler Load Failed
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.5/mouseTrap/mouseTrap.py", line 210, in startEventsHandler
    modules["events"].startMapperListener( modules["gui"].mapper )
KeyError: 'gui'

```

rather fustratingly...
anyone get the same problem?

---

### Post by Skully on 2009-12-23
I'm getting the exact same error message: 


```
gnome-mousetrap: command not found
yeti@yeti-laptop:~$ mousetrap
DEBUG: mousetrap.mouse -> GNOME desktop has been detected
DEBUG: mouseTrap -> Settings have been loaded
DEBUG: mouseTrap -> DBus Service has been started
ERROR: mousetrap -> Main Gui load failed
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.5/mouseTrap/mouseTrap.py", line 171, in showMainGui
    [''])
  File "/usr/lib/pymodules/python2.5/mouseTrap/mainGui.py", line 41, in <module>
    from opencv import cv
ImportError: No module named opencv
This modules depends of opencv libraries
ERROR: mousetrap -> Camera Module load failed
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.5/mouseTrap/mouseTrap.py", line 188, in startCam
    [''])
  File "/usr/lib/pymodules/python2.5/mouseTrap/cam.py", line 41, in <module>
    import ocvfw
  File "/usr/lib/pymodules/python2.5/mouseTrap/ocvfw.py", line 46, in <module>
    class ocvfw:
  File "/usr/lib/pymodules/python2.5/mouseTrap/ocvfw.py", line 65, in ocvfw
    def cmAddMessage(self, message, font = cv.CV_FONT_HERSHEY_COMPLEX, poss = None ):
NameError: name 'cv' is not defined
ERROR: mousetrap -> Events Handler Load Failed
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.5/mouseTrap/mouseTrap.py", line 210, in startEventsHandler
    modules["events"].startMapperListener( modules["gui"].mapper )
KeyError: 'gui'

```

Sorry I'm a newbie and can't help.

---

### Post by VirusCollector on 2010-01-01
Same problem here. All my base are belong to MouseTrap.

---

### Post by lockalidiot on 2010-02-07
I also have trouble with this. I'm running Karmic.

I only get the infinite loop of "not finding python 2.5"...
Tried to install it(apt-get install python 2.5) but it just said that I already have the newest version (2.6).. I just cant get the bugger to work.

---

### Post by busy4thyr on 2010-02-08
lockalidiot :
you should be able to install both 2.6 and 2.5 from the Ubuntu Software center.

This fixed the v2.5 problem but now I'm getting the same error as Skully

---

### Post by fnielsen on 2010-02-09
As far as I can see there is no python2.5-opencv. I can only see 2.6:

$ aptitude search opencv
p   opencv-doc                      - OpenCV documentation and examples         
i A python-opencv                   - Python bindings for the computer vision li
v   python2.6-opencv                - 

Could this explain the problem?

---

### Post by netlaptop on 2010-02-12
Yes...

I got the same problem on my Ubuntu 9.10 64 bits. It said something linked to missing Python 2.5... 

Bookmarked, hope get it works soon. Thnx.

---

### Post by trx64 on 2010-02-19
I've found a solution. Edit the file /usr/bin/mousetrap:

$ sudo gedit /usr/bin/mousetrap

And search for "python-2.5" (it's just one line) and change to "python":

Original:
        /usr/bin/python-2.5 -c "import mouseTrap.mouseTrap as mouseTrap; mouseTrap.$


Edited:
        /usr/bin/python -c "import mouseTrap.mouseTrap as mouseTrap; mouseTrap.$


That solved the question for me.

---

### Post by netlaptop on 2010-02-22
> **trx64 said:**
> i've found a solution. Edit the file /usr/bin/mousetrap:

$ sudo gedit /usr/bin/mousetrap

and search for "python-2.5" (it's just one line) and change to "python":

Original:
        /usr/bin/python-2.5 -c "import mousetrap.mousetrap as mousetrap; mousetrap.$


edited:
        /usr/bin/python -c "import mousetrap.mousetrap as mousetrap; mousetrap.$


that solved the question for me.

thanks muchhhhh! It works for my ubuntu 9.10 64 bits.

---

### Post by binamenator on 2010-05-08
I have Ubuntu 10.04 but it's not working. I tried to change it, but I think it's a read only file system.

---

### Post by bcooperb on 2010-05-11
> **binamenator said:**
> I have Ubuntu 10.04 but it's not working. I tried to change it, but I think it's a read only file system.

If it is read only then you probably need to run:

[COLOR="Green"]sudo gedit mousetrap[/COLOR]

It's on about line 140ish changing that to just "python" instead of "python2.5" worked as far as not getting that error. I had to do sudo mousetrap from the commandline to get anything to open.

My light on my webcam turned on and the software seemed to halfway open up. I don't see my picture in the window. Not sure what else to try?

---

### Post by skaarr on 2010-06-23
> **bcooperb said:**
> My light on my webcam turned on and the software seemed to halfway open up. I don't see my picture in the window. Not sure what else to try?

I can also get it to run with sudo but I also sont see the picture.

The terminal output for sudo mousetrap is 
```
Xlib.protocol.request.QueryExtension
DEBUG: mouseTrap -> Settings have been loaded
DEBUG: mouseTrap -> DBus Service has been started
ERROR: scripts -> The Profile load failed
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/mouseTrap/scriptHdlr.py", line 57, in _loadThirdProfiles
    modes[prof.setName] = prof.Profile
AttributeError: 'module' object has no attribute 'Profile'
DEBUG: scripts -> Mousetrap holdProfile Profile has been loaded
DEBUG: scripts -> Mousetrap dragProfile Profile has been loaded
DEBUG: scripts -> Mousetrap screenProfile Profile has been loaded
ERROR: mainGui -> All arguments must be INT
ERROR: mainGui -> All arguments must be INT
DEBUG: events -> New Area Listener Added
DEBUG: events -> New Area Listener Added
DEBUG: scripts -> Profile Started
DEBUG: mouseTrap -> MainGui has been started
DEBUG: ocvfw -> cmStartCamera: Camera Started
DEBUG: mouseTrap -> Camera Module has been started
DEBUG: mouseTrap -> Events handler has been started

```Is this what your screen looks like [http://i48.tinypic.com/30t100z.png](http://i48.tinypic.com/30t100z.png)?

Has anyone managed to fix this problem?

---

### Post by kWinner on 2010-07-12
> Has anyone managed to fix this problem?Yes, I got it works on my Ubuntu 10.04 x64 and Samsung R560 laptop!
First, I've uninstalled it by Ubuntu software center.
After that, I followed this instruction: [http://live.gnome.org/MouseTrap/Installation](http://live.gnome.org/MouseTrap/Installation)

Some features:

[LIST=1]
[*]Remove **mousetrap **from Software center, if installed, or if you tried to install it :).
[*]Remove ''mousetrap''-like directories from home directory (there were 2 hidden and 1 normal  directory in my case);
[*]Run 1st and 2nd commands from your home directory;
[*]For 3rd and other commands change directory to ~/mousetrap;
[*]When you run ./autogen.sh, you can see some errors. Just install the missing packages from repos. If you already have these packages installed, try to install -dev packets.
[*]I've installed **libglib2.0-dev** (when **glib-gettext** error appears), **python-xlib**, **python-opencv**, **libcv4**, **libhighgui4**, **zlib1g-dev**, **python2.6-dev**.
[*]Editing the /usr/bin/mousetrap via [COLOR=Lime]sudo gedit /usr/bin/mousetrap[/COLOR] and changing [COLOR=Red]"/usr/bin/python-2.5 -c" [COLOR=Black]to [/COLOR][/COLOR][COLOR=Red]"/usr/bin/python -c"[/COLOR] is required too.
[/LIST]
I can't remember all the packets needed to install mousetrap properly (so **many** of them were installed in 2 hours), but if you have problems, I'll try to remember all issues of this.

[SIZE=1]Sorry for bad English :sad:.
Good Luck!
[/SIZE]

---

### Post by artmendez on 2011-06-28
> **trx64 said:**
> I've found a solution. Edit the file /usr/bin/mousetrap:

$ sudo gedit /usr/bin/mousetrap

And search for "python-2.5" (it's just one line) and change to "python":

Original:
        /usr/bin/python-2.5 -c "import mouseTrap.mouseTrap as mouseTrap; mouseTrap.$


Edited:
        /usr/bin/python -c "import mouseTrap.mouseTrap as mouseTrap; mouseTrap.$


That solved the question for me.

I am running 11.04 64-bit. The version I installed had the same line as:

```
/usr/bin/python-2.6 -c "import mousetrap.app.main as mousetrap;
```

changed it the same way to:

```
/usr/bin/python -c "import mousetrap.app.main as mousetrap;
```

Now the preferences and another window appear, but blank. I think I should be getting closer.

Anyone with such issue?

Regards.

---

### Post by sudo_rm_ignorance on 2011-10-18
> **bcooperb said:**
> If it is read only then you probably need to run:

[COLOR="Green"]sudo gedit mousetrap[/COLOR]

It's on about line 140ish changing that to just "python" instead of "python2.5" worked as far as not getting that error. I had to do sudo mousetrap from the commandline to get anything to open.

My light on my webcam turned on and the software seemed to halfway open up. I don't see my picture in the window. Not sure what else to try?

The other thing you can do is to change the owner from root to yourself with:
```
sudo chown username 'usr\bin\mousetrap'
```
Replace 'username' with your actual user name and you can now edit, save, whatever you want.  If you want to have it protected afterwards, simply change the owner back when you're done.

I am also having trouble with mousetrap, it seems like my webcam disappears between closing and opening mousetrap and it won't display anything, or sometimes it'll display a static image of my head and so hold the mouse in one location.  At least it runs, so maybe I'm on the right track?  I did tro the page mentioned a couple answers above me, thanks!


NEW:
Now I get the following error, most of the time.
```
cj@cj-laptop:~/mousetrap$ mousetrap
/home/cj/.themes/XPLuna/gtk-2.0/panel.rc:13: Unable to locate image file in pixmap_path: "shadows/window-bg.png"
/home/cj/.themes/XPLuna/gtk-2.0/panel.rc:112: Unable to locate image file in pixmap_path: "menubar/menubar-item.png"
/home/cj/.themes/XPLuna/gtk-2.0/panel.rc:115: Background image options specified without filename
/home/cj/.themes/XPLuna/gtk-2.0/panel.rc:13: Unable to locate image file in pixmap_path: "shadows/window-bg.png"
/home/cj/.themes/XPLuna/gtk-2.0/panel.rc:112: Unable to locate image file in pixmap_path: "menubar/menubar-item.png"
/home/cj/.themes/XPLuna/gtk-2.0/panel.rc:115: Background image options specified without filename
Xlib.protocol.request.QueryExtension
DEBUG: mousetrap.ocvfw.idm -> Starting Forehead idm
INFO: mousetrap.ocvfw.idm -> Forhead Algorithm loaded
DEBUG: mousetrap.ocvfw.idm -> Setting Capture
DEBUG: Commons -> New Singleton Add (mousetrap.ocvfw.dev.camera.Camera)
DEBUG: ocvfw -> cmStartCamera: Camera Started
DEBUG: Camera -> Loaded backend OcvfwPython
DEBUG: OcvfwBase -> Changed lk_swap value to True
INFO: mousetrap - Idm loaded and started
DEBUG: ui.main - Interface Built
DEBUG: addon.recalc - Recalc Addon started
DEBUG: ui.main - Addons loaded
INFO: mousetrap - MouseTrap's Interface Built and Loaded
Corrupt JPEG data: premature end of data segment
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/mousetrap/ocvfw/dev/camera.py", line 116, in sync
    Camera.query_image()
  File "/usr/local/lib/python2.6/dist-packages/mousetrap/ocvfw/_ocv.py", line 129, in query_image
    self.imgSize        = co.cv.cvGetSize (frame)
  File "/usr/lib/pymodules/python2.6/opencv/cv.py", line 4350, in cvGetSize
    return _cv.cvGetSize(*args)
RuntimeError:  openCV Error:
        Status=Bad argument
        function name=cvGetSize
        error message=Array should be CvMat or IplImage
        file_name=cxcore/cxarray.cpp
        line=1227
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/mousetrap/app/main.py", line 238, in update_frame
    self.itf.update_frame(self.idm.get_capture(), self.idm.get_pointer())
  File "/usr/local/lib/python2.6/dist-packages/mousetrap/ocvfw/idm/forehead.py", line 128, in get_capture
    self.get_forehead()
  File "/usr/local/lib/python2.6/dist-packages/mousetrap/ocvfw/idm/forehead.py", line 148, in get_forehead
    face     = self.cap.get_area(commons.haar_cds['Face'])
  File "/usr/local/lib/python2.6/dist-packages/mousetrap/ocvfw/dev/camera.py", line 373, in get_area
    return Camera.get_haar_points(haar_csd)
  File "/usr/local/lib/python2.6/dist-packages/mousetrap/ocvfw/_ocv.py", line 335, in get_haar_points
    cascade = co.cv.cvLoadHaarClassifierCascade( haarCascade, self.imgSize )
AttributeError: Camera instance has no attribute 'imgSize'

```

Then the window does come up, but I get no picture and no control.  Any ideas?

---

### Post by Malka4re on 2011-10-18
I'm getting the exact same error message: 

[img]http://www.webcohosting.com/frankaz2.jpg[/img]
[img]http://www.webcohosting.com/myjs.jpg[/img]
[img]http://www.webcohosting.com/frankht.jpg[/img]

---

### Post by Kangarooo on 2012-03-14
I dont have such file.. :(
Update: couse i installed just mousetrap and not gnome-mousetrap
doing gnome-mousetrap i could change but that gives just as one poste this image [http://i48.tinypic.com/30t100z.png](http://i48.tinypic.com/30t100z.png)

> **trx64 said:**
> I've found a solution. Edit the file /usr/bin/mousetrap:

$ sudo gedit /usr/bin/mousetrap

And search for "python-2.5" (it's just one line) and change to "python":

Original:
        /usr/bin/python-2.5 -c "import mouseTrap.mouseTrap as mouseTrap; mouseTrap.$


Edited:
        /usr/bin/python -c "import mouseTrap.mouseTrap as mouseTrap; mouseTrap.$


That solved the question for me.

---

