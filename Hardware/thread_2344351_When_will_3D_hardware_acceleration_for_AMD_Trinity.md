---
title: "When will 3D hardware acceleration for AMD Trinity APU / HD 75x0D return"
date: 2016-11-24
forum: Hardware
---

### Post by superian on 2016-11-24
With the loss of being able to use the AMD fglrx drivers, graphics performance for these has fallen off a cliff because they're now using software rendering.  It doesn't look like the AMDGPU PRO drivers support this 2012 chipset either.  They're delightful chips - I can run an assortment of things at full screen in high quality with Windows and used to be able to do the same with Ubuntu - but when are they going to work properly under Ubuntu again?

---

### Post by QIII on 2016-11-24
At this point one can say only that they will work only through 14.04.1, as more recent releases use an X Server and graphics stack that fglrx will not work with.

AMD is working very hard with open source developers (well, er, Canonical mostly) to produce even better versions of the Radeon driver for non-GCN architecture GPUs such as yours.

AMD is doing what the open source community has been asking for for years:  creating a genuinely functional open source driver environment.  But this is the pain we're all going to have to bear with.

---

### Post by Yellow Pasque on 2016-11-25
It should work just fine with open source radeon driver on Ubuntu 16.04.x, unless there's some bug specific to Trinity APU's I'm not aware of. Maybe the 3D performance won't be quite as good as fglrx, but you shouldn't be stuck with software rendering. Do you get software rendering "out of the box" (or on LiveUSB)? I suspect you've been mucking about with fglrx and/or other video drivers and screwed something up on your install.

---

### Post by superian on 2016-11-26
That's interesting - it's not software rendering then. (Thank you for the suggestion.)

Hmm, my memory is there's been a fresh install of the / partition since we lost the ability to use fglrx, while retaining the /home one.  

Is this 'delete configuration files somewhere and it'll work out new defaults on next boot' time and if so, which?

---

### Post by superian on 2016-11-26
"OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD ARUBA (DRM 2.46.0 / 4.8.0-22-generic, LLVM 3.8.1)
OpenGL core profile version string: 4.1 (Core Profile) Mesa 12.0.3"

---

### Post by superian on 2016-11-26
I can't get one downloaded benchmark to run, but the score on glmark2 increased by a factor of six. The terrain test was particularly appalling on software rendering...

---

### Post by Yellow Pasque on 2016-11-26
So is this solved then? The benchmark that fails to run may require OpenGL > 4.1, which would require you to use a PPA with updated graphics packages. I'm just guessing on that though.

---

### Post by superian on 2016-11-26
Ah ha, I have been using (had to use) nomodeset on the grub command line when booting.

Changing this to radeon.modeset=1 means I get at least some hardware acceleration back.

---

