---
title: "HP pavilion DV6534ea mute led (Ubuntu 8.10)"
date: 2008-11-25
forum: Hardware
---

### Post by ikr on 2008-11-25
Hey!

I have a problem with my laptop HP pavilion DV6534ea. The mute led doesn't work. The mute itself works but the led doesn't change color and stays blue. I need this function workable. :(
my soundcard card is

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

Appreciate any suggestion.

---

### Post by ikr on 2008-11-27
bump :confused:

---

### Post by ikr on 2008-11-28
bump

---

### Post by jazzgossen on 2009-06-04
It's the same on my dv5 pavilion, so this behaviour is probably normal under Ubuntu. I don't have a fix though. (On a side note, I wish there were a way to dim or turn off the leds completely...)

---

### Post by gigahz on 2010-01-29
> **jazzgossen said:**
> It's the same on my dv5 pavilion, so this behaviour is probably normal under Ubuntu. I don't have a fix though. (On a side note, I wish there were a way to dim or turn off the leds completely...)

Hi did you resolve the LED dim issue? And in other operating systems, is the mute led changing color on mute? Is LED dimming possible in say for example Windows?

---

### Post by jazzgossen on 2010-02-01
No, LED dimming is not possible in other systems, so that's a hardware thing.

The mute LED, however, does turn red when sound is muted on Windows Vista, but not in Ubuntu.

---

### Post by gigahz on 2010-02-01
> **jazzgossen said:**
> No, LED dimming is not possible in other systems, so that's a hardware thing.

The mute LED, however, does turn red when sound is muted on Windows Vista, but not in Ubuntu.

Yeah, so it seemed the LEDs are hardwired.

For the mute LED color change I saw a post somewhere that someone had fixed the driver, I think the red color is wired to a GPIO#3 pin on a chip in there somewhere... Maybe with time it's fixed.

---

