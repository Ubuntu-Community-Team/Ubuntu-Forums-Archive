---
title: "Error while searching for updates"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by orion1315 on 2009-07-14
W: GPG error: [http://repository.cairo-dock.org](http://repository.cairo-dock.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1392A97E41317877
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

This is im sure, a HUGE problem because if i cant get updates, well, thats bad.
It starts looking for updates and it gets to like 50 or so then it shows the error and goes back to the blank update thing.

Please help :( new to ubuntu here.

Edit: now the update manager window wont close and alt f4 isnt workin

---

### Post by Partyboi2 on 2009-07-15
Hi, looks like you need to add the keys. Open a terminal (Applications>Accessories>Terminal) and add the wine key
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```then for the other one
```
wget -q http://repository.cairo-dock.org/cairo-dock.gpg -O- | sudo apt-key add -
```then
```
sudo apt-get update
sudo apt-get upgrade
```

---

