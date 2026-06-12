---
title: "[SOLVED] Turn off the LCD display on a laptop"
date: 2008-08-16
forum: General Help
---

### Post by FFighter on 2008-08-16
Hello,

I've got a HP dv6448SE running Ubuntu Hardy (8.04). I usually let it always on, since it is also my main workstation. However, in order to preserve its LCD display and to save energy, I would like to know how I explicitly tell it to turn its LCD display off. I know I can suspend or hibernate, but sometimes you just want to leave it on but still turn off the LCD, does anyone know if it is possible to do it?

Thanks in advance,

Marcelo.

---

### Post by bingoUV on 2008-08-16
Alt-F2, and type this in
```

xset dpms force off

```

The following will make the display go off after 200 seconds of inactivity:
```

xset dpms  200 200 200

```

---

### Post by jualin on 2008-08-16
Check under Power Management found on System, Preferences. And adjust the Display settings on AC power or battery.

---

### Post by kerry_s on 2008-08-16
i make a launcher. see pic

---

### Post by Rayaz on 2008-08-16
What about lock screen from the log off menu? Doesn't it do the same thing?

---

### Post by linuxisfree on 2008-08-16
> **Rayaz said:**
> What about lock screen from the log off menu? Doesn't it do the same thing?

It does. It's what i use myself.

---

### Post by FFighter on 2008-08-16
> **linuxisfree said:**
> It does. It's what i use myself.

I don't think it turns the LCD off. Instead, it just "blanks" the screen (makes it all black).

---

### Post by linuxisfree on 2008-08-16
> **FFighter said:**
> I don't think it turns the LCD off. Instead, it just "blanks" the screen (makes it all black).

Ah, i see... my bad.

---

