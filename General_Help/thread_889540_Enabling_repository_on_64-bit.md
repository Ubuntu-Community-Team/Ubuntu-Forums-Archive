---
title: "Enabling repository on 64-bit?"
date: 2008-08-14
forum: General Help
---

### Post by techstop on 2008-08-14
Well, after a bit of digging, I found I add to add the following lines to sources.list;

```
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
```

I ran a apt-get update and then tried to install the Zimbra Desktop using;

sudo apt-get install zdesktop

...but I got an error saying the package could not be found. :confused:

Is there no such thing as the partner repository for 64-bit hardy?

---

### Post by Vadi on 2008-08-16
There is, but that particular application doesn't support 64bit. So there is no package for it.

---

### Post by ppaixao on 2008-08-21
I have those repos on my file but it can find zdesktop.

---

### Post by Vadi on 2008-08-21
zdesktop is not available for 64bit, they only make a 32bit version

---

