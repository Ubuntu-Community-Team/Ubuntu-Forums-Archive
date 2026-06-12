---
title: "Some issues finding servers and repositories"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by themadjester on 2009-09-10
could not download all repository indexes

and fails

if I select "upgrade" (from feasty fawn to 9.xx or whatever is newer that it found) I get "could not find release notes, the server may be overloaded. (unlikely). 

in another thread someone had to edit their sources file, I used to command to view it... I have no idea what I should change these URLs to however (presumably some are obsolete?). 
gksudo gedit /etc/apt/sources.list:

# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse

For me this should all be "out of the box" as I have never really done a lot with Ubuntu since installing it over a year ago until recently.

sudo apt-get update
results in: Some index files failed to download, they have been ignored, or old ones used instead.

synaptic does not work either, but I'm thinking I'll work on it after this is fixed incase its the same route cause (likely).

Thanks,

Jester

---

### Post by damontallen on 2009-09-10
I'm having similar issues but I am also having a problem with CheckGmail not being able to log onto the gmail server.
Ubuntu 9.04 Kernal 2.6.28-15
AMD 64 Processor 3500+
Memory 1.8 GiB

---

### Post by Vector_Matt on 2009-09-10
> **themadjester said:**
> ...
According to this: [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
Ubuntu Feisty Fawn is no longer supported, which is probably why you can't download any updates. Probably.

---

### Post by damontallen on 2009-09-10
But I'm running Jaunty and I'm having the same problem.  When trying to reload in Synaptic I get the following error messages.

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.46), connection timed out [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/Release.gpg)  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/restricted/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/main/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/universe/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.46 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by andhar on 2009-09-10
I am having the same issues. Did the repository urls change? I honestly don't want to set my server back up. I am running 7.10 btw.

---

### Post by Vector_Matt on 2009-09-10
As for that, it appears that the primary server, the US server, and the Canadian server are all down (and maybe others).

If you want to update now you could try this:
> **Vector_Matt said:**
> So for those having trouble, go to "Software Sources" in the system menu, and select a different download location in the "Download from:" box (select "other", then try a different country), then update as usual. (checking back with the main and us servers every once and a while to see if they're back up.)

Hopefully whatever the problem is will be resolved soon.

---

### Post by andhar on 2009-09-10
> **Vector_Matt said:**
> As for that, it appears that the primary server, the US server, and the Canadian server are all down (and maybe others).

If you want to update now you could try this:

Once you've added that, go to "Software Sources" (probably in the system menu) and select a different download location in the "Download from:" box, then update as usual. (checking back with the main and us servers every once and a while to see if they're back up.)

Resource not available. What is funny is that the Distribution Upgrade still works and I am using it right now.

---

### Post by Vector_Matt on 2009-09-10
According to this: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)
7.10 isn't supported anymore, which is probably why upgrade works (newer versions are supported) but why updates don't work (this version isn't).

---

### Post by themadjester on 2009-09-12
Thanks for the info.

It looks like I'll just burn the 9.04 disk and update the ol' fashion way. 

I am hoping this will be relatively painless and I should be able to just install it over 7.xx in the same partition. I don't really have any data in that partition that I care for anyways.

Thanks all.

---

### Post by themadjester on 2009-09-12
hmmm no dice... do this is moving into somewhat different territory...

When I attempt to install 9.04 from my bootdisk, the menu pops up fine and everything, but proceeds to hang after I make a selection...

I seem to recall from before that there should be some sorts of status updates as the os code is loaded from the CD into memory (I have 4 GB... should be enough ;)

I did a privative look through the directories of the CD in my current installation but it could still be a bad CD I suppose, so I will burn another but if anyone has any input please let me know.

edit: turned out the CD was bad after all. Thanks all

---

