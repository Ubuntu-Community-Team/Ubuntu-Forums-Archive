---
title: "themse and other eye candy stuff....need help, please"
date: 2005-11-12
forum: General Help
---

### Post by nikolai.m on 2005-11-12
kde-look.org....tha place to be for eye candy stuff for your favorite KDE desktop. well....i downloaded several icon themes and desktop themes in common tar.gz files. i go to system settings (kubuntu 5.1) - icons - install new theme - ... and i get error :"the file is not valid icon archive file" /???? what's this all about?
i downloaded nuvola icon theme and it installed just fine. but for example oo.o ikde icon theme 0.01 gets me this error message.
any idea how can i fix this?
thnx

---

### Post by Juippisi on 2005-11-12
Download the icon-theme to your home directory, then open terminal. Follow:
```
::{ joonas@freedom (03:15:48) - ~ }::
::-» ls
amsn_received  Desktop  hdb2                     koulu  omat            pelit              programs            setups  torrents           box.jpg
antura         hdb1     Japanese Translator.rar    OperaDownloads  plista-amarok.m3u  realituxBG.tar.bz2  tmp

::{ joonas@freedom (03:15:58) - ~ }::
::-» tar -xjvf realituxBG.tar.bz2
<some files here>

::{ joonas@freedom (03:16:13) - ~ }::
::-» mv realituxBG .icons/
```

Now open kcontrol and go to icons. Your icon-theme should be there.

Themes can be installed by extracting the theme-package and browsing the .theme from kcontrol.

---

