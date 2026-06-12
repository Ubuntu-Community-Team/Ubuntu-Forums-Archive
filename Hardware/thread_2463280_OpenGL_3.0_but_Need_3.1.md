---
title: "OpenGL 3.0 but Need 3.1"
date: 2021-06-07
forum: Hardware
---

### Post by rebeltaz on 2021-06-07
I am trying to run Sketchup 2020 under wine under Ubuntu 18.04. It tells me:

```
- Your "Mesa DRI Intel(R) HD Graphics 5500 (BDW GT2)" graphics card's OpenGL version is 3.0. SketchUp requires a graphics card that supports OpenGL 3.1 or better.
```

When I run < glxinfo | grep "OpenGL" > I get:

```

OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 5500 (BDW GT2)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 20.0.8
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 20.0.8
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 20.0.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
OpenGL ES profile extensions:

```

Is there anyway to get the correct drivers for this to run?

---

### Post by Yellow Pasque on 2021-06-08
For some reason, the program insists on using OpenGL compatibility profile instead of core profile. You can try faking it:

```
MESA_GL_VERSION_OVERRIDE=3.1COMPAT wine <path to sketchup.exe>
```

---

### Post by rebeltaz on 2021-06-08
> **Yellow Pasque said:**
> For some reason, the program insists on using OpenGL compatibility profile instead of core profile. You can try faking it:

```
MESA_GL_VERSION_OVERRIDE=3.1COMPAT wine <path to sketchup.exe>
```

Thank you! That worked great. I never would have figured that out on my own.

EDIT: Or rather I might say, that worked great when I ran it from the terminal. When I run the same command from a Menu launcher (using the main menu gui editor) it still gives me that same error. Odd, but I can work around that. Anyway... I appreciate it!

---

### Post by Yellow Pasque on 2021-06-09
You're welcome. Assuming a one user system, you can make it permanent:
```
echo "export MESA_GL_VERSION_OVERRIDE=3.1COMPAT" | tee -a ~/.bashrc
```

---

### Post by rebeltaz on 2021-06-09
Oh ok... cool. I just made a script that ran the command, but that is good to know I will probably do that.

---

### Post by Yellow Pasque on 2021-06-09
On second thought, it's probably not a good idea to do that, as it may affect other programs depending on how they check the OpenGL version.
I'm sorry if it caused you any problems. But all you have to do is edit ~/.bashrc and remove the 'export MESA_GL_VERSION_OVERRIDE=3.1COMPAT' line at the end of the file.

EDIT: Oh , and, for reference: [https://docs.mesa3d.org/envvars.html](https://docs.mesa3d.org/envvars.html)

---

### Post by CatKiller on 2021-06-09
> **rebeltaz said:**
> When I run the same command from a Menu launcher (using the main menu gui editor) it still gives me that same error.

In a menu entry you'd probably want to use ```
env MESA_<blah...>
```

---

