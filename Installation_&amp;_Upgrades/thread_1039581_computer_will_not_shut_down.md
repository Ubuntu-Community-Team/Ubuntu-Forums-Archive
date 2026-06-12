---
title: "computer will not shut down"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by birdkathe on 2009-01-14
I posted a few months ago about installing Ubuntu on my new computer. Thanks to the great help I got here I am one of the masses who uses 
acpi=off

I can turn the computer on and restart with no problem however when I try to turn things off I run into error messages from the Network Manager claiming a bus error over and over and over... Until I get tired to looking at the white letters and kill the power.

Don't end up turning off the machine very often but thought that maybe now would be a good time to try to figure this out.

Thoughts?
-Kathe

---

### Post by avtolle on 2009-01-14
Which version of Ubuntu is installed?

---

### Post by avtolle on 2009-01-14
Found this: [http://ubuntuforums.org/showthread.php?t=1039350](http://ubuntuforums.org/showthread.php?t=1039350) Take a look to see if may be applicable.

---

### Post by birdkathe on 2009-01-14
I have vs 8.04 I did run across this post but am afraid I don't really understand the solution well enough to implement it. In particular I'm unsure what is ment by '... adding the two modules to the blacklist'

Things I have tried that don't work:
1) Turn off NetworkManager & NetworkManagerDispatcher using 

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

Results: Hung after 'Will halt now' with a curser in the upper left corner, no error messages.

2) add 'amp=power_off' to the boot command
Results: grey/blue screen instead of error messages

Thanks,
-Kathe

---

### Post by avtolle on 2009-01-14
The two modules to which the poster was referring were the thermal and fan modules, which I suspect were being called out in the error line he posted, with the precise module set forth, rather than [Reference]. Do you have any error messages that look like that (rather than the annoying issue with the network manager, which, as I recall, I had but never prevented the system from shutting down, albeit quite slowly sometimes)?

---

### Post by birdkathe on 2009-01-14
Turning off the splash screen I got these additional errors:

'Unable to iterate IED devices: No such file or directory'

and a like or two about 'gdm' looks like a null assertion failed for the hash_table

Does this help?
-Kathe

---

### Post by birdkathe on 2009-01-16
...Bump...

Still having the issue.

---

### Post by 440Hz on 2009-03-15
same problem here did you fix it already

---

### Post by 4Orbs on 2009-03-15
> 2) add 'amp=power_off' to the boot command
Results: grey/blue screen instead of error messages

Instead of the above, try:
Open the /etc/modules as root in the text editor,
```
gksudo gedit /etc/modules
```
Then add this as the bottom line:
```
apm power_off=1
```
Save and close the file.
Reboot, and shutdown should work thereafter.
This works for some people, myself included.

---

