---
title: "GLSL 3.30 on AMD Card?"
date: 2015-02-09
forum: Hardware
---

### Post by Krystee_Sulosson on 2015-02-09
So I've been searching around like crazy for the last week, trying to find a solution to this issue.  I'm doing development work with C# and OpenGL in MonoDevelop on my lubuntu 14.04.1 laptop.  I keep running into the program saying:

```
GLSL 3.30 is not supported.  Supported versions are 1.10, 1.20, 1.30, and 1.00 ES
```

lspci | grep VGA returns:

```
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250]
```

and glxinfo | grep version returns:

```
server glx version string: 1.4client glx version string: 1.4
GLX version: 1.4
OpenGL core profile version string: 3.1 (Core Profile) Mesa 10.6.0-devel (git-345e8cc 2015-02-08 trusty-oibaf-ppa)
OpenGL core profile shading language version string: 1.40
OpenGL version string: 3.0 Mesa 10.6.0-devel (git-345e8cc 2015-02-08 trusty-oibaf-ppa)
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 10.6.0-devel (git-345e8cc 2015-02-08 trusty-oibaf-ppa)
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00

```

As the above indicates, I have already tried using the oibaf PPA, and only got put at 3.0 Mesa 10.6.0.  Moving my code to run at version 3.0.0 yields the same error that it is not supported, so that doesn't work.  I have seen this thread ( [http://ubuntuforums.org/showthread.php?t=2160054](http://ubuntuforums.org/showthread.php?t=2160054) ) on it being available through a legacy fglrx driver set, but it requires downgrading the X server.  If this was Arch or another distro I was more comfortable with, I'd downgrade in a heartbeat and deal with the ramifications later.  But the buntu family seems to knit everything together tighter, and I don't know how safe that would be, or if there would be a safe way to handle a downgrade, or even if that would supply me with the correct version of GLSL.

So I'm asking, is there a way to get GLSL 3.3.0 running on lubuntu 14.04.1 with a AMD Radeon Mobility HD 4225/4250 since AMD's drop of support for the chipset?  I can provide any info as needed, thanks for the help.

---

### Post by Yellow Pasque on 2015-02-09
It looks like kernel 3.14 bumped the radeon DRM version to 2.37
[https://github.com/torvalds/linux/commit/7c4c62a04a2a80e3feb5d6c97aca1e413b11c790](https://github.com/torvalds/linux/commit/7c4c62a04a2a80e3feb5d6c97aca1e413b11c790)

And having radeon DRM 2.37 should allow GLSL 3.30 on your GPU:
```
/* pre-evergreen geom shaders need newer kernel */
if (rscreen->b.info.drm_minor >= 37)
   return 330;
return 140;
```

---

### Post by Krystee_Sulosson on 2015-02-09
As you posted, I moved my kernel up from 3.13 to 3.14.  I am still receiving the initial error from GLSL:

```
[COLOR=#000000][FONT=Ubuntu Mono]GLSL 3.30 is not supported.  Supported versions are 1.10, 1.20, 1.30, and 1.00 ES[/FONT][/COLOR]
```

glxinfo | grep version reports that I'm using GLSL 3.30 now, though:
```
server glx version string: 1.4client glx version string: 1.4
GLX version: 1.4
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.6.0-devel (git-345e8cc 2015-02-08 trusty-oibaf-ppa)
OpenGL core profile shading language version string: 3.30
OpenGL version string: 3.0 Mesa 10.6.0-devel (git-345e8cc 2015-02-08 trusty-oibaf-ppa)
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 10.6.0-devel (git-345e8cc 2015-02-08 trusty-oibaf-ppa)
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00

```

So I'm still at a loss...

---

### Post by Yellow Pasque on 2015-02-09
Hmm, I think we're reading the error backwards (at least I was). I thought your program was asking for 3.30 when it's actually requesting a lower version. 

> I keep running into the program saying:
I'm not sure what that means. Is it a program you are writing that the check is failing, or is it monodevelop itself? At this point, I think you'll have more luck in a programming forum, especially one where people understand OpenGL core/compatibility contexts. Your system and driver should not be the issue here. It sounds like whatever is producing the error is checking the core profile GLSL version (which was 1.40 on your system before the new kernel and 3.30 now) when it should be checking the compatibility profile version (OpenGL shading language version string: 1.30) if it wants to guarantee that features which were deprecated in GLSL 1.40 are still available.

---

