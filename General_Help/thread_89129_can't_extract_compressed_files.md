---
title: "can't extract compressed files"
date: 2005-11-11
forum: General Help
---

### Post by nikolai.m on 2005-11-11
hi all,
i did cleen install of Kubuntu. i think it was possible to right klick on compressed file (tar.gz, tar.bz2, zip...) and extract them. well...i'm missing this option on my right klick menu!!! please help me to get it back...i don't want to go to terminal everytime i xtract zip-file

---

### Post by odrop on 2005-11-11
Sounds like you might be missing the package konq-plugins.

Try giving that one a shot.

---

### Post by nikolai.m on 2005-11-12
well...that's the thing.. i had it installed during the cleen install!!!
please some more solutions?
or should i just clean reinstall kubuntu? (hope not)

---

### Post by odrop on 2005-11-12
Check to see whats in:

/usr/share/apps/konqueror/servicemenus/

That seems to be where we install them.  There should a lot of .desktop files sitting there nicely.

If they are not there, you might wana try 
```

apt-get install --reinstall konq-plugins

```

Actually, looking again, theres a ton of .desktop files spread across our kubuntu.  I'm not sure which one you might actually need or are missing.  I'll poke around later when I have some time.  Good luck.

---

