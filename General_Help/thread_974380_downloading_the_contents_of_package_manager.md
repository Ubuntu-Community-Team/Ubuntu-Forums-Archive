---
title: "downloading the contents of package manager"
date: 2008-11-07
forum: General Help
---

### Post by Griffin Bain on 2008-11-07
mates,

I have an issue. I need some files out of synaptic package manager but my ubuntu computer is in a different location off the internet. I have internet access on an XP computer and need these files, if possible, is there a way to get them in .deb files from another page or website so I can put them on a jump drive?

Files I need:

alien, libxml1, libpng12-0, libpng12-dev, libgtk1.2 and 
libgtk1.2-common

---

### Post by SuperSonic4 on 2008-11-07
[http://www.getdeb.net/](http://www.getdeb.net/) is usually best

---

### Post by ajgreeny on 2008-11-07
You can also get the packages by:-
1    Use synaptic to find all the dependencies of the package you want on your unconnected ubuntu machine.
2    On the windows machine go to [http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/) or whichever version of ubuntu you need and there by following the links you can download all the packages as the .deb files.
3    Back on the ubuntu machine install the packages copied over from the windows machine by making a folder for the debs, navigating to it and installing using the command ```
cd Foldername && sudo dpkg -i *.deb
```

---

