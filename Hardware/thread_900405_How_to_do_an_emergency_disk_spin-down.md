---
title: "How to do an emergency disk spin-down?"
date: 2008-08-25
forum: Hardware
---

### Post by zoubidoo on 2008-08-25
The builders next door suddenly started heavy drilling and my desktop was taking some serious vibrations.  What's the best thing to do and is there a gui or an applet?

I found hdparm:
```

       -y     Force an IDE drive to immediately enter the low power consumption standby mode, usually causing it to  spin
              down.  The current power mode status can be checked using the -C flag.

```
But after the -C check said  "drive state is:  active/idle"
```

       -Y     Force  an  IDE  drive to immediately enter the lowest power consumption sleep mode, causing it to shut down
              completely.  A hard or soft reset is required before the drive can be accessed again (the Linux IDE  driver
              will  automatically  handle  issuing a reset if/when needed).  The current power mode status can be checked
              using the -C flag.

```
-Y seems more determined, but if there's no way to spin-up won't that result in data loss and disk corruption especially if apps haven't saved data?

Thanks for any suggestions,
Z.

---

### Post by mrtomservo on 2008-08-25
If you are concerned about the vibration, I think your best bet would be to place your desktop on some sort of foam mat.  Think egg crate or something of the like, just don't block the vents.

---

### Post by zoubidoo on 2008-08-25
> **mrtomservo said:**
> If you are concerned about the vibration, I think your best bet would be to place your desktop on some sort of foam mat.  Think egg crate or something of the like, just don't block the vents.

Thanks for the reply. My question is really for emergency situations.  If I know there are going to be significant vibrations I'm just going to switch off and work from elsewhere.

Z.

---

### Post by Too Late on 2008-08-25
> **zoubidoo said:**
> ```

       -Y     Force  an  IDE  drive to immediately enter the lowest power consumption sleep mode, causing it to shut down
              completely.  A hard or soft reset is required before the drive can be accessed again [b](the Linux IDE  driver
              will  automatically  handle  issuing a reset if/when needed)[/b].  The current power mode status can be checked
              using the -C flag.

```
-Y seems more determined, but if there's no way to spin-up won't that result in data loss and disk corruption especially if apps haven't saved data?
If I remember right, Linux can spin-up the disc which has been turned off with the -Y option. In fact, it was a small problem for me sometimes, since there's no way to completely shut down the drive. (Of course, unmounting will particularly prevent any access to that drive, so it would stay sleeping, but it could still spin-up during the shutdown process for some reason).

I don't know about data loss or disk corrpution, it's a good question.

---

