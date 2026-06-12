---
title: "Help - boot error."
date: 2008-08-23
forum: General Help
---

### Post by edib0y on 2008-08-23
Ok, i recently installed Ubuntu 8.04 LTS Desktop edition (64-bit), and today sudenly when i'm booting up ubuntu it goes into Busybox, and I cant boot ubuntu! I'm writing trough live CD, because my Vista is also down, but I will deal with that when i get my ubuntu working. I installed it  inside windows partition - the new v8 option. partition name is dev/sda1, and when I am trying to acces 'media files' it shows me this error  "Failed to mount 'dev/sda1': operation not supported Mount is denied because NTFS is marked to be in use" and something more, included error in atachment! please help!

---

### Post by edib0y on 2008-08-23
ok, after searching hard in google, i fixed it myself. I just had to force mount it, and then unmount it. the problem was that windows dying didn't properly unmount the disk, so ubuntu couldn't acces it! this link was what helped me! [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/").

---

