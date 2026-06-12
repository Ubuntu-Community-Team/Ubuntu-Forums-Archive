---
title: "[SOLVED] KDE 4: Region &amp;amp; Language"
date: 2008-09-01
forum: General Help
---

### Post by TWO on 2008-09-01
Hello

I've just installed KDE 4 on top of Ubuntu to give it a try, but under the System Settings, it seems that I'm unable to change the system language or region.

I click on the 'Add Language' button but no window pops up.


Does anyone know why there aren't any languages displayed here?

Thanks in advance

TWO
 
Edit: I don't know why I didn't specify which version of KDE 4 I was using. I think I was in a rush at the time. Anyway, it appears that I was on KDE 4.0.3 as provided in the repositories and hadn't noticed the announcement and instructions fo installing KDE 4.1 on the Kubuntu website. The upgrade has bought with it improved functionality and as a result, the resolution to this problem.

I'll have to take care to pay attention to this in future. 

Thanks for your help anyway though.

TWO

---

### Post by Zorael on 2008-09-01
Is this in the KDE 4.0.5 available from the backports repository or the 4.1.0 available from the ppa listed over at kubuntu.org? If the former, chances are it's been fixed in later releases.

Have you tried opening up systemsettings with superuser permissions? That's the only other thing I can think of.
```
$ kdesu systemsettings
```

---

