---
title: "Repositories not working... can't download using sudo apt-get"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by headbangerbuggy on 2009-07-11
I'm trying to obtain the manager for Compiz on Jaunty Jackalope.


Doesn't work using the standard sudo apt-get install compizconfig-settings-manager

and I can't find it using Synaptic. I can't find ANYTHING using Synaptic.


The problem is that it's not connecting to the repositories.
Obviously my internet is working and I just installed Jaunty an hour ago so the repos are enabled by default(Though, I checked just in case.)

Yet I get the lame:

E: Package compizconfig-settings-manager does not exist.

Or 'could not be found' or whatever it says.
You get the point :)

The problem is that I can't obtain any packages.
Help?

I'm stuck :\

---

### Post by oldos2er on 2009-07-11
Can you run this command in a terminal, and post the output here:
```
sudo apt-get update && sudo apt-get install compizconfig-settings-manager
```

---

### Post by zvacet on 2009-07-11
System>admin>software sources>check all under Ubuntu software except source and first two under updates.Reload.Try if you can install what you want now.If not run in terminal

```
sudo apt-get update && sudo apt-get upgrade
```

and post output here to see if there is any errors.

---

