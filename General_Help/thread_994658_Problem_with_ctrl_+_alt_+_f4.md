---
title: "Problem with ctrl + alt + f4"
date: 2008-11-27
forum: General Help
---

### Post by EcKstasy on 2008-11-27
When I go into the terminal when typing ctrl + alt + f4, After about 10 minutes, the screen goes blank untill I hit enter, like some sort of screen saver.
Does anyone know how I can disable this?

---

### Post by EcKstasy on 2008-11-27
bump

---

### Post by adult swim on 2008-11-27
edit: i misunderstood your question!  im not sure how to turn that off.

---

### Post by EcKstasy on 2008-11-27
.

---

### Post by mali2297 on 2008-11-27
Run
```

sudo dpkg-reconfigure console-setup

```
and see if you can find some appropriate option to change.

If the above does not help, check out the **setterm** command.
```

man setterm

```

Does the screen turn off completely or is there a hint of a backlight?

---

### Post by EcKstasy on 2008-11-28
Thanks, and yes. the screen goes blank but you can still see its turned on. It's like some sort of screen saver; when I hit enter everything is back to normal. but still is annoying when monitoring system stuff as it goes blank all the time.

I tried to mess around with setterm, and dpkg-reconfigure console-setup, but still no options on how to turn off the screen saver, (And in gnome, I've tried everything in there. but that just disables the screen saver for gdm)

---

### Post by mali2297 on 2008-11-29
Did you try this?
```

setterm -blank 0 -powersave off -powerdown 0

```

---

### Post by EcKstasy on 2009-03-14
> **mali2297 said:**
> Did you try this?
```

setterm -blank 0 -powersave off -powerdown 0

```

I tried that, but I get:
```

-> root@EU ~ $ setterm -blank 0 -powersave off -powerdown 0
cannot (un)set powersave mode
```

Edit: it seems when I do "setterm -blank 0" it works fine. thank you.

---

