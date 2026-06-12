---
title: "Problem trying to partition"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by thezerofire on 2009-11-02
I get to the Prepare disk space screen and I select "Install Side by side, choosing between them each on startup"

I click next and get:
"before you can select a new partition size, any previous changes have to be written to disk. you cannot undo this operation. Please note that the resize operation may take a long time"

I assume that part is normal, but after "Scanning disks" I get:
 "an error occurred while writing the changes to the storage devices. the resize operation has been aborted"

after which I go to the manual partition screen which I don't know how to operate.

Can anyone help me get this installed/tell me what's going on?

---

### Post by presence1960 on 2009-11-02
Have you defragged windows at least once or twice and turned off system restore prior to resizing windows?

Also back up any data you do not want to lose. Although partitioning and/or installation processes normally work without any glitches, remember that things can & do happen.

If you are using Vista it is suggested you use Vista's disk management utility to create space for ubuntu. [here]("http://bugzilla.gnome.org/show_bug.cgi?id=379482") is a link for an unresolved bug when trying to resize vista with anything other than vista's disk management utility. Sometimes it works and sometimes it does not. When it does not vista is rendered unbootable. I would not chance it, I would use vista's disk management utility to shrink vista's partition when creating space for ubuntu.

---

### Post by thezerofire on 2009-11-02
you mean before trying to go through the partitioning process? not in a while and no to the system restore. I wasn't aware you could disable it.

---

### Post by presence1960 on 2009-11-02
> **thezerofire said:**
> you mean before trying to go through the partitioning process? not in a while and no to the system restore. I wasn't aware you could disable it.

I would defrag windows at least once probably twice. You can turn off system restore in Control Panel.

Windows has a bad habit of throwing files all over the disk in no particular order. This may be why your resizing can not be completed. Also if you have Vista see the last part I added to my above post about actually resizing Vista. There is a known bug that is still unresolved.

---

### Post by thezerofire on 2009-11-02
I don't have Vista but apparently the netbook came with a vista launcher that takes up 8GB. I'll try that defrag and system restore thing

---

