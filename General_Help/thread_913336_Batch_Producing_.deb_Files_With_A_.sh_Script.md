---
title: "Batch Producing .deb Files With A .sh Script?"
date: 2008-09-07
forum: General Help
---

### Post by Niklas Schröder on 2008-09-07
Could anyone out there help me out real fast?  I have about 30 .deb files that I need to compile, but I don't want to have to go through and manually run "dpkg-deb -b PACKAGENAME" for every one of them (the .deb's are updated regularly as well).  Could someone out there whip me up a .sh script (or something similar) that would look through a folder and automatically run "dpkg-deb -b" on all the folders?  "dpkg-deb -b *" and "dpkg-deb -R -b *" don't work sadly...

---

### Post by HalPomeranz on 2008-09-08
```

for i in *
do
    dpkg-deb -b $i
done

```

---

### Post by Niklas Schröder on 2008-09-08
Thanks a million!  I'll test it out a little later.  Looks promising though!

---

### Post by Sycron on 2008-09-08
Create a folder on the Desktop and copy all the 30debs on your folder then go to a terminal and type.
```
cd ~/D*/**[COLOR="Red"]your_folder_name[/COLOR]** && sudo dpkg -i *.deb
```

be sure to change your_folder_name

---

### Post by Niklas Schröder on 2008-09-08
> **Sycron said:**
> Create a folder on the Desktop and copy all the 30debs on your folder then go to a terminal and type.
Well...  They're not .deb's yet.  They're just the folders with the contents of the .deb and the "control" file.

---

