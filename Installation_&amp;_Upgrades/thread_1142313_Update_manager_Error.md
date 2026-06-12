---
title: "Update manager Error"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by rob2nd9th on 2009-04-29
When running updates or update manager I keep geting this??

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

---

### Post by kostkon on 2009-04-29
You forgot to add the keys for the repos.
Open a terminal and give
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
and then
```
sudo apt-get install medibuntu-keyring && sudo apt-get update
```
and you should be fine.

---

