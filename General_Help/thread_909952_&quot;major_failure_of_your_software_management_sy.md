---
title: "&quot;major failure of your software management system&quot;"
date: 2008-09-04
forum: General Help
---

### Post by webcrawler559 on 2008-09-04
This message appears when I try to open Add/Remove Applications:

```
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

This, when I try to open Update Manager:
```

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/lib/dpkg/status - open (2 No such file or directory), E:The package lists or status file could not be parsed or opened.'
```

And this when I try to open Synaptic Package Manager:
```

E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

I've tried everything suggested in each of the error codes...and Report a Problem won't open...

...suggestions?

---

### Post by iaculallad on 2008-09-04
Had you tried creating a status file?

```
sudo touch /var/lib/dpkg/status
```

then:

```
sudo apt-get update
sudo apt-get install -f

```

---

### Post by webcrawler559 on 2008-09-04
Thanks...no errors now!

...but how do I repopulate the list with all my currently installed applications...currently it telling me nothing is installed.

---

### Post by iaculallad on 2008-09-04
> **webcrawler559 said:**
> Thanks...no errors now!

...but how do I repopulate the list with all my currently installed applications...currently it telling me nothing is installed.

Try this: Remove the status file again using the terminal.

```
sudo rm /var/lib/dpkg/status
```

and try to copy the status-old file if it exist (we hope):

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Then:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by webcrawler559 on 2008-09-04
Thanks man...that worked perfectly...whoo...I wonder what I did to make it that screwy?

---

### Post by iaculallad on 2008-09-04
> **webcrawler559 said:**
> Thanks man...that worked perfectly...whoo...I wonder what I did to make it that screwy?

Either you had a corrupted status file or "in-our-don't-know" reason, the file got deleted.

---

