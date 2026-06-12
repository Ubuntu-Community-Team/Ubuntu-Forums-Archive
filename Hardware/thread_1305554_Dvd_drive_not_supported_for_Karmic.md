---
title: "Dvd drive not supported for Karmic"
date: 2009-10-30
forum: Hardware
---

### Post by Deathvalley122 on 2009-10-30
hi,
 
I have found out that karmic does not support my dvd drive or there seems to be a issue with sr0 I to had unmount my dvd drive due to logs flooding me with this issue.
 

Oct 29 20:30:58 deathvalley122-desktop kernel: [ 3449.472842] VFS: busy inodes on changed media or resized disk sr0
Oct 29 20:31:00 deathvalley122-desktop kernel: [ 3451.473676] VFS: busy inodes on changed media or resized disk sr0
Oct 29 20:31:00 deathvalley122-desktop kernel: [ 3451.477234] VFS: busy inodes on changed media or resized disk sr0
Oct 29 20:31:02 deathvalley122-desktop kernel: [ 3453.468583] VFS: busy inodes on changed media or resized disk sr0
Oct 29 20:31:02 deathvalley122-desktop kernel: [ 3453.472090] VFS: busy inodes on changed media or resized disk sr0
Oct 29 20:31:04 deathvalley122-desktop kernel: [ 3455.467219] VFS: busy inodes on changed media or resized disk sr0
Oct 29 20:31:04 deathvalley122-desktop kernel: [ 3455.470962] VFS: busy inodes on changed media or resized disk sr0
 

But when I slip something into my drive I have to mount it and it will not eject either I have to eject it from the terminal I was wondering if there is a fix for this or if you are not aware of this problem this happens on Karmic I would need solutions to fix this or you guys give me a fix for it.
 

Thanks


P.S.,


I have reported a bug for this.

[https://bugs.launchpad.net/ubuntu/+bug/464134](https://bugs.launchpad.net/ubuntu/+bug/464134)

Also my dvd drive is 

SONY DVD RW AW-Q170A

---

