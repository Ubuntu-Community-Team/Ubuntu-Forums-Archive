---
title: "dual partition w/ winxp-disk errors on ntfs side"
date: 2008-10-15
forum: General Help
---

### Post by jrav on 2008-10-15
i'm running ubuntu w/ win xp on the same hd for a couple months now without problems while accessing the ntfs partition within ubuntu. but recently, i've noticed whenever i run chkdsk (windows program to check ntfs disk integrity), i get repeated errors of: "Missing object id index entry or duplicate object id detected" and even running chkdsk with /f /r in boot mode still gives errors.

while in ubuntu, i recently was copying some files and some duplicates of lower and upper case characters, which ubuntu uniquely let me do (no "overwrite file?" messages), onto the ntfs partition. i was wondering if i boot into windows like that, could that cause ntfs partition issues? or if it does, does anyone know how to fix the prob?

thanks for all your help, and if there's somewhere else i should be posting this, please let me know...

jrav

---

### Post by spiderbatdad on 2008-10-15
take a look at testdisk in synaptic package manager. I believe it can repair errors on your ntfs.

---

### Post by marshall.robert on 2008-10-15
from what i understand, you have similar file names that use different case letters as the only actual difference.

linux is case sensitive so hello.txt is different from Hello.txt. windows will not complain about this, but you will not be able to access some files because windows will get confused.

---

