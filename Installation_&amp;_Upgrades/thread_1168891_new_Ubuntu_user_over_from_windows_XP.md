---
title: "new Ubuntu user over from windows XP"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by artdummy on 2009-05-24
I just discovered Ubuntu and love it's programs. The only thing is I have a lot of work using windows xp on this computer that I also installed Ubuntu on. I want to copy this work to the ubuntu operating system how can I do that. thanks for any help.

---

### Post by logos34 on 2009-05-24
during installation of ubuntu you'll be prompted to import email and ie browser favorites/bookmarks.  Ubuntu includes out-of-box support for read+write of NTFS filesystem, so you can access your windows documents.  After you've copied all your files to the ubuntu partition, you could delete XP.

---

### Post by SuperSonic4 on 2009-05-24
If by work you mean data then you can use either what logos said or copy and paste it from the drive once you've installed.

You could also move it to it's own data partition although this could be bad news if you're not confident with formatting and then edit fstab to mount it on boot

Beware that some files may be a windows only filetype (like exe or cab or msi which work natively only on windows) but your media such as mp3 doc avi etc should be fine once codecs are installed

---

