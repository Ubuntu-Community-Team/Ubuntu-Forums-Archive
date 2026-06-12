---
title: "LG x110 screen resolution serious problem"
date: 2008-12-12
forum: Hardware
---

### Post by scf! on 2008-12-12
Hello,

I'm trying to set a virtual desktop resolution to my machine.

The display can shox 1024x600 but some programs, like gpsdrive need more!

So I changed my xorg.conf like
```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        SubSection      "Display"
                Depth   24
                Modes   "1024x768" "1024x600"
                Virtual 1024 768
        EndSubSection
EndSection

```

But I can't select the desired virtual resolution.
I can't get it to work.

Running Ubuntu 8.10

Any help would be so welcome!

Thanks in advance!

---

### Post by scf! on 2008-12-12
Any help, I tried these links:

[http://ubuntuforums.org/showthread.php?t=1003722]("http://ubuntuforums.org/showthread.php?t=1003722")

and searched the forum.

...

---

