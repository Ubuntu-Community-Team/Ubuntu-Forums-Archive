---
title: "Suggestions for keeping current on software versions"
date: 2008-10-23
forum: General Help
---

### Post by edmicman on 2008-10-23
I'm on 8.04 Hardy, and I appreciate that apt maintains my software.  But there are some programs I use regularly that I feel are woefully behind in the repos - point versions or more behind what the latest is available on the software's website.  Ones that specifically come to mind are Pidgin, FileZilla and Deluge that I've run across recently.  Notably Pidgin, since I've had some minor problems with IMs lately, and wonder if an updated version might fix those.  

Does everyone manually install/build from source or whatever?  Or do you just wait and hope that some day down the road you might get an update?  Are there other methods or something?  Sometimes I've found some vendors provide .deb files of their own, but not all do.  

Thanks for any help!

---

### Post by jmszr on 2008-10-23
Getdeb.net currently has Pidgin 2.5.2, Filezilla 3.1.5, and Deluge 1.03. You would need to update them youself,but that's no big deal.

---

### Post by zvacet on 2008-10-24
You can add getdeb in your sources list 

```
gksudo gedit /etc/apt/sources.list
```

```
deb http://ubuntu.org.ua/ getdeb/
```

save and close file.

```
sudo apt-get update
```

---

### Post by 3rdalbum on 2008-10-24
I don't see the need to upgrade to every new point version. But if I do, I can often find good new versions at GetDeb. Alternatively, I compile from source.

---

