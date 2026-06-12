---
title: "resurrecting hdd.."
date: 2010-10-19
forum: Hardware
---

### Post by Baldrick_NZ on 2010-10-19
i have an external hdd which, when plugged into any pc, causes the light to show and the hdd motor 2 whirr - but no computer (regardless of o/s) recognises it. so, how can i get it working again properly without loosing the existing data on it? thanks in advance..

---

### Post by Lazaruss on 2010-10-19
plug it in under ubuntu and run ```
lsusb
``` in terminal, post output.

---

### Post by Baldrick_NZ on 2010-10-26
Sorry for the delay...

```
baldrick@baldrick-desktop:~$ lsusb
Bus 005 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 059f:0341 LaCie, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
baldrick@baldrick-desktop:~$ 


```

This is the one:
Bus 001 Device 004: ID 059f:0341 LaCie, Ltd 

Any idea how I can remount it?

Cheers.

---

### Post by tech.kyle on 2010-10-26
Have you tried mount -a? If that doesn't do anything, could we see what mount says?

---

### Post by Baldrick_NZ on 2010-10-28
> **tech.kyle said:**
> Have you tried mount -a? If that doesn't do anything, could we see what mount says?

```
baldrick@baldrick-desktop:~$ sudo mount -a
baldrick@baldrick-desktop:~$ 

```

But nothing else (aside of what I had before) mounts.

---

### Post by coffeecat on 2010-10-28
Here is a thread from someone with a similar problem and the same Lacie drive.

[http://ubuntuforums.org/showthread.php?t=1586206](http://ubuntuforums.org/showthread.php?t=1586206)

Have a look at RJ12's (post #5) suggestion which solved the problem for the OP. If that doesn't do it, see my comment about failing LaCie power supples, although that seems less likely  in your case considering you get lights and whirring.

---

### Post by Baldrick_NZ on 2010-10-28
> **coffeecat said:**
> Here is a thread from someone with a similar problem and the same Lacie drive.

[http://ubuntuforums.org/showthread.php?t=1586206](http://ubuntuforums.org/showthread.php?t=1586206)

Have a look at RJ12's (post #5) suggestion which solved the problem for the OP. If that doesn't do it, see my comment about failing LaCie power supples, although that seems less likely  in your case considering you get lights and whirring.

Nope, didn't help.
It could be that it suffered an unclean removal under windows. I've since tried to reconnect to XP, hoping to revive the drive, but with a failed result.

Thanks for your help though. Any other ideas?

---

### Post by coffeecat on 2010-10-28
> **Baldrick_NZ said:**
>  Any other ideas?

Well - since XP doesn't "see" it as well, there are several variables to consider and exclude in turn:

1 - Filesystem corruption.

2 - Failure of the hard drive - even though it is whirring.

3 - Failure of the Lacie enclosure firmware - it happens.

4 - Failure of the Lacie power supply - that happens often; I've seen it myself. It could be that the power supply is in the process of failing - providing enough power to make it seem as though it is working, but not enough to work properly.

What I would do would be to remove the bare drive from the enclosure to test it, thus eliminating 3 and 4. You could put it in another USB enclosure that you know works, or a docking station. If you have neither of those, check whether the drive is PATA or SATA and see if you can plug it directly into the motherboard of a desktop computer. If SATA you would need a spare SATA header, or if PATA you would have the (slight) complication of needing to attach it to the slave connector on the ribbon cable and making sure the jumper on the drive is set appropriately. Don't forget to attach a spare power connector - of course.

---

