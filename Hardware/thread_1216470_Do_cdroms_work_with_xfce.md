---
title: "Do cdroms work with xfce?"
date: 2009-07-18
forum: Hardware
---

### Post by NinjaNumberNine on 2009-07-18
Hi, all. I have a tsstcorp DVD-RAM/RW drive and am running Mythbuntu 9.04. for some reason, when I insert a music cd, it does not show a "new removable device" alert. I tried browsing it under //media/cdrom0, but it showed that it was empty. :confused:
Anyone got any ideas?


(P.S. You would think that Mythbuntu, which is BUILT for the ultimate Multimedia experience would play a cd, right? )

           :biggrin:   :mrgreen:   :biggrin:    :mrgreen:   :biggrin:    :mrgreen:   :biggrin:

---

### Post by ibutho on 2009-07-18
Audio discs will not show in /media because they don't have a filesystem you can mount. What happens when you start a cd playing app? Does the disc play?

---

### Post by wyliecoyoteuk on 2009-07-18
Mythbuntu plays CDs fine, even rips them to the hard disk, but you need to be in MythTV, Mythbuntu is a cutdown Ubuntu platform for MythTV after all.

You may have to specify the CDrom device in MythTV setup, if it isn't /dev/cd0 for some reason (e.g. if it is a SATA drive)

---

### Post by NinjaNumberNine on 2009-07-18
> You may have to specify the CDrom device in MythTV setup, if it isn't /dev/cd0 for some reason (e.g. if it is a SATA drive)     It is not SATA. Has normal PATA hookups and all.
> ...but you need to be in MythTV MythTV plays them fine, but it is sometimes too large-scale. I want a small, lightweight app like mplayer to run cds.  > What happens when you start a cd playing app?  None of the cd playing programs other than MythTV work. (i.e. VLC, Mplayer,)

---

