---
title: "Laptop hates Edgy"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by remusus on 2006-12-25
After a wonderful experience upgrading from Dapper to Edgy on my personal laptop (HP Pavilion zt3000), I went ahead and updated my dad's Toshiba laptop (off-the-shelf, don't have model # available right at the moment).  BAD call.  The touchpad freaks out now and hibernate does not work properly.

On Dapper I had it set to configure the touchpad on startup with 'qsynaptics -r', and it worked properly.  For some reason this does not work right in Edgy, though it does work if you restart the X server after booting  :confused: 

Hibernate worked perfectly in Dapper, though suspend didn't and I could never work out why.  In Edgy, hibernate hangs for about 15 seconds in text mode with a blinking cursor, then goes back to GNOME.  Once I got it to actually hibernate, but it did not reload the hibernate file on boot.  (yes, suspend still doesn't work, meh)

Any help with either of these problems would be appreciated, I do not want to have to downgrade the computer back to Dapper.  Gack.

---

### Post by pixor on 2007-01-13
I am having the same problem with 'qsynaptics -r' not working when I first login. Indeed, a ctrl-alt-backspace to restart my X session seems to fix things.

Any ideas, folks?

---

