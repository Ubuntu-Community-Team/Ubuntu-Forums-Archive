---
title: "Space issue in Terminal"
date: 2005-11-09
forum: General Help
---

### Post by rado_london on 2005-11-09
Hi 
I have strange problem.
My windows partition is mounted as /media/ntfs and I often need to use it via terminal.
When I type 
```
cd /media/ntfs/Documents and Settings
```
the terminal replies me
```
bash: cd: /media/ntfs/Documents: No such file or directory

```
Is there any symbol for that problem?
Thanks in advance

---

### Post by Pablo_Escobar on 2005-11-09
In Linux You need to tell the command line that You're using space.
AFAIR it should be like 
> cd /media/ntfs/Documents\ and\ Settings

"\" sign is a notification that You're going to use a special char like f.e. space.

---

### Post by doclivingston on 2005-11-09
Alternately you can enclose the name with quotes.
```
cd "/media/ntfs/Documents and Settings"
```

---

### Post by rado_london on 2005-11-09
Thanks guys it works wwith both ways!

---

