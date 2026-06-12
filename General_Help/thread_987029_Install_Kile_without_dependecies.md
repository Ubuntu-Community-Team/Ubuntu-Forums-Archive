---
title: "Install Kile without dependecies"
date: 2008-11-19
forum: General Help
---

### Post by CalvinGhost on 2008-11-19
Hello !

I'm trying installing Kile with Synaptic but it also ask me to install TexLive which I already installed without Synaptic (texlive-2007). So is it possible to install a packet without some of its dependencies ? I should uninstall my TexLive distribution and then reinstall it via Synaptic, but the problem will come back if I decide to install TexLive 2008 which is not in the repositories.

Thanks for your help !

[EDIT] I'm sorry for the title, I forgot a 'n' :s

---

### Post by ju2wheels on 2008-11-19
You should install it from the repository, the version of texlive in the repository is already 2007 so you would be fine. 

It would not be a problem when you decide to texlive 2008 just make sure you use the debian installers for it so the package manager knows its installed. If you install using the source code then the package manager has no idea you have installed it.

Take a look here [http://www.tug.org/texlive/debian.html](http://www.tug.org/texlive/debian.html) which states the 2008 debian installers are being worked on.

---

### Post by tacutu on 2008-11-19
i also use texlive 2008, which is not in the repos... to get rid of the dependencies issue, I created a dummy .deb useing a nice program called equivs (in the repos)

in the control file I put: 
```
Section: TeX Authoring
Package: texlive-dummy
Description: Dummy package to replace the Ubuntu TeXlive installation.
Provides: texlive-doc-base, texlive-common, texlive-base-bin, texlive-base, tex-
common, texlive-latex-base


```

installed the deb and voila, all the tex dependencies are satisfied!

Hope that helps.

---

### Post by CalvinGhost on 2008-11-19
> **ju2wheels said:**
> You should install it from the repository

Thanks for your link but I precisely don't want to use the package manager for texlive so I can update to 2008 without waiting for the debian installer. Moreover it spares me reinstalling my 2007 distribution.

[QUOTE=tacutu]i also use texlive 2008, which is not in the repos... to get rid of the dependencies issue, I created a dummy .deb useing a nice program called equivs (in the repos)

in the control file I put:
```

Section: TeX Authoring
Package: texlive-dummy
Description: Dummy package to replace the Ubuntu TeXlive installation.
Provides: texlive-doc-base, texlive-common, texlive-base-bin, texlive-base, tex-
common, texlive-latex-base

```
installed the deb and voila, all the tex dependencies are satisfied!

Hope that helps.[/QUOTE]

Thank you for your trick I'm going to try it !

However, isn't there a clean and 'official' way to tell the package manager he should ignore some dependencies ?

---

### Post by tacutu on 2008-11-20
sorry, not a debian guru, but afaik, no. you have to trick your system into believing the dependencies are satisfied, but do not worry: you can uninstall texlive cleanly at any time, it doesn't leave any junk files behind, so there's no worry your system will be messed up.

what's important is that you remember the steps you took (maybe write them down) and is you decide to get rid of texlive, undo them in reverse order. I am happily using texlive2008 in ubuntu. I installed it because I wanted the newer xelatex (which now can do ps-tricks!!). the whole installation lives in /usr/local/texlive (with symlinks in /usr/local/bin), so it doesn't mess up my system. 

if you need more help, let me know.

best,
tacutu

---

### Post by CalvinGhost on 2008-11-21
It's working great, thanks !

---

