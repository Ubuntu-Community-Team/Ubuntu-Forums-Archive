---
title: "Compozer crashes"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by Brian_G_M on 2009-03-01
Hi,

Yesterday I upgraded to the latest version of Ubuntu. Today I am trying to use Compozer to edit a website, and it  keeps crashing. I use it for maybe 20 or 30 seconds, then it just disappears - no warning, no error message. I can reopen it and try again, same result.

Can anyone help?

Thanks

---

### Post by thatguyisjames on 2009-03-26
i have the same issue on my acer aspire one (eeebuntu 8.10, gnome 2.24.1)

i found: [http://ubuntuforums.org/showthread.php?t=1094500](http://ubuntuforums.org/showthread.php?t=1094500)

after using 

```
sudo apt-get autoremove kompozer
```

to clean up the not so good version of kompozer

i then downloaded kompozer---.tar.gz
from: [http://kompozer.net/download.php](http://kompozer.net/download.php)

```
wget http://superb-east.dl.sourceforge.net/sourceforge/kompozer/kompozer-0.7.10-gcc4.0.3-i486.tar.gz
```

unziped

```
tar -xvzf kompoz[COLOR="DarkOrchid"]tab[/COLOR]
```
```
cd kompoz[COLOR="DarkOrchid"]tab[/COLOR]
```
```
./kompozer
```

works, but

its not installed

made a work around 

```
cd ..
```
```
sudo mv kompoz[COLOR="DarkOrchid"]tab[/COLOR] /usr/share/kompozer/
```

then just created a launcher with the menu editor for kompozer

hehe, works for me, and no crashing, now time to make some web pages,

hope this helps

---

