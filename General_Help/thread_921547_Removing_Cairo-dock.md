---
title: "Removing Cairo-dock"
date: 2008-09-16
forum: General Help
---

### Post by Macdelaney on 2008-09-16
I finally got the cairo-dock working last week (i couldn't enable 3d view), and today Ubuntu update manager told me there was an update for it but that it wouldn't be installed. So, i went to synaptic and mark the packages for complete removal, i figured i would then be able to reinstall it, ending up with the newer version. The thing is that some weird errors come up and some packages cant be installed. The cairo-dock package is in fact installed but there are no themes, no applets and no options in the Views tab, so i would like to just erase everything and start again, wich marking the package for complete removal didn't do. Anyone can tell me how to do this?
Thanks in advance

---

### Post by rdionicio on 2008-09-16
Try

```
sudo apt-get remove cairo-dock
```

---

