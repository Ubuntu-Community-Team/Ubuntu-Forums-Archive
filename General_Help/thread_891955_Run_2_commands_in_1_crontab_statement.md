---
title: "Run 2 commands in 1 crontab statement?"
date: 2008-08-16
forum: General Help
---

### Post by Hawk__0 on 2008-08-16
What my goal is for this crontab is to basically back up my music once a day THEN unmount my hard drive (external).  This is what I have:

```
# m h  dom mon dow   command
  4 14    * *   *  rsync -u -r Music/* /media/Vault/mint_music/
  30 15    * *   *  umount /media/Vault

```

but if I add anything like && umount /media/Vault or ; umount /media/Vault then my crontab has errors.  Is this possible? Given certain circumstances I can see this as a fail method to back up my data as it could possibly unmount the drive before my data is completely copied..

---

