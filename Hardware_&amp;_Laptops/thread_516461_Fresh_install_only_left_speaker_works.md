---
title: "Fresh install only left speaker works"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by somuchfortheafter on 2007-08-03
I installed Ubuntu 7.04 yesterday for the first time on my desktop. In windows the sound was perfectly fine, however in linux I am only getting sound to the left speaker and a few hits out on the sub. I connected my ipod to the system just to make sure the speakers were fine and they passed. I am not exactly sure what kind of soundcard is on the motherboard. Here is the excerpt from the command lspci though.
```

00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

```

any suggestions?

---

### Post by schallstrom on 2007-08-03
I would try and start 'alsamixer'. Maybe the volume settings got messed up for some reason and one channel is muted in the mixer.

---

### Post by Lord Illidan on 2007-08-03
From what I see over here : [http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-intel8x0)

You might need to add a few lines to a file..

So first, let's make a backup of it.

```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.backup
```

So do this in a terminal to open gedit with sudo permissions : ```
gksudo gedit /etc/modprobe.d/alsa-base
```

And copy and paste the following lines at the end of the file.

```
       # ALSA portion
       alias char-major-116 snd
       alias snd-card-0 snd-intel8x0
       # module options should go here
       
       # OSS/Free portion
       alias char-major-14 soundcore
       alias sound-slot-0 snd-card-0
       
       # card #1
       alias sound-service-0-0 snd-mixer-oss
       alias sound-service-0-1 snd-seq-oss
       alias sound-service-0-3 snd-pcm-oss
       alias sound-service-0-8 snd-seq-oss
       alias sound-service-0-12 snd-pcm-oss

```

Let us know how it goes.

---

### Post by somuchfortheafter on 2007-08-03
thanks for the help, I am at work now but I will give it a try when i get home. Hope all goes well and thanks again.

---

