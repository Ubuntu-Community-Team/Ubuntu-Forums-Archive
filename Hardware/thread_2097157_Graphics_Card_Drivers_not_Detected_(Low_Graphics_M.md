---
title: "Graphics Card Drivers not Detected (Low Graphics Mode)"
date: 2012-12-22
forum: Hardware
---

### Post by rolya96 on 2012-12-22
I have a Dual boot of Ubuntu 12.10 and Windows 7 created by the Wubi Installer, I installed the latest updates through the Software Updater and after a reboot, it entered "Low Graphics Mode" I have a nvidia GEForce with CUDA graphics card and and Intel i5-2410M CPU with Intel HD Graphics.

After the boot a Dialog box  saying that the laptop is in Low Graphics mode and the 'Screen, Graphic Card & Input device settings could not be detected correctly. Please configure these yourself.'

'Run in Low Graphics Mode for 1 session' brings up a dialoge box with 'Stand by one minute while the display restarts...' which does nothing and when "OK" is clicked goes to a black screen.

'Reconfigure Graphics' does nothing and returns to the current menu

'Exit to Console Login' goes to a Black screen and does nothing.

'Troubleshoot Problems' has a blank 'Startup Errors' File, 'Edit Config File' returns to the current menu and the 'xserver log file' contains these errors:

```
(WW) Directory "user/share/fonts/XIV/(multiple fonts)" does not exist.
Entry deleted from font path

Load Module "nvidia"
(WW) Warning, couldn't open module nvidia
UnloadModule:"nvidia"
Unloading nvidia
(WW) Failed to load module "nvidia" (Module does not exist,0)

Load Module "nv"
(WW) Warning, couldn't open module nv
UnloadModule:"nv"
Unloading nv
(WW) Failed to load module "nv" (Module does not exist,0)

Load Module "nvidia"
(WW) Warning, couldn't open module nvidia
UnloadModule:"nvidia"
Unloading nvidia
(WW) Failed to load module "nvidia" (Module does not exist,0)

Load Module "nv"
(WW) Warning, couldn't open module nv
UnloadModule:"nv"
Unloading nv
(WW) Failed to load module "nv" (Module does not exist,0)

Falling back to old probe method for vesa
Falling back to old probe method for modesetting
Falling back to old probe method for fbder

(EE)
(EE) aBacktrace:
(EE) 0:/usr/bin/x (xorg_backtrace+0x49)[0xb7739cd9]
(EE) 1:/usr/bin/x (0xb759000+0x1abbc6)[0xb773dbc6]
(EE) 2:(vdso)(__kernel_rt_sigreturn+0x0)[0xb756f40c]
(EE) (EE)3:/usr/lib/xorg/modules/drivers/nouveau_drv.so(0xbbe9f000+0x2b3e)[0xb756f40c]
(EE)4:/usr/bin/x(WakeupHandler+0x6a)[0xb75d31ca]
(EE)5:/usr/bin/x(WaitForSomething+0x19b)[0xb7736f5b]
(EE)6:/usr/bin/x(0xb7592000+0x3c91e)[0xb75ce91e]
(EE)7:/usr/bin/x(0xb7592000+0x2a10a)[0xb75bc10a]
(EE)8:/lib/i386-linux-gnu/libe.so.b
(EE)9:/usr/bin/x

Caught Signal 11 (Segmentation Fault). Server Aborting.

```

These are all of the Errors that I could find in the xserver log file and surrounding text which may be helpful. I have a live USB of Ubuntu if that is of any help in fixing this error.

At most points of the dialogue boxes and black screens, I can press the power button on my laptop and it shuts down 'normally'

Note that Ubuntu was working perfectly until it updated through the software updater a day or two ago.

---

### Post by amiliv on 2012-12-23
This sounds exactly like the problem I'm having lately.  So looks like I'm not alone, and you are not alone either...

Which card do you have?  The one I'm having trouble with is reported as: NVIDIA GPU GeForce GT 440 (GF106).  It used to work perfectly fine until few weeks ago.

I found that switching to Nouveau open source driver "solves" the immediate problem reliably, as long as you can do without 3D acceleration (e.g. X-Plane will bitterly refuse to start when using this driver).

Also, it seems that rebooting machine when you get stuck on that "low res / reconfigure graphics" screen loop, will get you to login prompt eventually (if you reboot machine sufficient number of times).  Of course, next time you boot, you are in for the same problem.

---

### Post by rolya96 on 2012-12-23
I spent a couple of hours with a friend who knows Linux well and after 3 hours, we hadn't made much (if any) progress because Xorg was complaining and wanting to use the Intel HD Graphics. I'm going to try re-installing and hopefully that will work better.

---

