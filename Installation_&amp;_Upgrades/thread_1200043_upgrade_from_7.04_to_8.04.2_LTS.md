---
title: "upgrade from 7.04 to 8.04.2 LTS"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by Brigitte Seib on 2009-06-29
I know 7.04 is EOL and 7.10 is also EOL. 
I would like to do a clean install of 8.04.2 rather then upgrading to also EOL 7.10 and then from there to 8.04.2

Is it possible to use the saved software list to reinstall all the applications on 8.04.2
from:
dpkg --get-selections | grep -v deinstall > installed-software.log
etc ..
see:
[http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)

Or will this no work since the sources.list file will be different?

---

### Post by raymondh on 2009-06-30
> **Brigitte Seib said:**
> I know 7.04 is EOL and 7.10 is also EOL. 
I would like to do a clean install of 8.04.2 rather then upgrading to also EOL 7.10 and then from there to 8.04.2

Is it possible to use the saved software list to reinstall all the applications on 8.04.2
from:
dpkg --get-selections | grep -v deinstall > installed-software.log
etc ..
see:
[http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)

Or will this no work since the sources.list file will be different?

Hello Brigitte Seib,

Interesting link .. thanks for sharing.... it'll be bookmarked for me :)

I don't think it will work because as you change versions, so does your sources.lst.  I think it will work in scenarios where you need to re-install the same version.

I may be wrong..... why not try?  I would myself but currently have no need to change versions as I am still waiting a bit longer to see how karmic develops.

---

