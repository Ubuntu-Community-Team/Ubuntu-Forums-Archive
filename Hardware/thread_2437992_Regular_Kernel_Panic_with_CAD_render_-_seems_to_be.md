---
title: "Regular Kernel Panic with CAD render - seems to be nouveau video driver linked"
date: 2020-03-04
forum: Hardware
---

### Post by steve234 on 2020-03-04
Good morning,

I am having new issues since running some updates (prompted by the OS) - [see thread here]("https://ubuntuforums.org/showthread.php?t=2437949"). I have two questions (see below).

_*Background:*_

I use online CAD software through a browser (OnShape) which is webGL dependant. From what I understand views in OnShape render client-side (i.e. using my graphics card). Since the update, if I do something taxing in OnShape em crashed (freezes) there is a dmsg log in the above linked thread.

I suspect a video driver issue because: I've just run an update, and the crash (which at first I thought was browser-related) can be reproduced in other browsers.

I'm running Lubuntu 18.04.4 LTS with i3 as my WM.

```
Distributor ID:	UbuntuDescription:	Ubuntu 18.04.4 LTS
Release:	18.04
Codename:	bionic

```

my lspci output shows the nouveau driver seems to be being used.

```
NVIDIA Corporation GT218 [GeForce G210]

Kernel driver in use: nouveau
Kernel modules: nvidiafb, nouveau
```
[CODE]

[I][U]I have two questions:

[/U][/I](1) Has the nouveau drive been recently updated? I can't seem to find version information about it?

(2) If so can I roll it back? I don't really want to mess around with NVIDEA drivers if I can help it, I've been burned in the past.

---

