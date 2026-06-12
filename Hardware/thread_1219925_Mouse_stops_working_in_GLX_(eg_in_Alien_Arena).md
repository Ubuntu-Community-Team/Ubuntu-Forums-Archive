---
title: "Mouse stops working in GLX (eg: in Alien Arena)"
date: 2009-07-22
forum: Hardware
---

### Post by Jack Fear on 2009-07-22
My mouse work fine normally.  When I start anything that uses OpenGL (eg games), the mice (tried many different kinds) won't move up or down, only left and right.

I am running 64 bit Jaunty with 2 nvidia GPUs.  I do not have any visual effects running (no compiz)

Any help or pointers would be great :)

---

### Post by bryonak on 2009-07-22
A guess: are you running unclutter?

---

### Post by Jack Fear on 2009-07-22
> **bryonak said:**
> A guess: are you running unclutter?

Nope, not even installed.  Thanks though.

---

### Post by Jack Fear on 2009-07-23
Could this be an NVIDIA problem or is it an XORG problem?  I would like to make a bug report but not really sure which is the culprit.

---

### Post by Jack Fear on 2009-07-26
Got some advise that works:

```

export SDL_VIDEO_X11_DGAMOUSE=1

```

---

