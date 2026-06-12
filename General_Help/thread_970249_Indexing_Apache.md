---
title: "Indexing Apache"
date: 2008-11-04
forum: General Help
---

### Post by skidder on 2008-11-04
I am having trouble with my web site.  I use apache2 with virtual hosts.  I would like to stop indexing in one of my directories called (docs) I have tried .htaccess and <Directory> tags with Options-Indexes and they both stop indexing, but they also cut my links that go to that folder.  Is there a way to have your cake and eat it too.  I mean stop people from accessing the whole folder and have my links to files in that folder work?  Maybe I can't have both, but it seems like I should be able to do this.

---

### Post by tonybaqain on 2008-11-04
simply 
```

<Directory /path/to/directory>
    Options none
</Directory>

```

check if you have in apache2.conf anything like **Options Indexes ....** and just remove the indexes from there.

have fun :)

---

### Post by skidder on 2008-11-05
Hey thanks Tony,

That worked, I had indexing still in the virtual host directory tags.

---

