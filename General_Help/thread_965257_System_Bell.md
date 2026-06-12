---
title: "System Bell"
date: 2008-10-31
forum: General Help
---

### Post by talonstriker on 2008-10-31
I'm sick of gnome's overuse of the system bell.  How do I "turn off" the system bell?
I hope you can do this in gnome (recent convert from KDE)

---

### Post by snova on 2008-10-31
> **talonstriker said:**
> I'm sick of gnome's overuse of the system bell.  How do I "turn off" the system bell?

Try System->Preferences->Sound, in the Sounds tab, try unchecking some of the boxes.

If that doesn't work, add this line to /etc/modprobe.d/blacklist:

```
blacklist pcspkr
```

This will prevent loading the kernel module that makes beeping possible, thus effectively disabling it (with the added benefit that it will work throughout the entire system).

But that change won't take effect until you reboot. So run this command for the time being:

```
sudo rmmod pcspkr
```

And you'll get the same result.

> **talonstriker said:**
> I hope you can do this in gnome (recent convert from KDE)

So am I, though with all likelihood, not permanently.

---

### Post by FuturePilot on 2008-10-31
> **snova said:**
> Try System->Preferences->Sound, in the Sounds tab, try unchecking some of the boxes.



In addition to what snova said the specific one you want to uncheck is the "Play Alert Sound".

But I just ended up blacklisting pcspkr like described above because I would still get beeps sometimes and I can't stand the sound of that beep. It drives me nuts. ](*,)

---

### Post by talonstriker on 2008-10-31
The second method did the trick.  Thanks.

---

