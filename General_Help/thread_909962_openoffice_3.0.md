---
title: "openoffice 3.0"
date: 2008-09-04
forum: General Help
---

### Post by Nailhac on 2008-09-04
I intend to download open office 3.0. When installing this is it necessary to uninstall current version 2.4 or overwrite??:confused:

---

### Post by Elfy on 2008-09-04
It installs seperately so you can use both, OO3 is still a beta. I do use it myself though and have had no problems with it.

---

### Post by Spiritof76 on 2008-09-06
I tried getting the new Release Candidate working in Ubuntu it crashes. I left 2.4 installed.   

Will I have to wait for the new CD package to gewt it running or is it now required to uninstall the 2.41?

---

### Post by Fredo on 2008-09-11
> **Spiritof76 said:**
> I tried getting the new Release Candidate working in Ubuntu it crashes. I left 2.4 installed.   

Will I have to wait for the new CD package to gewt it running or is it now required to uninstall the 2.41?

Installing OO.o 3.0 RC1 should work without uninstalling 2.3, since it installs in /opt.

But I also experienced the crash. I get the new startup screen, but when I select "New Text document", it crashes. In the terminal, I only get this quite uninformative message:

```
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'
```

Did anybody manage to get the RC working?

---

### Post by kokkus on 2008-09-11
OO3 is beta but works fine under windows. WIne will support it. Then u can have them both installed and with no problems at all. I suggest u do it like that for now, atleast untill the package release.

---

### Post by Moises Cabello on 2008-09-11
Try to remove .openoffice.org folders in home

---

### Post by Fredo on 2008-09-11
> **Moises Cabello said:**
> Try to remove .openoffice.org folders in home

Thanks, that lead me to the right solution. After removing ~/.openoffice.org, I get the setup assistant again. This time, I chose not to migrate my personal settings from OO.o2, and that did the trick.

---

### Post by zerubbabel on 2008-09-21
I'm running OpenOffice 3.0 RC1 and am very happy with it. Now how can I make it the default when I double-click .odt files, instead of 2.4.1 launching? I'm not quite ready to uninstall 2.4.1 yet.

---

