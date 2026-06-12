---
title: "strange behavior after upgd on Dell Dim 4300"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by EricLorenz on 2009-10-31
P4, 1.6Ghz, 512Mb, 9.04 previously installed.

I too plunged in with both feet and started an upgrade last night. Was going to take several hours- went to bed, checked in the morning...all *seemed* to be fine. 2issues found later:

- gnometris...runs REALLY slowly, pieces are bigger than normal (almost like it's running at a different resolution than everything else).

( I know this seems petty, but this and Mahjongg are my 2 stress break games I play. Mahjongg works fine).

- I run an app called CQRLog (Amatuer radio logging program). Worked fine before...now when I try to start, I get:
"Can't load library: /home/eric/cqrlog/lib/libfembed.so.2.1.1." Checked, file is there.

- I chose to keep the unsupported packages during the upgrade, thinking there might be ones used by some apps I am running. So, went into options for package manager and selected 'unsupported packages' under sources. Now...

- I cannot update the package lists. When I go into package manager, I get errors, or it hangs searching.

Still learning here, fairly new Ubuntu user...any help appreciated.

Thanks!
Eric Lorenz

UPDATE--- Been doing more poking around on the game issue...thought I'd try uninstalling and re-installing Gnometris (Gnome games) and when I did that, i got an error saying that the source for those titles was not recqnized. When I went into Software sources, and checked the jaunty(source code) box, it installed, but same performance.

So, I guess that this package is not optimized for 9.10 somehow?

Eric

---

