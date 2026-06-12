---
title: "upgrade from 8.04 to 8.10 without reinstalling?"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by querent on 2009-03-06
Hey.  Newbie question.  How do I (I feel it must be possible) upgrade from 8.04 to 8.10 without running a fresh install.  Update manager never asked (like it used to), and I'd like to.

Thanks in advance!

---

### Post by jpeddicord on 2009-03-06
It's because 8.04 is a LTS release, so it won't notify you by default.

See [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) for information on how to upgrade, namely the "Before you Begin" part. :)

---

### Post by tommcd on 2009-03-07
To upgrade from Hardy to Intrepid see this:
[https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

---

### Post by querent on 2009-03-09
Thanks!

---

### Post by Neo_The_User on 2009-03-09
or just do this command from a terminal.

```

gksudo update-manager -d

```

---

### Post by jpeddicord on 2009-03-10
> **Neo_The_User said:**
> or just do this command from a terminal.

```

gksudo update-manager -d

```

That will only work for upgrading to a pre-release version. The -d flag should not be used for upgrading between stable releases.

---

