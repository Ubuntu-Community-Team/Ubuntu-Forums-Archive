---
title: "Cannot install libasound2-dev"
date: 2008-08-25
forum: General Help
---

### Post by Deten on 2008-08-25
I am trying to install libasound2-dev(1.0.15-3ubuntu4) but when I do from synaptic it says:

```
libasound2-dev:
  Depends: libasound2 (=1.0.15-3ubuntu4) but 1.0.16-0ubuntu0.1 is to be installed

```

But libasound2(1.0.15-3ubuntu4) is not available from repository.

---

### Post by Deten on 2008-08-25
I figured it out:

Go to Synaptic Package Manger-> Package -> Force Version

With libasound2 selected do force version and it lets you use the previous version which then allows you to install the dev version.

---

