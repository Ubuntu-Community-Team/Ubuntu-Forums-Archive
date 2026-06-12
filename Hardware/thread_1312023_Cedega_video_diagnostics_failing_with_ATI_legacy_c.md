---
title: "Cedega video diagnostics failing with ATI legacy card"
date: 2009-11-02
forum: Hardware
---

### Post by Padakwaak on 2009-11-02
OK, so I have Ubuntu 9.10 x64 installed on my Dell Inspiron 9400 with an ATI x1400 Mobility, which is now classified as Legacy by AMD/ATI.

When I'm trying to do a diagnostic test in Cedega, it fails:```
videocard: error: no direct rendering support detected
videocard: Direct rendering support is required for 3D graphics.
videocard: error: unsupported videocard vendor: DRI R300 Project
videocard: Video cards from either NVIDIA or ATI are recommended.  Other video cards may not have enough hardware or driver support to run games under Cedega.
videocard: failed
```

I'm using the default opensource drivers and OpenGL seems to be working fine for glxgears. Compiz is working fine & video playback too.

Here's some more info:```
$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project
$ glxinfo | grep direct
direct rendering: Yes
```

The reason why I'm not posting on the Cedega forums is because I just have a trial membership and want to get it working before I go and buy it :(

I've tried downgrading my xserver to the version in Intrepid and then to install the Catalyst 9.3 drivers, but I had no success with that either. Probably because the guide was intended for Ubuntu 9.04.

Help in this regard would be appreciated.

---

