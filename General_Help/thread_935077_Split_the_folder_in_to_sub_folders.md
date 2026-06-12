---
title: "Split the folder in to sub folders"
date: 2008-10-01
forum: General Help
---

### Post by bn_munni on 2008-10-01
Hello All,

I need a simple uitility that will split my main folder by name in to subfolders (Ex: main folder 8390000/subfolders, i want it like 8/39/0000/subfolders).Could you please help me out on how to do this

Thanks

---

### Post by tCarls on 2008-10-06
Here's a very simple script that should work but doesn't do any error checking.

```

for file in *; do
   mkdir -p ${file:0:1}/${file:1:2}
   mv $file ${file:0:1}/${file:1:2}/${file:3}
done

```

---

