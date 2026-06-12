---
title: "[SOLVED] Eliminate specific updates from update manager"
date: 2008-09-06
forum: General Help
---

### Post by kryos on 2008-09-06
Update Mananger is reporting over 200 language pack updates that I do not need and would like to mark as skip/don't remind at this time/not interested now/?  I don't want to turn off reminders globally but only for those that I do not need, and cannot see where to accomplish this.

---

### Post by hyper_ch on 2008-09-06
uninstall the other languages that you have installed that you don't need. Then you won't be prompted for an update of those.

---

### Post by drs305 on 2008-09-06
There is an app named 'localepurge' in the repositories. On the initial run you choose which locales you wish to use. From then on, localepurge works with apt and limits the language packs to the ones you selected.

The man page has a caution about using it but I've never had a problem.

```
sudo apt-get install localepurge
```

There is also the Language Support section of System, Admin, Language where you can make sure only the language(s) you wish are selected.

---

