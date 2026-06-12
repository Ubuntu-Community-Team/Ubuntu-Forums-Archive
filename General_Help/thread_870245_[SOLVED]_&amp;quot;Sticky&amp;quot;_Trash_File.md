---
title: "[SOLVED] &amp;quot;Sticky&amp;quot; Trash File"
date: 2008-07-25
forum: General Help
---

### Post by lordadi on 2008-07-25
Hi guys,

I have a weird problem. A while back, I moved an unneeded public_html folder to the trash. Now that I need to empty my trash to free disk space, the folder won't delete!

I have checked this by moving other folders to the trash and then deleting them from there and it works but not my public_html folder!


Any ides?


Thanks in anticipation,


Lordadi.

---

### Post by pauper on 2008-07-25
Please, post the output:

```
lsattr ~/.Trash/*public_html*
ls -l ~/.Trash/*public_html*
```

Have you tried these commands?

```
rm -rf ~/.Trash
mkdir ~/.Trash
```

---

### Post by RuleMaker on 2008-07-25
If you are using Hardy then this should work:
```
cd /home/<username>/.local/share/Trash/files/
sudo rm -r public_html
```

Dont forget to replace <username> with your username.

---

### Post by drs305 on 2008-07-25
Delete the 'files' and 'info' folders to remove all trash or navigate to individual files

For Hardy user trash:
```
gksu nautilus ~/.local/share/Trash
```

For Hardy root trash:
```
gksu nautilus /root/.local/share/Trash
```

---

### Post by lordadi on 2008-07-25
Hi,

Thanks RuleMaker it did the trick.

```
rm -rf
```

Pauper, I'm no bash jockey but to me the above looks dangerous.



Cheers,



Lordadi.

---

