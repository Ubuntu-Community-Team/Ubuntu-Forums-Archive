---
title: "pipe into clipboard (copy buffer)"
date: 2008-07-15
forum: General Help
---

### Post by PGScooter on 2008-07-15
Hi, is there a way to pipe the output of a command into the buffer from which I can paste (say, into firefox) with ctrl-v?

I know that there are some clipboard managers out there, but I don't think that this is what I'm looking for. Maybe it is though.

thanks

---

### Post by sdennie on 2008-07-15
You could use xclip.  However, I think that rather than pasting with Ctl-V you'll have to paste with the middle mouse button (sometimes emulated as pressing both keys at the same time).

```

sudo apt-get install xclip
ls | xclip

```

---

### Post by PGScooter on 2008-07-16
thanks vor, that's exactly what I'm looking for

---

