---
title: "Compaq/HP nw8440 flashing screen/lock when lid closed"
date: 2010-10-03
forum: Hardware
---

### Post by nc_jed on 2010-10-03
I swear I ran across a thread here but have given up trying to locate it.  

My situation is this, when I close the lid on my laptop once, and open it back after a while, everything is fine.  It wakes up normally.  System is set to 'suspend' on lid closure (on battery and 'blank screen' when on AC).  Doesn't matter, happens either way.

Now, the funny thing is, when it is closed a second time, problems start.  Typically when I open it back up, it'll be mostly black with a 1/2" or so of space at the bottom flashing some blocky, pixelated, VGA color sprites.  Normally, I have to turn it off/on and everything is fine (until I close the lid a second time).  I think I read somewhere this was an issue with Xorg.config.  Any ideas?

This is the model with the ATI FireGL 5200 chip.  lspci is attached.

THANKS!!!

- jed

---

### Post by nc_jed on 2010-10-05
bump.

---

### Post by nc_jed on 2010-10-07
bump

---

### Post by nc_jed on 2011-02-02
Resolved by installing Lucid.  Powersave works beautifully.

---

