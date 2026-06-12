---
title: "Machine Readable Synaptic History?"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by pgmer6809 on 2009-02-23
One of the annoyances is doing re-installs and having to re-install all the extra packages. Is there a way of saving the names of the packages currently installed in a file that I could then pass to apt-get or the like after I have re-installed ubuntu.
This is necessary as I am running Gutsy, and Hardy and Ibex do not work properly with my system (network issues). If and when the next release of Ubuntu does work, I will need to re-install. I want to be able to automate the re-install of all the packages I have added to Gutsy.
I can write a simple perl script to pass a list of names to apt-get if that is needed, but where do I find the information in a simple easy to use format.

---

### Post by InspiredIndividual on 2009-03-02
> **Cynical said:**
> I found out how to do this recently and thought it might be helpful to some people. To output this information to a file in your home directory you would use,

```

dpkg --get-selections > installed-software

```

And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,

```

dpkg --set-selections < installed-software

```

followed by

```

dselect

```

You may need to use sudo for some of the commands. I found the solution in the following thread: [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366) . I copied a quote here for completeness.

---

