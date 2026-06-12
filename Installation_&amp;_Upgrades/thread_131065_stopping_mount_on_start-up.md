---
title: "stopping mount on start-up"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by ces001 on 2006-02-15
I have a Dell PC i am dual booting with windows.  Dell has a small partition with system files on my HD that is being automatically mounted when I start Ubuntu.  If I remove the entire line from fstab, will that keep it from mounting or will that also cause other problems?

Thanks

---

### Post by o_fortuna on 2006-02-15
[QUOTE=ces001]I have a Dell PC i am dual booting with windows.  Dell has a small partition with system files on my HD that is being automatically mounted when I start Ubuntu.  If I remove the entire line from fstab, will that keep it from mounting or will that also cause other problems?

Thanks[/QUOTE]
Just remove the line. There won't be any problems unless the system starts looking for something there (which it probably -- most likely -- won't). Then it won't mount.

---

### Post by ces001 on 2006-02-15
[QUOTE=o_fortuna]Just remove the line. There won't be any problems unless the system starts looking for something there (which it probably -- most likely -- won't). Then it won't mount.[/QUOTE]


Thank you ;)

---

### Post by taurus on 2006-02-15
Or you can also put a # in front and the system won't read it in case you want to have that line back in /etc/fstab later...

---

