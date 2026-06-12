---
title: "[SOLVED] Sound doesn't play anymore"
date: 2008-08-13
forum: Hardware
---

### Post by Rommidze on 2008-08-13
Hi all! Today my soundcard stopped to produce any sounds. A have tryed to boot from livecd but with no effect. I have checked dmesg and found no error messages. Card is listed by lspci. I have also checked levels in alsamixer. All sound applications just work without errors but I hear nothing.

---

### Post by lwhitmore on 2008-08-13
If you navigate to ...

[System -> Preferences -> Sound]

... does specifying the sound driver/system manually help?

If you plug in headphones, do you get any sound output?

Luke

---

### Post by hessiess on 2008-08-13
> A have tryed to boot from livecd but with no effect

So sound wont work off a live cd? have you checked obvious thinks like a plug fallen out, or forgetting to turn your amp on :lolflag:

run 
```

alsamixer
```

is anything muted?

---

### Post by Rommidze on 2008-08-13
> **lwhitmore said:**
> If you navigate to ...

[System -> Preferences -> Sound]

... does specifying the sound driver/system manually help?

No, it doesn't help. Tryed each from the list.

> **lwhitmore said:**
> If you plug in headphones, do you get any sound output?

No sound. Just hear the slap which confirms that headphones received some power.

---

### Post by Rommidze on 2008-08-13
> **hessiess said:**
> So sound wont work off a live cd? have you checked obvious thinks like a plug fallen out, or forgetting to turn your amp on :lolflag:

run 
```

alsamixer
```

is anything muted?

It doesn't work from livecd. I've checked alsamixer. And there is no sound neither on embedded speakers nor on headphones. I believe that reason could be trivial but havent found it yet.

---

### Post by Rommidze on 2008-08-13
:guitar:

Got it! I've plugged my mic into the output and tryed to use the input for headphones.

Thanx for participation!

---

