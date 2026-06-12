---
title: "[SOLVED] One issue with Rsync"
date: 2008-12-02
forum: General Help
---

### Post by linuxology on 2008-12-02
Ok Rsync works great, but when I delete files from the source directory it does not delete them in the destination.  Can someone help with this?  I have included a copy of the rsync script.


#!/bin/bash
# rsync documents

rsync -av /home/linuxology/Documents/* /media/2ndary_250GB/Docs_Bakup
rsync -av /media/2ndary_250GB/MP3_backed_up/* /media/2ndary_108GB/MP3_backed_up

---

### Post by __Ryan__ on 2008-12-02
You can add the '--delete' option. I would suggest using the '--dry-run' option as well to test what will happen before going ahead with the sync.

---

### Post by m_l17 on 2008-12-02
Also take the time and read the man page:

[http://manpages.ubuntu.com/manpages/hardy/man1/rsync.html]("http://manpages.ubuntu.com/manpages/hardy/man1/rsync.html")

---

### Post by linuxology on 2008-12-02
--delete option does not work

---

### Post by linuxology on 2008-12-02
Got it to work.  Have to remove * at the end of source directories.

---

