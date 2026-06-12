---
title: "Will I need to change my virtual SWAP file when upgrading, if so, how?"
date: 2008-10-21
forum: General Help
---

### Post by chumchum on 2008-10-21
Hello all
I have Ubuntu 8.04 installed with Wubi, when installing I had 1.12GB of RAM. Wubi made a virtual SWAP disk which occupies 953MB.
I want to change one of my chips so that my PC has a total memory of 2GB, when I do this will I need to resize the virtual SWAP disk, and how?
Many thanks in advance.

---

### Post by ago on 2008-10-21
No need. Swap as large as memory is mostly a requirement for hibernation, but hibernation does not work in Wubi... So no need to change that, 1G is more than enough in most situations.

---

### Post by chumchum on 2008-10-21
Cool, thanks.

---

