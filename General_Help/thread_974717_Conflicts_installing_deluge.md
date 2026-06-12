---
title: "Conflicts installing deluge"
date: 2008-11-07
forum: General Help
---

### Post by miromiro on 2008-11-07
I am trying to install deluge on 8.08 (using apt-get install deluge-torrent). I end up getting this message:

> Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  deluge-torrent: Depends: libboost-date-time1.34.1 (>= 1.34.1-8) but it is not going to be installed
                  Depends: libboost-filesystem1.34.1 (>= 1.34.1-8) but it is not going to be installed
                  Depends: libboost-iostreams1.34.1 (>= 1.34.1-8) but it is not going to be installed
                  Depends: libboost-python1.34.1 (>= 1.34.1-8) but it is not going to be installed
                  Depends: libboost-thread1.34.1 (>= 1.34.1-8) but it is not going to be installed
E: Broken packages

Anyone else encountered (and fixed) this?

---

### Post by stinger30au on 2008-11-07
try doing this

click applications

add remove

set the box to "show all applications"

search on deluge

put a tick next to the box to install it, click on apply and follow prompts, see how that goes

---

### Post by miromiro on 2008-11-07
Thanks - but I get a message: there are conflcits, try Synaptic to sort them out. Synaptic essentially says the same thing...

---

### Post by adult swim on 2008-11-07
from terminal type in ```
sudo apt-get -f install
``` and then try to install deluge again

---

### Post by miromiro on 2008-11-07
Thanks for the suggestion Adult Swim, but no change: same error messsage (in terminal as well as Synaptic)...

---

