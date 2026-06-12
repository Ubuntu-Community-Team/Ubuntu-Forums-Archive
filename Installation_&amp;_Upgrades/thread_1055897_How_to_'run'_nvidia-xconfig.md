---
title: "How to 'run' nvidia-xconfig"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by errolgreer on 2009-01-31
I am trying to set up dual screens with the Nvidia GS 7600. when I run 
'sudo nvidia-settings' I am told that I am not using the Nvidia x driver and to 'run nvidia-xconfig and restart the server' How do I 'run' something ? - Ubuntu novice !!

---

### Post by mikewhatever on 2009-01-31
Well, <sudo nvidia-xconfig> is the way to run it. Do note that nvidia-xconfig is not the same as nvidia-settings. Another thing worth mentioning, is that you probably need to install the nvidia-xconfig package, to get something useful out of running nvidia-xconfig.

---

### Post by errolgreer on 2009-01-31
I have installed and run nvidia-xconfig seemingly correctly but how do I now
'restart x server' ?? as I still have the same response if I run nvidia-settings.

---

### Post by mikewhatever on 2009-01-31
There is a very easy way to restart xserver, just hit alt+ctrl+backspace. As for the driver not being in use, the question is whether or not you installed the driver? What version of Ubuntu do you use?

---

