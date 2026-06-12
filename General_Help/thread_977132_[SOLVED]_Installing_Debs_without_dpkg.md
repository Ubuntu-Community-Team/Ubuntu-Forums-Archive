---
title: "[SOLVED] Installing Debs without dpkg"
date: 2008-11-09
forum: General Help
---

### Post by dstein on 2008-11-09
Whenever I have a deb file, I use dpkg to install the package. Is there any way to use aptitude or synaptic to install these debs?

I would just add ```
deb /home/... intrepid ___ ____
``` to my sources.list file, where /home/... would be replaced with the file. I am unsure what would go where the blanks are, but I see that other entries in the sources.list file have strings there.

I am unsure if this would work or if there is a better way. Please let me know the best way to install debs with aptitude or synaptic, and what the preceding blanks are used for in the sources.list file.

Thanks.

---

### Post by Mazin on 2008-11-09
Hmm... I'm not sure why you have to install debs from files so often, and I'm not sure why you don't want to use dpkg, since, well, it's the tool that installs deb.

If it's any consolation, you can double-click the deb, which will bring up a GUI for installing packages.  Otherwise, there is no reason to not use dpkg.

---

### Post by dstein on 2008-11-10
I would prefer to use a program such as aptitude or synaptic that does a better job of handling dependencies. That is, if a program depends on another program, those packages will automatically install/uninstall the dependencies if I install or uninstall the program.

---

### Post by lswest on 2008-11-10
you might want to have a look at this:
[http://ubuntuforums.org/showthread.php?t=20217](http://ubuntuforums.org/showthread.php?t=20217)

essentially you have to:

a) Find and download the packages you want (save it to one folder I'll call a "repo" for the moment, since it will be your local repository).

b) Create the packages.gz file as follows:
```
cd */path/to/repo/*
sudo dpkg-scanpackages binary /dev/null | gzip -9c > binary/Packages.gz
```

c) Add the entry to your sources.list as follows:
```
deb file:*/path/to/repo/* ./
```

I do not know if this still works, I've never tried it, but I do believe it should.  Post back with your results maybe?

---

### Post by Mazin on 2008-11-10
The GUI for installing debs also automatically installs dependencies.  Does that help?

---

### Post by lswest on 2008-11-12
> **Mazin said:**
> The GUI for installing debs also automatically installs dependencies.  Does that help?

I think he finds gdebi's dependency handling to be lacking, but I could be wrong.

---

### Post by dstein on 2008-11-23
Thanks lswest. I followed the instructions on the link you provided. Basically I had to create a directory with debs in them. Then, in the same directory, I created a file that lists these debs (each one beginning with "./". Lastly, from this directory, I ran ```
dpkg-scanpackages . listofdebs > Packages
```
Then I added this directory to sources.list:
deb file:~/Repository ./
and ran apt-get update

This worked perfectly. Aptitude handled dependencies perfectly.

Thanks again.

---

### Post by fslezak on 2008-11-23
If you have 8.04 or higher, double-click on them.

---

### Post by dstein on 2008-11-23
I don't believe that gdebi has as many options as aptitude or some other package installer. I am not sure though, because I have not used it. My main reason for sticking with one package manager, aptitude, is because it handles dependencies and unused dependencies better this way, which I learned in a prior thread of mine 2 years ago - [http://ubuntuforums.org/showthread.php?t=196111](http://ubuntuforums.org/showthread.php?t=196111).

---

