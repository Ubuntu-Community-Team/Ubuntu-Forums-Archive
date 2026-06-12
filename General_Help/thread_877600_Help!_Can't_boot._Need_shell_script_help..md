---
title: "Help! Can't boot. Need shell script help."
date: 2008-08-01
forum: General Help
---

### Post by MountainX on 2008-08-01
SOLVED

I need to implement this shell script, but I don't understand how. Can anyone help?

```

#!/bin/bash
## /etc/swap.cryptokey should be owned by root:root with perms: 0600
exec cat /etc/swap.cryptokey

```

It comes from here:
[http://wejn.org/how-to-make-passwordless-cryptsetup.html](http://wejn.org/how-to-make-passwordless-cryptsetup.html)

The author says:
> You might also note that you can store keys for additional partitions on your (encrypted) root filesystem (in /etc, for instance) and use simple one-line keyscript like above.

That's what I need to do because the "improved" script from [http://tjworld.net/wiki/Linux/Ubuntu/HardyRAID5EncryptedLVM](http://tjworld.net/wiki/Linux/Ubuntu/HardyRAID5EncryptedLVM) has left me unable to boot.

I would appreciate any advice. (I don't know the shell scripting language--yet.)

---

### Post by knightcoder on 2008-08-01
You mean, you want to know how to run it ??

---

### Post by MountainX on 2008-08-01
I would like to know what he means by swap.cryptokey. Is that just a file name for the key file? If so, then I'll simply replace swap.cryptokey with my key file name.

Assuming that's the case, how the heck does it work? It looks like it simply displays (types) the contents of the key file. How does that accomplish the goal? :confused:

---

### Post by MountainX on 2008-08-02
SOLVED

> **MountainX said:**
> I would like to know what he means by swap.cryptokey. Is that just a file name for the key file?

Yes, that was it. I got it working.

I'm using a combination of the two different scripts mentioned in these two articles:

[http://tjworld.net/wiki/Linux/Ubuntu/HardyRAID5EncryptedLVM](http://tjworld.net/wiki/Linux/Ubuntu/HardyRAID5EncryptedLVM)
for the first two encrypted partitions

[http://wejn.org/how-to-make-passwordless-cryptsetup.html](http://wejn.org/how-to-make-passwordless-cryptsetup.html)
short script (1-liner) for the next three encrypted partitions

Got it working :)

---

