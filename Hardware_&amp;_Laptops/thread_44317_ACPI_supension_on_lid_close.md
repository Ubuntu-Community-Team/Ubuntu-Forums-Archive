---
title: "ACPI supension on lid close"
date: 2005-06-25
forum: Hardware &amp; Laptops
---

### Post by flan on 2005-06-25
I've got suspend-to-RAM to work on lid close...
simply removed the square brackets (ie. []) from the command
```
event=button[/]lid
``` 
in /etc/acpi/events/lidbtn
so it become
```
event=button/lid
``` 

but for some reason I don't understand now it doesn't work anymore...
if I put the lid down it won't do anything
if I do
```

$ cd /etc/acpi/
/etc/acpi/$ ./sleep.sh


``` 
the script return
```

ifdown: failed to open statefile /etc/network/ifstate: Permission denied
SIOCSIFFLAGS: Permission denied
ifdown: failed to open statefile /etc/network/ifstate: Permission denied
SIOCSIFFLAGS: Permission denied
ioctl(): Operation not permitted
chvt: VT_ACTIVATE: Operation not permitted
open /dev/mem: Permission denied


``` 
what's go wrong?  ](*,)

---

### Post by elsewhere on 2005-06-25
Those are permission errors.  You'll need to use "sudo ./sleep.sh" to activate the sleep script.

When you say it stopped working, is it having any effect when you close the lid or is it just not reacting ?  There may be some logging info in /var/log/acpid as well.

Also, maybe try executing /etc/acpi/lid.sh (with sudo) to see what happens.

Hope this helps...

Cheers,
KV

---

### Post by flan on 2005-06-26
hmm yes, if i do
```
sudo ./sleep.sh
``` 
it sleeps correctly... but it seems not react to lid or sleep button events...
And the bad thing is that I have no idea of what did wrong...

---

### Post by elsewhere on 2005-06-26
Ok, next time you close your lid and open it, type "sudo tail /var/log/acpid" and see if the ACPI log recorded the lid closing / opening event.  That will at least tell you whether the lid event is even being received.

Did you change anything with your startup config ?  Might want to check to make sure acpid and the acpi-scripts are running when you boot.

Cheers,
KV

---

