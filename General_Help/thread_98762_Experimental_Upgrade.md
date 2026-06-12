---
title: "Experimental Upgrade"
date: 2005-12-04
forum: General Help
---

### Post by wizzomafizzo on 2005-12-04
Is it safe to upgrade an experimental 5.10 system to the newer stable 5.10 system as I only have the 5.10 experimental cd and cannot download another.

Also what is the procedure to do the upgrading?

Thanks for any help.

---

### Post by linbetwin on 2005-12-04
I suppose by "experimental" you mean beta version, preview of release candidate. If you keep that system updated, I think you already have 5.10.

---

### Post by wizzomafizzo on 2005-12-04
So if I just let it do the downloading and such at boot after the installation and just let it upgrade what it needs to it should be fine?

---

### Post by briguy on 2005-12-04
Just install the system and allow it to upgrade.  It will be 100% up to date.

---

### Post by linbetwin on 2005-12-04
So you don't have it installed? If not, install it and after the first boot you'll see a popup telling you that updates are ready for your system (or something like that). Install those updates.

You could also issue these commands:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by wizzomafizzo on 2005-12-04
Problem solved then. Thanks for the help.

---

