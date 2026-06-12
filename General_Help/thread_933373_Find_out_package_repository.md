---
title: "Find out package repository"
date: 2008-09-29
forum: General Help
---

### Post by stek79 on 2008-09-29
Hi,
    I was wondering how to check which of the installed packages come from main repository and which not.

Anyone can help me here, preferabily with a command line tool? I might guess that a dpkg query should be enough.

Also, can you confirm that security updates are done by ubuntu only on main packages?

Thanks

---

### Post by drs305 on 2008-09-29
I hope someone can provide a good answer regarding using the command line. In the meantime, you can view the packages available in each repository in your sources.list via synaptic. 

Open synaptic, Click on "Origin" in the lower left window. In the upper left window, you can select the repository you wish to investigate. Once you have highlighted a repository, the packages (available or installed) are listed in the right window.

When selecting a repository, you need to carefully select the one you are interested in. For example, to view the *main* ubuntu repository, you need to be sure you have selected the correct *main*. There may be "main" repositories for ubuntu, medibuntu, security.ubuntu, etc.

---

