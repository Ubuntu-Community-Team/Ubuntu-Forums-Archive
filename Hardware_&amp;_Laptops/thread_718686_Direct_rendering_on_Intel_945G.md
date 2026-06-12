---
title: "Direct rendering on Intel 945G"
date: 2008-03-08
forum: Hardware &amp; Laptops
---

### Post by duncanbell on 2008-03-08
I am on a fresh install of 7.10 Gutsy. 

Done a whole lot of searching and tried a lot of things I found, but couldn't get anything to work, so here is my problem. 

I have a laptop using a 945G Intel chip for graphics, and am trying to enable direct rendering for playing games using 3d graphics. The result of glxinfo | grep direct returns this:

```
duncan@siemens:~$ glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

```

and glxinfo | grep render returns

```
duncan@siemens:~$ glxinfo | grep render
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2

```

and glxgears is successful, above 700fps.

I have tried using 'i810' and 'intel' as my drivers, both driver settings give the same outputs. 

The appropriate line of my xorg.conf gives 

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"


EDIT - I have also tried 

duncan@siemens:~$ export LIBGL_ALWAYS_INDIRECT=no
duncan@siemens:~$ glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

I don't (and never did) have xserver-xorg-xgl installed.

Hope I have given as much information as is needed.

Does anyone have any suggestions?

Thanks in advance! :)

---

### Post by duncanbell on 2008-03-08
Noone have any ideas?

---

### Post by Whiffle on 2008-03-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/137388](https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/137388) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Maybe try this,  i don't think "no" is the right value:

 export LIBGL_ALWAYS_INDIRECT=0

---

### Post by duncanbell on 2008-03-08
Thanks for the reply Wiffle.
Unfortunately, glxinfo | grep direct gives the same output of 'direct rendering: No (LIBGL_ALWAYS_INDIRECT set)' even after setting LIB_GL_ALWAYS_INDIRECT to 0. 

After looking at the bug report it seems others are in a similar situation :(

---

### Post by Whiffle on 2008-03-08
One other thing to try.  In your "Device" Section, try changing i810 to intel.  Make sure that  xserver-xorg-video-intel is installed first, and that the i915 driver is loaded (should be "modprobe i915")

---

### Post by duncanbell on 2008-03-08
Thanks Wiffle. I did some fiddling about and turned off all visual effects in 'Appearance' and now get a Yes for direct rendering. Thanks for your help :)

---

### Post by simosx on 2008-06-15
Dudes, if you want to unset a variable, you do 

unset VARIABLE_NAME

When you do "VARIABLE_NAME=0" or "VARIABLE_NAME=FALSE", the variable is still defined, which is opposite of what you want.

---

