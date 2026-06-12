---
title: "Serial port printer"
date: 2012-10-09
forum: Hardware
---

### Post by DimiOrla on 2012-10-09
Hi everyone,

The port does not show up in CUPS
after I give permission to the port (chmod 777 /dev/ttyS0)
it shows up but after a reboot not any more.
I tried to make it permanent by adding the user in uucp, with no luck
then added the line
KERNEL=="ttyS[0-9]*", NAME="tts/%n", SYMLINK+="%k", GROUP="uucp", MODE="0777"
in /etc/udev/rules.d/90-local.rules and my system froze up.

I use Lubuntu 12.04

Thanks in advance,
Dimitris

---

### Post by DimiOrla on 2012-10-09
The solution was making file
/etc/udev/rules.d/40-permissions.rules
and adding line
KERNEL=="ttyS[0-9]", GROUP="dialout", MODE="0777"
and adding user to the dialout group.

I don't know if it is best practice to open the port like this.
Please let me know if their is another solution.

Solution was found in this post
[http://ubuntuforums.org/showthread.php?t=782115&highlight=ttyS0+permission]("http://ubuntuforums.org/showthread.php?t=782115&highlight=ttyS0+permission")

---

