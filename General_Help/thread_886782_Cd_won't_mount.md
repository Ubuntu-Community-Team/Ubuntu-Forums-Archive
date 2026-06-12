---
title: "Cd won't mount"
date: 2008-08-11
forum: General Help
---

### Post by Howitzer777 on 2008-08-11
i have some files for brushes and fonts that i want to put into gimp but when i click  it says [IMG]http://i36.tinypic.com/29kp9va.png[/IMG]

---

### Post by cmnorton on 2008-08-11
As root (sudo) you should be able to mount the volume

sudo mount /dev/cdrom0 /media/cdrom0

Make sure your installation has a /media/cdrom0.

Otherwise, will this volume mount on a Windows system and how was the volume created (burned). If you dragged files to it, did you "complete" or "finish" the CD?

---

