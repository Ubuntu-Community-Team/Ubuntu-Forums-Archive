---
title: "The eject -T command doesn't work"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by akudewan on 2007-04-17
I was looking for an easy way to eject and close the tray of my DVD drive. Looking in the man page, I found the -T argument.
> 
       -T   With this option the drive is given a CD-ROM tray close command if it’s opened, and a CD-ROM tray eject command if it’s closed. Not all devices support this command, because it uses the above CD-ROM tray close  command.


However when I use this command, I get an error saying: ```
ioctl: Input/output error
```

The -t argument closes the tray normally. Why is the -T argument not working? Can anyone help?

---

### Post by akudewan on 2007-04-22
*bump*

---

### Post by yabbadabbadont on 2007-04-22
> Not all devices support this command
Even though your drive appears to suppor the close command, it must not support the ioctl required for the open command.  Just as a test, try running the open command both with and without a disc in the tray.  It would be interesting if it works one way and not the other.

---

### Post by squirrelpimp on 2007-04-27
I have the same problem with feisty. I can still eject the drive and get this error only when i try to close it using eject -T. Closing the drive using eject -t does work however.

It all worked when i was using dapper and edgy. :)

Greetings from Germany
Lars

---

### Post by akudewan on 2007-04-28
> **yabbadabbadont said:**
> Even though your drive appears to suppor the close command, it must not support the ioctl required for the open command.  Just as a test, try running the open command both with and without a disc in the tray.  It would be interesting if it works one way and not the other.

I tried that. It doesn't work either way, with or without a disc

---

