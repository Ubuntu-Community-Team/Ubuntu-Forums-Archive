---
title: "Webcam detected but fails to produce an image"
date: 2020-04-19
forum: Hardware
---

### Post by lashi on 2020-04-19
I'm on Ubuntu Mate 18.04, and I've noticed that my built in webcam fails to work. 

I initially thought it was a hardware error, so I tried another webcam, and to my surprise, that also fails to work. The webcam is detected, and the light on it switches on. 

Output from guvcview: 

> 
GUVCVIEW: version 2.0.5
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
ALSA lib pcm_dsnoop.c:618:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1052:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm.c:2495:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2495:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2495:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm_dmix.c:1052:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
V4L2_CORE: Could not grab image (select timeout): Resource temporarily unavailable
V4L2_CORE: Could not grab image (select timeout): Resource temporarily unavailable
V4L2_CORE: Could not grab image (select timeout): Resource temporarily unavailable
V4L2_CORE: Could not grab image (select timeout): Resource temporarily unavailable


When I look in the kernel logs: 

> 
[    2.565028] usb 2-6: Product: Lenovo EasyCamera
[    8.032908] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (5986:0652)
[    8.053496] uvcvideo 2-6:1.0: Entity type for entity Camera 1 was not initialized!
[    8.053635] input: Lenovo EasyCamera: Lenovo EasyC as /devices/pci0000:00/0000:00:14.0/usb2/2-6/2-6:1.0/input/input15


I also tried booting off a standard USB for both Ubuntu MATE and the normal Ubuntu, but the issue stands.

Anyone have an idea what's going on here? I recall my webcam worked fine in older versions.

Cheers, 

- Lashi

---

