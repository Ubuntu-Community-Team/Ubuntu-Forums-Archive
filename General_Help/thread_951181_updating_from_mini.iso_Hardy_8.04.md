---
title: "updating from mini.iso Hardy 8.04"
date: 2008-10-17
forum: General Help
---

### Post by hyperscythe on 2008-10-17
I know I'm such a noob, but I just got into Ubuntu today, and I'm wondering how to upgrade from 6.06 to 8.04 on a PPC Mac. I have the mini.iso file, burned it to a CD and then I held "c" when booting, and it goes fine until it tries to download the manual or something; it comes up with a blue screen and stays there. 

Any easier ways to do this? Help a noob out. :P

---

### Post by MaxIBoy on 2008-10-17
It's not really possible to update directly from 6.06 to 8.04. (From 6.06 to 7.04 and from 7.04 to 7.10 and from 7.10 to 8.04, maybe. But it's extremely likely that somewhere along the line, something will break.) Besides which, the PPC port is no longer officially supported, and is maintained by the community, so I don't know if dist-upgrade will work anymore.

My recommendation: backup all the files and do a full reinstall.

---

### Post by hyperscythe on 2008-10-17
> **MaxIBoy said:**
> It's not really possible to update directly from 6.06 to 8.04. (From 6.06 to 7.04 and from 7.04 to 7.10 and from 7.10 to 8.04, maybe. But it's extremely likely that somewhere along the line, something will break.) Besides which, the PPC port is no longer officially supported, and is maintained by the community, so I don't know if dist-upgrade will work anymore.

My recommendation: backup all the files and do a full reinstall.
Sorry, another noob question.

How do I do a full reinstall? I haven't added anything new, so I won't need to back up anything...

---

### Post by MaxIBoy on 2008-10-17
Download the 8.04 CD image. (make sure you get the PPC version. I found a download of it here: [http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/))

Burn the CD.

Install 8.04 (Hardy Heron) over the partition where 6.06 (Dapper Drake) is installed. 

Doesn't get simpler than that.




Alternately, wait for a while until a PPC port of 8.10 (Intrepid Ibex) comes out.

---

