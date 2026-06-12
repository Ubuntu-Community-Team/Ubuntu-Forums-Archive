---
title: "menu.lst in grub folder missing"
date: 2008-10-26
forum: General Help
---

### Post by abercross1991 on 2008-10-26
well i installed wubi. configured ubuntu for a whole day. rebooted and now i cant start ubuntu. i checked and saw that menu.lst from grub folder (c:\ubuntu\...grub\) is mising. is there any way i can get it back.

im using ubuntu hardy + vista

---

### Post by ago on 2008-10-27
run chkdsk /r from windows in the drive where you installed ubuntu, then look for a hidden fodler c:\found.000 (you need to change windows explorer settings to see hidden files) if you find one move the files in there to their original position.

---

