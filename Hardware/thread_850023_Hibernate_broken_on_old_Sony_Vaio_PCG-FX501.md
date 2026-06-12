---
title: "Hibernate broken on old Sony Vaio PCG-FX501"
date: 2008-07-05
forum: Hardware
---

### Post by perce on 2008-07-05
I've just installed Xubuntu Hardy on an old Sony Vaio PCG-FX501. It hibernates, but resume hangs without any error message when you'd expect X to start. I've tried to kill gdm and then reboot, but nothing changes. Hibernate used to work on Ubuntu feisty, I don't know with Gutsy because I skipped it.

---

### Post by perce on 2008-07-17
The last message before hanging was:
```

suspending console(s)

```

Following some advise found on the LKML I added the line"
```

no_console_suspend

```
to the kernel line in grub. Now resume goes a little further, but hangs at:
```

Disabling non-boot CPUs

```

The strange thing is that it is an old laptop with only one CPU.
I'm using the kernel:
```

2.6.24-19-generic SMP
```
Is there a way to boot a non SMP kernel, just to try?

---

