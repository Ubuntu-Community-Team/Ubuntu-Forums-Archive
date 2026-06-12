---
title: "I still have no sound"
date: 2008-08-01
forum: General Help
---

### Post by majikhotline on 2008-08-01
can anyone help

can anyone post their solutions.

i did a clean install 8.04 and havent had sound since, when i had Ubuntu 7.0.4 (Feisty Fawn) everything worked fine.

i did the   Comprehensive Sound Problem Solutions Guide and still have no luck.

what can i do now?

---

### Post by iaculallad on 2008-08-01
Post your audio card model:

```
lspci | grep audio
```

---

### Post by majikhotline on 2008-08-01
```
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

```

also i used aplay -l and i got 
```
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

---

### Post by iaculallad on 2008-08-01
Try if this method works: Drop to your terminal and input the following codes:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

and find the "**options snd-intel8x0 index=-2**" and set it to "**=0**"

Save and close the file.

```
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

```

Reboot your computer:

```
sudo shutdown -r now
```

---

### Post by majikhotline on 2008-08-05
i did all the commands successfully and rebooted....no sound

any other suggestions?

---

