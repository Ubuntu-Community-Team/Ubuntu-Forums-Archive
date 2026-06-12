---
title: "apt-get upgrade size mismatch"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by gannster on 2009-06-22
Is there a way to download all upgrade packages only once?

The questions I have are probably already answered here somewhere, but my search attempts aren't finding the answers.  

I have performed many installs of Linux in the past months. After the install is complete, the update manager will report 100+ updates available.  I go to the terminal window and issue the command 

apt-get update

then

apt-get upgrade --fix-missing

apt-get dutifully tells me there are (for example) 134 packages to download, and begins to download all of them.

After 20 minutes or so, the downloading will cease, and a few of the packages will be installed, but most will be listed as "Failed to fetch http... ... Size mismatch"

Then I type apt-get upgrade -- fix-missing  and apt-get downloads 108 files, and applies 12 of them.  And again so apt-get download 96 files and applies 8 of them.

I'm guessing what is going on is some sort of dependency check.  File fxxx of version vxxx won't install unless file fyyy of version vyyy already is installed.

But, is there anyway I can download all 134 packages only once? I have attempted to do it in stages...

apt-get upgrade --fix-missing --download-only
apt-get upgrade --fix-missing --no-download
apt-get upgrade --fix-missing --no-download

but this approach  doesn't work either.

It seems to be an incredible waste of bandwidth to download a file eight or nine times in a row merely because the version checker is not happy yet.  :confused:

Or am I using apt-get upgrade in the most newbie of ways?

---

### Post by zvacet on 2009-06-22
```
sudo apt-get update && sudo apt-get upgrade
```

should work.

```
sudo apt-get -f install
```

or just try to switch server under** system>admin>software repositories**.

---

### Post by vmsda on 2010-03-12
I had this problem after installing 9.10 from scratch, and I had never had any problems with Update Manager.

So, I went into System > Administration > Synaptic Package Manager > Settings > Repositories : here I unmarked the CD from which I had done the installation, changed the Server from my local one to Main Server, closed, Reload to make the changes effective.

I then recalled Update Manager, and everything ran like a breeze. So here is my experience, for what it's worth.

Cheers.

---

