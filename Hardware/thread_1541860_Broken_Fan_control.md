---
title: "Broken Fan control"
date: 2010-07-29
forum: Hardware
---

### Post by Tehut on 2010-07-29
I'm running Kubuntu 10.04 on a desktop pc. Since an update a few days ago, some fan has been constantly powering up and down. The same computer runs nearly silent in windows and also in kubuntu prior to whatever update did this. Does anyone have any idea how to fix this?
Thank you very much.

---

### Post by Tehut on 2010-07-30
Bump.

---

### Post by PresenceofMind on 2010-07-30
Try this and see what you get:

```
sudo pwmconfig

```

---

### Post by Tehut on 2010-07-30
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

Is what I got.

However, I found the source of the problem: A cd I had left inside the drive. Mistook the sound of the cd reading for a fan since I hardly ever use that drive anymore.
Still odd, though, since I wasn't using the cd, so there should have been no need to constantly read from it. Reading persisted as long as kubuntu was running and also after rebooting.

---

### Post by j0eb0b on 2010-07-30
This is an interesting question.  I too, have this problem that does not exist on Windows 7 Pro 32 (dual boot machine).  i am running 32 bit 10.04 on the following hardware.

Gigabyte MA 790X-UDP4P motherboard
AMD 7850 black 2X CPU
4 Gb GSkill 1066b memory 
All the other stuff that you normally find in a machine like this. 

The machine is a mild overclocker but I think the loud fan comes from the CPU fan which seems to be being told to run at max velocity.  FYI the fan never runs at high speed under Windows 7 under similar conditions.

---

