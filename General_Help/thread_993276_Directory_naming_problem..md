---
title: "Directory naming problem."
date: 2008-11-25
forum: General Help
---

### Post by ferrous26 on 2008-11-25
At work I have to use CVS and Red Hat (git and Ubuntu at home), and being new to CVS, I accidentally used this command without having much idea of what it would do:

```

cvs co -P -d -r cvs/repo/directory

```

Aside from not doing what I thought it would do, it created a folder named "-r" which I could not remove or rename when using rm, rmdir, or mv. I finally had to run a PERL command to attack the folder at a lower level:

```

perl -e 'use File::Path; rmtree("-r");' 

```

I have since been able to create other folders with similar names on my Ubuntu system at home and had to resort to the same perl command to get rid of it. Is there something else I can do to prevent such files/folders from being created or should I report a bug?

---

### Post by silverglade00 on 2008-11-25
Hmm... so if we change everything to put the system files under a "-r" folder, then the whole accidental rm -rf thing will no longer work. It's not a bug you found, it's a feature!

---

### Post by scorp123 on 2008-11-25
> **ferrous26 said:**
>  ```

perl -e 'use File::Path; rmtree("-r");' 

``` ```
rm -rf ./-r
``` ;)

---

