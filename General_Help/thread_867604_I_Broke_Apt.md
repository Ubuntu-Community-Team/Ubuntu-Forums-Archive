---
title: "I Broke Apt"
date: 2008-07-23
forum: General Help
---

### Post by Brando569 on 2008-07-23
whenever i try to use apt-get install it wont install anything and all it says is E: The package linux-image-2.6.25.10-ultimate needs to be reinstalled, but I can't find an archive for it. even though the package is still in /usr/src. when i try to open synaptic it pops up a box that says error and says that it cant find the package and then under that it says this E: Internal error opening cache (1). Please report.

**edit:** thanks to google this seems like a common problem, all you have to do is delete **all** of the files that include the name of your problem package (i had 11 files which contained linux-image-2.6.25.10-ultimate) and then run ```
sudo dpkg --remove --force-depends --force-remove-reinstreq <problem package name here> 
``` and then apt will say this ```
dpkg: serious warning: files list file for package <package name> missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package <package name> missing, assuming package has no files currently installed.
126687 files and directories currently installed.)
Removing <package name> ...
```

but dont worry about it because your problem is fixed! the solution came from [here](http://www.ubuntugeek.com/package-installation-error-and-solution.html) specifically post #8

---

### Post by tinny on 2008-07-23
Long shot..

--purge should COMPLETELY remove the linux-image-2.6.25.10-ultimate
```

sudo apt-get remove --purge linux-image-2.6.25.10-ultimate
sudo apt-get clean
sudo apt-get update

```

---

