---
title: "tar ing read-only files &amp; folders"
date: 2008-12-01
forum: General Help
---

### Post by Johnsie on 2008-12-01
Hi,  I'm trying to tar some folders and subfolders that are read only using the following command:

> tar  -cvvf moo.tar /foldername


I'm getting a permission denied message. The folder I'm is has write permissions but /foldername is read-only.

Does anyone know if there's a way to do this that wont give me errors? I have no gui, just terminal.

Thanks,

John

---

### Post by Angelajhone on 2008-12-01
Hi I am angela,


This is the best information.

============================================================
[Internet Marketing Company]("http://www.internetmarketinginc.com/")  l  [Online Marketing]("http://www.internetmarketinginc.com/") | [seo company]("http://www.internetmarketinginc.com/")

---

### Post by happyhamster on 2008-12-01
Try:

sudo tar -cvvf moo.tar /foldername

---

