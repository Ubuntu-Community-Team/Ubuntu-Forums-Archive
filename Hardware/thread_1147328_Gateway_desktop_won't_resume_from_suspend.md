---
title: "Gateway desktop won't resume from suspend"
date: 2009-05-03
forum: Hardware
---

### Post by nbtrap on 2009-05-03
I'm running 9.04 on a Gateway FX and the machine won't resume from suspend in Ubuntu (but will in Windows). It wouldn't work in 8.10 either, but it DID work in 8.04. When I try to resume, it hangs at a blank screen with a blinking cursor in the top left corner and doesn't move from there. Here is my xorg.conf:

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
EndSection

Section "Module"
Load "glx"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
Option "NoLogo" "True"
EndSection

I'm using nVidia's 180 drivers, but it still didn't work when I was using the 173. Any ideas?

Also, I'm not very computer savvy. Please be specific.

---

### Post by mikedep333 on 2009-05-03
Well, for the sake of troubleshooting you could try reverting to the open-source default nv driver. That way we'll know if its the nvidia driver or not.

You can do that from the hardware drivers app (system > administration > hardware drivers.)

---

### Post by nbtrap on 2009-05-03
After disabling the graphics drivers, the problem persists but in a different way.

Before, after attempting to wake the machine, my monitor would hang on a blank screen with a flashing cursor. Now, having disabled the graphics drivers, the monitor itself won't even wake up from suspend, even though the machine sounds like it's doing work.

---

### Post by nbtrap on 2009-05-03
Bump.

---

### Post by nbtrap on 2009-05-03
Bump. Someone please help. This is my second thread on this.

---

### Post by mikedep333 on 2009-05-04
You don't have some sort of issue with the monitor looking for a signal on a different video input, do you?

---

### Post by nbtrap on 2009-05-04
I wouldn't know how to tell exactly, but I'd say almost for sure "no". It definitely seems to be a problem with the computer.

---

### Post by mikedep333 on 2009-05-04
Well, it sounds like your motherboard is not compatible with ubuntu going into standby.

That or it doesn't like one of the piece of the other pieces of hardware on your computer for standby.

You can try unplugging everything unnecessary from your computer and seeing if standby works.

Or we can look through log files, which will be a lot of work.

---

