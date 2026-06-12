---
title: "Jaunty update? what gives"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by zaphodbblx on 2009-04-23
so Im all excited to get the release version(I was running beta) and i've tryed every method I could find to do upgrade and no luck.( even cant upgrade from the iso image or burnt disk and it even shows in my software sources!) when I check version it says im running 9.04 but I never upgraded to the release version and my manager says all packages are 20 days old.
  I do this:

brian@dell-desktop:~$ sudo do-release-upgrade
Checking for a new ubuntu release

I get this:

No new release found

Id so hate to wipe my drive rather than upgrade..any ideas?

---

### Post by Newfoundlander on 2009-04-24
What about under System>Administration>Update Manager?  Does it show an upgrade to Jaunty there?

If not, you may need to check the settings in Software Settings.  I'm in the process of restarting my upgrade so I can't check those details right now.  You should also have Ubuntu 8.10 up-to-date before starting the upgrade.

---

### Post by Partyboi2 on 2009-04-24
If you are using the beta version and are  up to date with all your updates you are running the final release of Jaunty.

---

### Post by dsnettleton on 2009-04-24
So you're already running the beta version of Jaunty, but it won't let you download the actual Apr. 23 "release" version.

Are they the same?  That doesn't seem right.  You'd think the final release would be a different build from the beta release.

---

### Post by Sef on 2009-04-24
Applications >  Accessories > Terminal

then copy and paste (or type) in this code:

```
sudo apt-get update && sudo apt-get upgrade
```

If you are using a beta version, then it will upgrade to the stable verion.

---

### Post by zaphodbblx on 2009-04-24
> **Sef said:**
> Applications >  Accessories > Terminal

then copy and paste (or type) in this code:

```
sudo apt-get update && sudo apt-get upgrade
```

If you are using a beta version, then it will upgrade to the stable verion.

it appears I was overthinking all of this! Thanks all! I had been keeping up to date all month so there ya' go!

---

