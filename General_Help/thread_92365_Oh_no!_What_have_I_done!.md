---
title: "Oh no! What have I done!"
date: 2005-11-19
forum: General Help
---

### Post by HunterCo on 2005-11-19
Okay, here's my situation...
I tried a couple different ways of installing OpenOffice.org 2 Final, most of which left me with a very shaky, "crashes all the time" product. While cleaning out some old files before my most recent install, I deleted the file update-openoffice-dicts (I don't remember where from, I just remember killing it).

Ironically, the most recent install of OpenOffice 2 Final works like a champ, except that I have this growning problem with synaptic/apt/dpkg. Below is the error I'm getting... I have tried reinstalling a number of packages, but cannot find the one with the file I deleted (named above). Can someone please tell me how to remedy this?

```
Setting up myspell-en-gb (20050823-1ubuntu1) ...
/var/lib/dpkg/info/myspell-en-gb.postinst: line 6: update-openoffice-dicts: command not found
dpkg: error processing myspell-en-gb (--configure):
 subprocess post-installation script returned error exit status 127
Setting up myspell-en-us (20050823-1ubuntu1) ...
/var/lib/dpkg/info/myspell-en-us.postinst: line 6: update-openoffice-dicts: command not found
dpkg: error processing myspell-en-us (--configure):
 subprocess post-installation script returned error exit status 127
Setting up openoffice.org2-common (2.0.0-0ubuntu1) ...
/var/lib/dpkg/info/openoffice.org2-common.postinst: line 11: update-openoffice-dicts: command not found
dpkg: error processing openoffice.org2-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of language-support-en:
 language-support-en depends on myspell-en-gb; however:
  Package myspell-en-gb is not configured yet.
 language-support-en depends on myspell-en-us; however:
  Package myspell-en-us is not configured yet.
dpkg: error processing language-support-en (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 myspell-en-gb
 myspell-en-us
 openoffice.org2-common
 language-support-en
```

---

### Post by gapplewagen on 2005-11-19
Have you tried running this install with the -f (fix broken) option for apt-get?

sudo apt-get -f install [packagename]

---

### Post by HunterCo on 2005-11-19
[QUOTE=gapplewagen]Have you tried running this install with the -f (fix broken) option for apt-get?

sudo apt-get -f install [packagename][/QUOTE]
That didn't work- it gave the same response/error.

I also get the error if I try to run dpkg --configure -a

I'll try the overly simple copying of the file from a different Ubuntu system for now, but I'd really like to know what package is responsible for that file just in case I get a brain fart, do something like that again, and don't have another system handy to copy from.

---

### Post by HunterCo on 2005-11-20
So I fixed the problem- but to tell you the truth I'm not sure specifically what did it. I know it was in relation to removing certain dictionary packages- I must have just found the correct one that used the file. Wish I would remember the specific one that it was, but since it works now I'm not too worried about it. Thanks all! See you around the forums!

---

### Post by gapplewagen on 2005-11-21
[QUOTE=HunterCo]So I fixed the problem- but to tell you the truth I'm not sure specifically what did it. I know it was in relation to removing certain dictionary packages- I must have just found the correct one that used the file. Wish I would remember the specific one that it was, but since it works now I'm not too worried about it. Thanks all! See you around the forums![/QUOTE]


Did you end up copying these files from another Ubuntu machine?

---

### Post by HunterCo on 2005-11-21
[QUOTE=gapplewagen]Did you end up copying these files from another Ubuntu machine?[/QUOTE]
I didn't copy the file from another computer. I was able to finally find the program that used it, and by removing that package, my system was no longer trying to update whatever it was trying to update. I'm a little confused by how I fixed it- if it was an important file enough that installing other packages required it to run, why did removing the package fix it? I believe it was one of the MySpell packages, though, as the packages that gave errors with the file missing were openoffice packages...

So did that even answer your question? :confused:

---

### Post by kruz on 2005-11-21
make SURE that u purge the packages config files it left

im not sure
man apt-get and man dpkg

---

### Post by HunterCo on 2005-11-22
Yeah-
Any time I remove a package in Synaptic, I use the "Remove Completely" option. I can't stand having things left behind. You should have seen my pulse quicken back in the MS Windows days when I'd take a look at the registry only to find *TONS* of left overs from things long gone... :) I'm confident in knowing, though, that it's a pet peeve worth having.

---

