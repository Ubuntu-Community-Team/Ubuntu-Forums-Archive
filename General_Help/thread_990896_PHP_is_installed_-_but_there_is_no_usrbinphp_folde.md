---
title: "PHP is installed - but there is no usr/bin/php folder?"
date: 2008-11-23
forum: General Help
---

### Post by nappymonster on 2008-11-23
I'm running torrentflux B4rt, and it said there is no folder /usr/bin/php
I thought it strange as I had installed it (i checked - sudo apt-get install php5 returns already at latest version), but there is no folder. I need it for a certain aspect (fluxd) of torrentflux.

I need to know the path for:

"Specify the path to the commandline (cli) php binary (/usr/bin/php)."

thanks,
Nappymonster

---

### Post by jrib on 2008-11-23
Are you using the torrentflux package from the repositories?  I don't use this program myself, but you should read /usr/share/doc/torrentflux* and check bugs.ubuntu.com as it sounds strange that you should have to input this path yourself.  If those two things do not turn up any useful information, then you may need to install the php5-cli package which provides /usr/bin/php5.

---

