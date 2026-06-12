---
title: "Ubuntu installation fails (Ubiquity)"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by kjarli on 2009-11-02
First of all, each file check fails on 1 file. Doesn't tell me which file though.
After that, I've tried the install. First of all, it takes ages to load everything, but so far so good, except for some I/O errors after the grey pixelated flashing ubuntu icon. After the UI finally loaded (after a long black screen), I get 1 or 2 Desklet Errors (if I'm correct, could be applet aswell). Than I've tried clicking Install Ubuntu 9.10, but nothing happens.
```

Running: ubiquity --desktop %k gtk_ui
(as the icon does) gives me: 'import site' failed; use -v for traceback

Running: ubiquity --desktop
gives me the above message + 
Traceback (most recent call last):
  File "usr/bin/ubiquity", line 135, in <module>
    main()
  File "usr/bin/ubiquity", line 24, in main
    desktop = sys.argv[i + 1]
IndexError: list index out of range

```
What can I do to fix it? md5 sums are correct. I've had a similar file error with the last beta a few days ago, though thatone atleast gave me the install..

---

