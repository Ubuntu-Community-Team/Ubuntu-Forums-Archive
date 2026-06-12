---
title: "force download of packages/dependencies with apt-get"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by pythonscript on 2009-07-29
How do I force apt-get to download a package and all of its dependencies from the repositories, even if they're already installed? In this case, I'm trying to download the gnome network manager (network-manager-gnome) but I know it has some dependencies that will be removed if I remove it. When I run

```
sudo apt-get install -d network-manager-gnome
``` it tells me that it's already installed, and it won't download the .debs. I want to test out a new network manager, but I want to have those packages on hand in case I mess up. That way, I can just reinstall them without having to connect to the internet. Any ideas? I'm trying to do this from the command line using apt-get/aptitude's handling of dependencies, so I'd like to avoid just downloading every single dependency (at least those that will be removed when I uninstall the gnome network manager) from packages.ubuntu. com. Thanks for the help!

I don't have another computer to download the packages on, either, so I don't think that's a solution for me right yet.

---

### Post by verylazyguy on 2010-03-17
--reinstall
> sudo apt-get install -d network-manager-gnome --reinstall

---

