---
title: "Ubuntu 16.04, OpenGL 4.3 issues, Radeon HD 7450 (Caicos)"
date: 2018-02-23
forum: Hardware
---

### Post by erikstrawn on 2018-02-23
I am running Ubuntu 16.04 with an AMD FX-6300 Six-Core Processor and a Radeon HD 7450 (AMD CAICOS) graphics card.


A friend talked me into installing the UnrealEngine development suite, which requires OpenGL 4.3. I tried to update to OpenGL 4.3, but somewhere I screwed it up.


```

sudo apt-get install ppa-purge && sudo ppa-purge ppa:ubuntu-x-swat/updates
sudo add-apt-repository ppa:oibaf/graphics-drivers
sudo apt-get update

```


I think I wasn't supposed to purge the ubuntu-x-swat ppa.


When I try to run the development suite I get an error saying that OpenGL 4.3 is required.


When I try to play Mordheim (Steam under Wine), the player models don't appear.


I tried to reinstall the ubuntu-x-swat ppa.


```

sudo add-apt-repository ppa:ubuntu-x-swat/updates
sudo apt update && sudo apt dist-upgrade

```


No luck.


I purged the Oibaf ppa.


```

sudo apt-get install ppa-purge && sudo ppa-purge ppa:oibaf/graphics-drivers
sudo apt update && sudo apt dist-upgrade

```


Still no luck.


When I run glxinfo I get the following:


```

~$ glxinfo | grep OpenGL
OpenGL vendor string: X.Org
OpenGL renderer string: AMD CAICOS (DRM 2.50.0 / 4.13.0-36-generic, LLVM 6.0.0)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 18.1.0-devel
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 18.1.0-devel
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 18.1.0-devel
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
OpenGL ES profile extensions:

```



My first goal is to un-dork my drivers so I can play Mordheim again. My second goal is to be able to use the UnrealEngine development suite. Where do I go from here?

---

### Post by Yellow Pasque on 2018-02-24
"At the moment OpenGL 4.x with R600g is only advertised for Radeon HD 5800 and HD 6900 series graphics cards. Other hardware at the moment is limited to OpenGL 3.3 due to not having ARB_gpu_shader_fp64 support."
-- [https://www.phoronix.com/scan.php?page=news_item&px=R600g-Almost-At-OpenGL-4.5](https://www.phoronix.com/scan.php?page=news_item&px=R600g-Almost-At-OpenGL-4.5)

You can try overriding the version manually, but no guarantees it works:
```
MESA_GL_VERSION_OVERRIDE=4.3 MESA_GLSL_VERSION_OVERRIDE=430 programname
```

---

### Post by erikstrawn on 2018-02-24
Ugh, but thanks. I'd read a listing elsewhere that said it was good. Unverified information on the internet strikes again!

Any idea on how to un-break my current drivers so I can play more Mordheim? Uninstalling oibaf didn't fix it.

What file would I put the manual override into if I wanted to try it?

---

### Post by Yellow Pasque on 2018-02-24
> Any idea on how to un-break my current drivers so I can play more Mordheim? Uninstalling oibaf didn't fix it.
"Mesa 18.1.0-devel" means you still have some 3rd-party/PPA version installed.

> What file would I put the manual override into if I wanted to try it? 
No, you would type it in the command line, substituting the name of your program for "programname".
Example:
```
MESA_GL_VERSION_OVERRIDE=4.3 MESA_GLSL_VERSION_OVERRIDE=430 glxinfo | grep OpenGL
```

---

