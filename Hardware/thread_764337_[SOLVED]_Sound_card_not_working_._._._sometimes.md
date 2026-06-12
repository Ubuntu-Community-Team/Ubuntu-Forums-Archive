---
title: "[SOLVED] Sound card not working . . . sometimes"
date: 2008-04-23
forum: Hardware
---

### Post by yeats on 2008-04-23
I recently acquired an Acer Aspire 2010 laptop and installed Gutsy on it.  The sound card was working fine with the live CD and then when I first installed Ubuntu.  I did a "medibuntu" install of several drivers to allow DVD playback and since then my sound card is not working consistently.  What happens is that it is either recognized when I boot, in which case it works fine, or it is not recognized when I boot, in which case it does not work at all.

Here's the "aplay -l" when the card is working:

```
chris@chris-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chris@chris-laptop:~$ 
```

Of course, when it's not working, it says that no sound cards are installed.

Here's the "lspci -v" when the card is working:

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0061
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at e100 [size=256]
        I/O ports at e200 [size=64]
        Memory at f0080400 (32-bit, non-prefetchable) [size=512]
        Memory at f0080600 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
```

and when it's not working:

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0061
        Flags: medium devsel, IRQ 17
        I/O ports at e100 [size=256]
        I/O ports at e200 [size=64]
        Memory at f0080400 (32-bit, non-prefetchable) [size=512]
        Memory at f0080600 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
```

I've noticed that the "Flags" field lists different output in each case.

I've followed the general sound card troubleshooting on the Ubuntu wiki to no avail.  Any suggestions?

Thanks!

---

### Post by yeats on 2008-04-26
I know everyone's excited about Hardy, so I understand :), but can anybody help me here?

I'll mention that I upgraded my laptop to Hardy in hopes that the sound card problem would be resolved - but no luck.  When the sound card is recognized, no problems at all.  When it's not recognized - nada.

---

### Post by yeats on 2008-04-26
Is there anybody out there?:confused:

---

### Post by yeats on 2008-04-28
bump

---

### Post by Ben325e on 2008-04-28
Not dual booting, are you?  Sometimes if I mute my windows session, and then boot back into ubuntu I can't get any audio but the system beep.  I have to go back and unmute in windows before having sound in ubuntu.  Sucks.

Good luck,

Ben

---

### Post by yeats on 2008-04-29
No, this is a single installation laptop, though I have a dual boot on my desktop and it works just fine.  Thanks for the answer, though.

---

### Post by dbcoolio on 2008-07-19
I have this same problem.  I got it working in gutsy, I think it was something to do with the onboard modem getting confused with the soundcard, though after I blacklisted my modem this time it didn't solve the issue.

---

