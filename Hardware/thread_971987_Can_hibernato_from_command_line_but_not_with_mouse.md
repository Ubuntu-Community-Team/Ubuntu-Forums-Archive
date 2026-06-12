---
title: "Can hibernato from command line but not with mouse"
date: 2008-11-05
forum: Hardware
---

### Post by diegorodriguezv on 2008-11-05
Hello everyone.

I have a problem (after a backup/reinstall/restore for awkward reasons) on my Ubuntu 8.04 box.

When I click the "power" button on gnome panel and hit Hibernate the screen goes blank for 2 seconds and then prompts for password to unlock the session.

If I run the following command:
```
 sudo /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux 
```
the computer hibernates (and then resumes) correctly.

I thought that was the script run by the gnome panel button.

Can someone please help me diagnose the problem?

---

### Post by mul14 on 2008-11-12
Hi.. I'm not expert. But I found this in /etc/gdm/gdm.conf

```

HibernateCommand=/usr/sbin/pm-hibernate

```

Maybe can fix your problem..

---

### Post by diegorodriguezv on 2008-11-16
Thank you mul14.

Beside the one I described I had some other annoyances in my system like not being able to configure the network from the system menu or mounting ntfs volumes.

I decided I had enough and reinstalled Ubuntu.

Thanks again for your help.

---

