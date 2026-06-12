---
title: "Unable to hear audio from cd rom: mount problem?"
date: 2008-11-10
forum: General Help
---

### Post by manolomanolo on 2008-11-10
Hi.

When I try to play music from CDROM using amarok or any other player I'm unable to open audio files.
For example, trying to open .was files using Amarok gives:
> "No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes."

No problems if I copy those .wav from CDROM to my hard disk.

Actually when I browse the content of CDROM its files appear to be "locked" (each file is represented with an icon having a little lock on the right-down corner) and I suppose this is the cause why those players cannot access them.

This is the /etc/fstab line related to mounting my cdrom:
**/dev/scd0 /media/cdrom0 udf,iso9660 user,auto,exec,utf8 0 0**

Thanks for your attention.
Regards.

---

### Post by lisati on 2008-11-10
The "locked" icon probably refer to files on most CD-ROMs being "read only" (meaning you can't change them) I would *guess* that the difference in your ability to open the files depending on their location could be related in part to their being read-only, and partly due to the method the program uses to open the files. Amorak is possibly opening them in "read/write" mode (maybe to help keep track of the "last played" information), even though for playing files this isn't strictly necessary.

---

