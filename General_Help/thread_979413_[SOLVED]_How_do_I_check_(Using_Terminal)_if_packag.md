---
title: "[SOLVED] How do I check (Using Terminal) if package/app installed?"
date: 2008-11-11
forum: General Help
---

### Post by otz070 on 2008-11-11
How do I check using terminal to see if my package/app is properly installed?
like for .deb and for other installs as well but mainly for .deb packages

(I'm starting to get used to the terminal as I seem to be using it alot:) it's really not that hard it's just knowing the right command)

Thanks:)

---

### Post by blacky667 on 2008-11-12
You can check this with dpkg-query -l '*pkgname*'
The first two characters in the output show the package installation status. For correctly installed packages it should read "ii"

---

### Post by bodhi.zazen on 2008-11-12
aptitude can help with this as well

```
sudo aptitude search <package_name>
```

See man aptitude :

> search
           Searches for packages matching one of the patterns supplied on the command line. All packages which match any of the given patterns will be displayed; for instance, &#8220;aptitude search &#8217;~N&#8217; edit&#8221; will list all &#8220;new&#8221; packages and all packages whose name contains &#8220;edit&#8221;. For more information on search patterns, see the section &#8220;Search Patterns&#8221; in the aptitude
           reference manual.

           Unless you pass the -F option, the output of aptitude search will look something like this:

               i   apt                             - Advanced front-end for dpkg
               pi  apt-build                       - frontend to apt to build, optimize and in
               cp  apt-file                        - APT package searching utility -- command-
               ihA raptor-utils                    - Raptor RDF Parser utilities

           Each search result is listed on a separate line. The first character of each line indicates the current state of the package: the most common states are
p, meaning that no trace of the package exists on the system, 
c, meaning that the package was deleted but its configuration files remain on the system, 
i, meaning that the package is installed, and 
v, meaning that the package is virtual.

The second character indicates the stored action (if any; otherwise a blank space is displayed) to be performed on the package, with the most common actions being i, meaning that the package will be installed, d, meaning that the package will be deleted, and p, meaning that the package and its configuration files will be
removed. If the third character is A, the package was automatically installed.

---

### Post by caljohnsmith on 2008-11-12
And since there are always so many ways to do things in linux, you could also do:
```
apt-cache policy <package>

```
Always plenty of choices. :)

---

### Post by otz070 on 2008-11-26
Cool thanks to all.:)

---

