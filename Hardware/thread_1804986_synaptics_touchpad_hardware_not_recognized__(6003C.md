---
title: "synaptics touchpad hardware not recognized  (6003C8)"
date: 2011-07-15
forum: Hardware
---

### Post by simiasota on 2011-07-15
Hello,

I'm facing problems with my brand-new Asus laptop (K53SV).
It has a synaptics touchpad:

```

egrep -i 'synap|alps|etps' /proc/bus/input/devicesN: Name="Synaptics Inc. Composite TouchPad / TrackPoint"
N: Name="Synaptics Inc. Composite TouchPad / TrackPoint"
N: Name="Synaptics Inc. Composite TouchPad / TrackPoint"

```

It supports 2-fingers scrolling and tapping (it works correctly on win7), but the synaptics driver, once loaded, gets unloaded by X:

```

[  8617.203] (EE) Query no Synaptics: 6003C8
[  8617.203] (EE) Synaptics Unable to query/initialize Synaptics hardware.
[  8617.830] (EE) PreInit returned 11 for "Synaptics"

```

gsynaptics package is already installed. Under system->preferences->pointing devices


I followed this thread:
[http://forums.debian.net/viewtopic.php?f=7&t=57107](http://forums.debian.net/viewtopic.php?f=7&t=57107)
in order to get rid of my problems with the double recognition of the hardware, but unfortunately this did not help: synaptics driver is still unloaded during X startup.

Is there anyone who solved the problem?
thank you in advance

---

### Post by Toz on 2011-07-15
There's a whole thread here devoted to this notebook: [http://ubuntuforums.org/showthread.php?t=1791081]("http://ubuntuforums.org/showthread.php?t=1791081"). 
There is information there on how to get the touchpad working.

---

