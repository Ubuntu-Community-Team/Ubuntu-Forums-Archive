---
title: "i810 Error"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by hedgefighter on 2007-06-02
Hey guys,
I'm having an issue running 3d in wine. I get this error:

libGL warning: 3D driver claims to not support visual 0x5b

I get the same error with glxinfo/glxgears. Beryl runs great. It doesn't seem to mind at all, but wine freezes on me. I'm using an Intel 945GM/PM/GMS/940GML with the i810 driver. I've searched a bit for a solution. It seems to be a common issue with i810 but I couldn't find any answer. Anyone have an idea?

Thanks!

---

### Post by ramjet_1953 on 2007-06-02
If you haven't already done it, try installing the new Intel driver.

In a terminal paste in this commend:

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

Re-boot and see if the problem is fixed.

Regards,
Roger :cool:

---

### Post by almkglor on 2007-06-02
Hello, I've been having some problems with my 945GM chipset.
My laptop is a Neo laptop (forgot the exact model number) and has an Intel 950 board.

I've been trying to find the "new" intel drivers, but can't find them.
When I execute the line above, apt-get says "E: Couldn't find package xserver-xorg-video-intel"
I suppose I need to setup the repository?

In any case, I installed the 64-bit version of Ubuntu Dapper Drake.  It seems that the 64-bit version is not as well suported as the 32-bit version.  For instance, I've been trying to get Easycam2 to try to detect my laptop's builtin webcam, but the repository I've found doesn't have 64-bit code (but that's OT anyway).

Among the other (display) problems I have are:
Glest can't run - it says it needs GL_ARB_texture_env_crossbar but OpenGL doesn't support it.  I've seen other people having problems with their 945GM's, but the glxinfo they post all have "GL_ARB_texture_env_crossbar".

Sauerbraten works - for some maps.  On some maps, it's smooth and fast-paced.  On other maps, however, it slows to a crawl.  I suspect it can't get enough video memory to load big maps.

Wine won't run - it keeps getting an X Error of failed request: BadAlloc (insufficient resources for operation).  The details are: Major opcode of failed request: 143 (GLX) Minor opcode: 3 (X_GLXCreateContext) Serial number: 17 Current serial number in output stream: 18.  I really, really suspect it can't get enough memory.

In my BIOS setup, video memory is set to 224Mb, but one line on my Xorg.0.log is
(==) I810(0): VideoRAM: 65536 kByte
Also, it mentions something about "Will attempt to tell the BIOS that there is 12288 kB VideoRAM" way before that line.  I don't quite understand that bit.

Anyway, hopefully a driver update will be all that's necessary.  I've heard mention that the latest drivers will need compilation of some stuff, including the kernel; I'm not yet quite 100% sure I can do that...

---

