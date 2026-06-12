---
title: "problems upgrading from 7.04 to 7.10"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by HeyItsMatt on 2009-02-10
Hey everyone, I am trying to upgrade from an existing 7.04 installation to 7.10 (a little behind, I know).

At first I was having problems in terms of getting an 'Error during update' coupled with a bunch of "failed to fetch (web address) 404 not found" messages, regardless of what server I was using under 'software sources'.  I changed my sources.list file to comment out the feisty repositories and add 'old-releases' repositories so that it now looks like this:

```

# deb http://archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
# deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

# deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
# deb http://archive.ubuntulinux.jp/ubuntu-ja edgy/
# deb http://ubuntu.beryl-project.org feisty main
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
```

However, I am now getting this message:

```
No valid mirror found

While scanning your repository information no mirror entry for the upgrade was found.This can happen if you run a internal mirror or if the mirror information is out of date.

Do you want to rewrite your 'sources.list' file anyway? If you choose 'Yes' here it will update all 'feisty' to 'gutsy' entries.
If you select 'no' the update will cancel.
```

If I choose 'yes', I get the same error message I was originally getting:

```
Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz 404 Not Found
```

So, what's going on here? Am I missing something in my sources.list? Eventually I can just give up and do a clean install, but I assume that will cause me a whole different set of headaches, so I'd like to see if there is a solution here first.

*EDIT* I do not think my network connection is the problem, as I am posting this from the same computer and can access the internet while attempting to do all this.  And I was able to successfully download some file using Synaptic Package Manager.

---

### Post by zvacet on 2009-02-12
Look [here]("https://help.ubuntu.com/community/EOLUpgrades") and maybe you find it helpful.

---

