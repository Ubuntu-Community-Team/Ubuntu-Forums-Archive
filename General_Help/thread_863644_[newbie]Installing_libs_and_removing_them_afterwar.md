---
title: "[newbie]Installing libs and removing them afterwards, among other things"
date: 2008-07-18
forum: General Help
---

### Post by damatta on 2008-07-18
Hi,


I need to compile aMule and I know all the instructions. The problem is that I need some developement packages that will install a WHOLE LOT OF libs and it's also a pain to select every single package using synaptic, so:

1) Is there a way I can install all the dev. packages I need in a single shot using the terminal?
2) After compiling, how do I remove all the dev packages along these libs previously installed, that wont be needed anymore? I'm asking this because it seems that when I choose to completely remove the package the libs are not removed.

Thank you in advance !

---

### Post by CatKiller on 2008-07-18
You could try ```
sudo apt-get build-dep amule
```

EDIT: There are .debs of the latest version [available]("http://forum.amule.org/index.php?PHPSESSID=053bb9e1388d4c24bdbf6a3abe2ad625&topic=15249.0").

---

### Post by damatta on 2008-07-18
Thank you. Now I was thinking of how to remove all these dev packages thoroughly, after compilation, knowing I won't need again the dependencies just installed. Thank you

---

