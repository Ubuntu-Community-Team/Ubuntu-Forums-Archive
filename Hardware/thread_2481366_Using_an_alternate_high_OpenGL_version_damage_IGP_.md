---
title: "Using an alternate high OpenGL version damage IGP and video card ?"
date: 2022-11-27
forum: Hardware
---

### Post by aug7744 on 2022-11-27
Hello.

IGP Radeon HD 3000 OpenGL 3.3.

Mesa updated version installed.

When doing
glxinfo | grep OpenGL
was reported using OpenGL 3.0.
However the IGP is 3.3.

Thus I had changed in /etc/environment
MESA_GL_VERSION_OVERRIDE=3.3
MESA_GLSL_VERSION_OVERRIDE=330

Restarting the OS was possible use OpenGL 3.3
Some softwares requiring OpenGL 4.3 not start with IGP Radeon HD 3000.

Well ... I had manually changed the current Mesa environment settings to
MESA_GL_VERSION_OVERRIDE=4.3
MESA_GLSL_VERSION_OVERRIDE=430
Doing
glxinfo | grep OpenGL

OpenGL vendor string: X.Org
OpenGL renderer string: AMD RS780 (DRM 2.50.0 / 6.0.6-060006-generic, LLVM 14.0.6)
OpenGL core profile version string: 4.3 (Core Profile) Mesa 22.2.2 - kisak-mesa PPA
OpenGL core profile shading language version string: 4.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.3 (Compatibility Profile) Mesa 22.2.2 - kisak-mesa PPA
OpenGL shading language version string: 4.30
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 22.2.2 - kisak-mesa PPA
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:

Now softwares requiring OpenGL 4.3 start and works.
However the IGP is OpenGL 3.3.
OpenGL 4.4 is being forced.
Mesa is using an mixed OpenGL 3.3 hardware acceleration and 4.4 in software ?
Using an OpenGL high version than IGP OpenGL hardware version can damage the IGP or video card ?
In logic IGP only change frequency and voltage. OpenGL 4.4 will try to do more processing.
Thanks for reading.

---

