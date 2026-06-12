---
title: "what is already installed since clean install"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by honda4life on 2009-02-19
Hello everyone,

I'm a beginner with Ubuntu,
Is it possible to keep track of what i have already installed in synaptics, something similar to "windows software",

i also want to know if I installed a main package, and it installs other required packages, if I afterwards remove the main package, the other required packages will be removed to?

I like a very clean system :D

The last question is, can I make linux battery life as long as windows battery life, it can be a lot better on linux, is there somebody who did better than windows?

---

### Post by cariboo on 2009-02-19
Go to System-->Administration-->Syunaptic Package Manager-->File-->History, for a list of installed packages. To clean up no longer needed dependencies,
open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get autoremove
```

To remove archived packages type:

```
sudo apt-get clean
```

Remember Linux is not Windows, installed programs  only take up space on the hard drive, and don't use any ram until they are run, and release the ram when  they are closed.

Jim

---

### Post by oldos2er on 2009-02-19
To see installed packages in Synaptic, click 'Status,' 'Installed.'

 "sudo apt-get autoremove" will remove dependencies for packages no longer installed.

---

