---
title: "I installed unauthenticated software - now what?"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by pkid on 2009-07-07
So the update manager pops up this morning with some updates to Pidgin.  No problem I click install.  A little while later I log into another machine and the same process happens but before I click the install button I notice that there are some pieces of software that could not be authenticated (hal, libhal1, libhal-storage1)  and that there is a dire warning that people could take over my PC, the world and generally cause the end of human civilisation.  

When I click on the "Check" button on the update manager I get the following error:  W: GPG error: [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I went into Synaptic and it looks like the unauthenticated packages are coming from za.archive.ubuntu.com/main.  How do I know that the packages I installed this morning are fine?  It is very annoying.  There should be an option to block the install of unauthenticated software and it should be set to "on" by default.

---

### Post by spcwingo on 2009-07-07
Run this:

```
gpg --keyserver subkeys.pgp.net --recv 40976EAF437D05B5
```

followed by:

```
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -
```

That will get rid of the errors.

---

### Post by Tibuda on 2009-07-07
> **spcwingo said:**
> Run this:

```
gpg --keyserver subkeys.pgp.net --recv 40976EAF437D05B5
```

followed by:

```
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -
```

That will get rid of the errors.

Or only
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```

---

### Post by pkid on 2009-07-07
Cool.  So the issue was that the keys were corrupt or it got the wrong key etc?  I don't need to reload the OS or anything cause if I got the packages from the Ubuntu repo it should be okay and not malware or something that could nuke my machine?  I must admit that the warning message is pretty scary :) 

Thanks for the answers.

---

### Post by Tibuda on 2009-07-07
[http://za.archive.ubuntu.com/](http://za.archive.ubuntu.com/) uses ubuntu.com domain. I would be careful with different domains.

---

### Post by pkid on 2009-07-07
I was using my 3G wireless connection on the small laptop and an ADSL connection on my other machine.  Tried to refresh the package info using the wireless connection and it gives me the error about the key and installing unauthenticated software.  Do the same refresh with the ADSL connection and no problems. 

Looks like it might be related to this: [http://ubuntuforums.org/showthread.php?t=786050&highlight=update+key+invalid+cache](http://ubuntuforums.org/showthread.php?t=786050&highlight=update+key+invalid+cache)

All that stressing for nothing!

---

