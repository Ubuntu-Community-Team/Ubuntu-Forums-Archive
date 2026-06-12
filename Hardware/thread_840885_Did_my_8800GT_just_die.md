---
title: "Did my 8800GT just die?"
date: 2008-06-25
forum: Hardware
---

### Post by imnotryan on 2008-06-25
So yesterday, after 3 flawless months, it started this game where it freezes for no reason, even when just leaving it alone.

When it starts up, the BIOS splash screen has black dots arranged in a pattern all over it. Video artifacts I guess? Than he GRUB menu has all my options as usual, except that when you highlight the options - some of the characters are green... Like "Ub[COLOR="Lime"]un[/COLOR]tu 8.0[COLOR="Lime"]4[/COLOR] H[COLOR="Lime"]ard[/COLOR]y He[COLOR="Lime"]r[/COLOR]on" and Mic[COLOR="Lime"]ro[/COLOR]soft W[COLOR="Lime"]i[/COLOR]nd[COLOR="Lime"]o[/COLOR]ws X[COLOR="Lime"]P[/COLOR]" Only when the option is highlighted, though.

Once selected EITHER OS's loading screen will have those dots from the BIOS splash screen, arranged in the same pattern, except green instead of black. Halfway through the loading process - the 8800GT's fan will spin back up to full speed (spools down after BIOS typically) and the computer will restart itself.

Yesterday the problem went away after a few reboots. Today only Windows XP SAFE MODE will start and run. So the computer is basically unusable for now.

The BIOS splash screen does the same thing with both of the HDD's unplugged... So I'm fairly certain this can't be a software issue.

Should i try and get EVGA to replace it? Could I do this? Would it help? Bought it off newegg.com a few months ago.

---

### Post by Sef on 2008-06-25
> Should i try and get EVGA to replace it? Could I do this? Would it help? Bought it off newegg.com a few months ago.

Have you booted with a Live CD to see if the same problem happens or not?

---

### Post by imnotryan on 2008-06-26
> **Sef said:**
> Have you booted with a Live CD to see if the same problem happens or not?

It will not boot from a live CD.

---

### Post by Arkenklo on 2008-06-26
I suspect that your problem is a faulty graphics-card, but it could justa as well be anything from the PSU to the RAM. Start with unplugging any non-critical parts, as the CD, HDD and PCI-cards. Then try replacing one part at a time, starting with the 8800GT, then RAM, PSU, CPU and lastly motherboard. Also, if you have multiple RAM sticks, try unplugging all but one.

Hope that will help =)

//Arkenklo

---

### Post by ukripper on 2008-06-26
Take your nvidia card out and enable onboard Graphics card in BIOS and then see if problem persists and post here the result.

---

### Post by imnotryan on 2008-06-26
My MB doesn't have onboard video.  I don't have any new style ram chips, or another MB that accepts PCI-E... So I can't test any parts of the setup outside of one another.

---

### Post by ukripper on 2008-06-27
> **imnotryan said:**
> My MB doesn't have onboard video.  I don't have any new style ram chips, or another MB that accepts PCI-E... So I can't test any parts of the setup outside of one another.

ok can you look in below logs and post anything related to **EE** are errors or **WW** are warnings from
var/log/messages:

```
cat /var/log/messages
```

---

