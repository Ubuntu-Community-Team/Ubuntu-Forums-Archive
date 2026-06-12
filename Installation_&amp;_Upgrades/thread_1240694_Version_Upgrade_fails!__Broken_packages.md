---
title: "Version Upgrade fails?!  Broken packages?"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by Support the 2nd on 2009-08-15
I am running 8.04, but when I install my updates, i am told I can upgrade to the new version.  However when I do that, it fails.

It will download and verify the upgrade tool with the Upgrade Wizard, I click Finish to launch, it start doing stuff, but then I get a window for "Could Not Calculate the Upgrade".

E:Unable to correct problem, you have held broken packages.


So whats my next move?

---

### Post by Partyboi2 on 2009-08-15
Hi, open a terminal and try
```
sudo apt-get -f install
```

---

### Post by Support the 2nd on 2009-08-15
Found 16 files that were no longer need so I removed them and tried installing again.  No luck.  Same error.

EDIT:  I did a clean install and am running gnome now too.

---

### Post by ptn107 on 2009-08-15
Verify that your /etc/apt/sources.list file looks EXACTLY like this one: _[http://paste.ubuntu.com/253631/]("http://paste.ubuntu.com/253631/")_  With NO third-party repositories in it.  Each line on the page is numbered, ignore those.

---

### Post by Support the 2nd on 2009-08-15
> **ptn107 said:**
> Verify that your /etc/apt/sources.list file looks EXACTLY like this one: _[http://paste.ubuntu.com/253631/]("http://paste.ubuntu.com/253631/")_  With NO third-party repositories in it.  Each line on the page is numbered, ignore those.

I can't, I reformated my drive.  :/

---

