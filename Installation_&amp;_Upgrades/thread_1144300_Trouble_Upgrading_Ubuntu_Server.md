---
title: "Trouble Upgrading Ubuntu Server"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by Chernevik on 2009-04-30
I am running Ubuntu Server and am having trouble upgrading.

When I run the following commands, I get the following error messages:

apt-get update 
    -> 'Some index files failed to download . . .'
apt-get install update-manager-core 
    -> 'Install these packages without verification?' Y
    -> 'Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?'
apt-get install update-manager-core --fix-missing
   -> Failed to fetch [snip] 404 Not Found
apt-get upgrade
    -> 'Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?'

Is the server busy?  Or am I doing something wrong here?

---

