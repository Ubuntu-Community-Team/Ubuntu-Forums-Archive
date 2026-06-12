---
title: "X11 keys"
date: 2014-04-28
forum: Hardware
---

### Post by dhlii on 2014-04-28
I am setting up an HP dv7t-6c00 laptop, and it apears that fn-F# and F# are swapped for all Function keys

i.e. if I hit F2/F3 I get bright/dim and fnF2/fnF3 gives me the normal F2/F2

How can I fix this ?

Do I try to change this with xmodmap
or changes in /lib/uved/hwd.b/60-keyboard.hwdb

or ....

---

### Post by m_duck on 2014-04-29
My first idea would be to take a look at the BIOS settings for that laptop. I have a Dell which has a BIOS option of how to consider the function keys, the two settings being "normal" function keys (with media etc. functions when pressing **fn** first) and the other setting being the reverse of this.

---

### Post by dhlii on 2014-04-29
Thanks that did the trick.

---

