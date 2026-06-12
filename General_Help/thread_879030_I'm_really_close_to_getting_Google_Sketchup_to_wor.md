---
title: "I'm really close to getting Google Sketchup to work..."
date: 2008-08-03
forum: General Help
---

### Post by Ameades on 2008-08-03
Hey guys,

I've been searching for about an hour now and still cannot find a way to fix Sketch-up so that I can see the 3d objects.  When I open Sketchup everything seems to work except that there is a black screen which I know is some sort of 3d problem/open GL issue and I cannot figure out how to fix it.  

I believe this is my video card: 00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

I have tried installing Compiz-Switch and using that to switch off compiz and then opening Sketchup but that still did not work.


What am I missing here???

---

### Post by Ameades on 2008-08-03
I should also mention that I have upgraded to the latest version of wine 1.1.2

---

### Post by daleus on 2008-08-03
did you try

wine programname.exe --opengl

To allow wine to use opengl?

It would most likely help with the 3D

---

### Post by Ameades on 2008-08-03
I tried that and this is what I recieved

andrew@andrews-laptop:~$ wine sketchup.exe --opengl
wine: could not load L"C:\\windows\\system32\\sketchup.exe": Module not found
andrew@andrews-laptop:~$ wine SketchUp.exe --opengl
wine: could not load L"C:\\windows\\system32\\SketchUp.exe": Module not found
andrew@andrews-laptop:~$

---

### Post by edd07 on 2008-08-03
You need to write the complete location of sketchup.exe. Like /home/username/sketchup.exe or something like that, depending on where you have it in your hard drive. So...
```
wine /path/to/sketchup.exe --opengl
```
Hope this helps

---

### Post by Ameades on 2008-08-04
This is what I recieved after trying that:

fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (30000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 30000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 30000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_CONNECT_RETRIES 0
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2029 WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 2007 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2029 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2029 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 2007 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2007 WGL Attribute
fixme:wgl:ConvertAttribWGLtoGLX unsupported 2028 WGL Attribute
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (30000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 30000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 30000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_CONNECT_RETRIES 0
fixme:wininet:INET_QueryOption INTERNET_OPTION_CONNECTED_STATE: semi-stub
fixme:wininet:INET_QueryOption INTERNET_OPTION_CONNECTED_STATE: semi-stub


SketchUp opened but there was still a black screen.

---

### Post by ubi-laptop on 2008-09-23
I get exactly the same error bat on different system

graphic card
NVRM version: NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
GCC version:  gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Ubuntu Release 8.04 Hardy
kernel linux 2.6.24-19-generic
Gnome 2.22.3

---

### Post by C.S.Cameron on 2008-09-23
I was checking just this morning, (with an 8 meg high texture model), and SU runs just as well for me in Ubuntu as in Windows, same orbit/zoom speed with the same texture degradation.
Using a 8800GTS card and booting Ubuntu from flash drive.
Plugging the flash drive into my laptop with ATI X700 card and using the restricted drivers, I can't get beyond the black screen.
I do not recall anybody ever recommending ATI in the SU forums.

---

### Post by Ned490 on 2008-10-01
C.S.'s post is tantalizing--so SU can be made to work?

I'm on Hardy, using an Nvidia card and proprietary drivers.

When I execute SketchUp, here's what I get.  Any insights?

```
ned@moonlight-l:~/.wine/drive_c/Program Files/Google/Google SketchUp 6$ wine SketchUp.exe --opengl
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  427
  Current serial number in output stream:  427
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7e664767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0x7e66481e]
#2 /usr/lib/libX11.so.6 [0x7e74c518]
#3 /usr/lib/libX11.so.6(XESetCloseDisplay+0x31) [0x7e72f8d1]
#4 /usr/lib/libGL.so.1 [0x7e6aeb69]
#5 [0x7c039cb0]

```Thanks,
Ned

---

### Post by nikkkko on 2008-10-23
Did you do the registry fix?

```
[HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConfig\Display]
"FIRST_TIME"=dword:00000000
"HW_OK"=dword:00000001
```

Go to the windows directory in your fake C drive and click on regedit.exe

navigate to the HKEY as above and set HW_OK to be "1" instead of "0".  That worked for me and SU works just about perfectly. Even ruby scripts.

---

### Post by dankegel on 2008-11-23
Sketchup 7 is working fine for me (I have an Nvidia 8500 graphics card, and I'm using the latest drivers on Intrepid) once I follow the tips in 
  [http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup)
but I'm no expert.  
If after following the tips there, you still have
problems, please report them to the wine appdb or bugzilla
and I'll try to get them fixed, if I can.

(That page links to one guy's report of success with Intel 945 graphics.
but I doubt that Intel 910 is going to cut it, sorry...)

Thanks!

---

