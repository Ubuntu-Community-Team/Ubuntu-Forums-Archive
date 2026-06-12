---
title: "Do I have OpenGL ?"
date: 2015-01-26
forum: Hardware
---

### Post by michael-piziak on 2015-01-26
How can I determine if I have the hardware called OpenGL [or if I have XVideo hardware] or if my box is simply emulating it via software.

(When I select OpenGL in PCSX it works, but if I select it in SNES I have lag in some games).

---

### Post by TheFu on 2015-01-27
[http://askubuntu.com/questions/47062/what-is-terminal-command-that-can-show-opengl-version](http://askubuntu.com/questions/47062/what-is-terminal-command-that-can-show-opengl-version) says to run **glxinfo**.

---

### Post by michael-piziak on 2015-01-28
> **TheFu said:**
> [http://askubuntu.com/questions/47062/what-is-terminal-command-that-can-show-opengl-version](http://askubuntu.com/questions/47062/what-is-terminal-command-that-can-show-opengl-version) says to run **glxinfo**.


ok, I installed that and entered the command.  Here is what results:

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ glxinfo | grep "OpenGL version"
OpenGL version string: 1.4 Mesa 10.1.3
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ 


Does this mean I do or don't have Open GL hardware ?

---

### Post by vasa1 on 2015-01-28
> **michael-piziak said:**
> ok, I installed that and entered the command.  Here is what results:

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ glxinfo | grep "OpenGL version"
OpenGL version string: 1.4 Mesa 10.1.3
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ 


Does this mean I do or don't have Open GL hardware ?
If you have Firefox, go to *about:support*. I see this:```
Graphics
Adapter Description	Intel Open Source Technology Center -- Mesa DRI Mobile IntelÂ® GM45 Express Chipset
Device ID	Mesa DRI Mobile Intel® GM45 Express Chipset
Driver Version	2.1 Mesa 10.1.3
GPU Accelerated Windows	0/1 Basic
Vendor ID	Intel Open Source Technology Center
WebGL Renderer	Intel Open Source Technology Center -- Mesa DRI Mobile IntelÂ® GM45 Express Chipset
windowLayerManagerRemote	false
AzureCanvasBackend	cairo
AzureContentBackend	cairo
AzureFallbackCanvasBackend	none
AzureSkiaAccelerated	0

```And I think I don't have hardware acceleration because of *GPU Accelerated Windows	0/1 Basic*.

---

### Post by michael-piziak on 2015-01-28
I get this in Firefox:

Adapter Description	Intel Open Source Technology Center -- Mesa DRI Intel(R) Q33
Device ID	Mesa DRI Intel(R) Q33
Driver Version	1.4 Mesa 10.1.3
GPU Accelerated Windows	0/1 Basic Blocked for your graphics card because of unresolved driver issues.
Vendor ID	Intel Open Source Technology Center
WebGL Renderer	Blocked for your graphics card because of unresolved driver issues.
windowLayerManagerRemote	false
AzureCanvasBackend	cairo
AzureContentBackend	cairo
AzureFallbackCanvasBackend	none
AzureSkiaAccelerated	0

So what does that tell me about my OpenGL ?

---

### Post by Yellow Pasque on 2015-01-29
It tells us that you have an Intel GMA3100 GPU, which only has support for the relatively ancient OpenGL 1.4 version. You're not going to be able to run a lot of applications which require OpenGL 2.1 (and there are lot of apps, especially games, that require 2.1 at minimum).

---

### Post by michael-piziak on 2015-01-29
Thanks Temujin. 

Does this mean I have an old hardware that runs the older opengl or is my systems software simulating it ?

I'm basically an emualtion game player.  The emulators I use don't require a lot, I don't think.  I use NES emulator, SNES emulator, and PS1 emulator with little problems. For example, pcsx (ps1) emultor only uses opengl 1.178.    I'm sure if I tried a PS2 emualtor or others I would not be able to use them.

Thanks again !

---

### Post by Yellow Pasque on 2015-01-29
Your GPU only supports hardware-accelerated OpenGL 1.4, though it may also support acceleration for some features/extensions of OpenGL 2.x
It all comes down to the application, what features it requires, and how it checks for OpenGL support. Some applications simply look at the version number glxinfo reports, while some do a more thorough check for each extension.

---

### Post by michael-piziak on 2015-01-29
Thanks, marking this thread as solved.

---

