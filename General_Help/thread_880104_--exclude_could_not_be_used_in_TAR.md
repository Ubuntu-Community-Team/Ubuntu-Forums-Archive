---
title: "--exclude could not be used in TAR"
date: 2008-08-04
forum: General Help
---

### Post by princekinTOT on 2008-08-04
```
root@XXX-desktop:/bin/King# tar --exclude&#65309;/bin/King/backup1.tar.gz -cvpf backup1.tar.gz
tar&#65306;Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.
root@XXXX-desktop:/bin/King# 
```

---

### Post by jerome1232 on 2008-08-04
that syntax is a bit wrong. If you want it gunziped add the -z option also. (as in my example) I also eliminated the -p option as that is default when ran as root, and according to your example you are running this as root
```
tar cvzf backup1.tar.gz --exclude=/bin/King/backup1.tar.gz / # if you trying to gunzip up some other directory then replace "/" with that directory
```

---

### Post by Yannick Le Saint kyncani on 2008-08-04
> **princekinTOT said:**
> root@XXX-desktop:/bin/King# tar --exclude&#65309;/bin/King/backup1.tar.gz -cvpf backup1.tar.gz

Read the manpage again, you're supposed to tell tar what you want tarred. In your case, you probably want to add /bin/King/ at the end of your command.

---

