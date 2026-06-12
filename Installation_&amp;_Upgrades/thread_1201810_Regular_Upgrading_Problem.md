---
title: "Regular Upgrading Problem"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by derbay2002 on 2009-07-01
Hello,

I have been trying to do a regular upgrade. However, I am getting the following error message:
Error authenticating some packages
It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages:

initscripts
sysvinit-utils


Any help will be greatly appreciated. 

Thank you.

---

### Post by lemming465 on 2009-07-03
You don't say which version of Ubuntu you are running, nor which country and timezone you are in, so any advice here is going to be kind of generic.

Typically this is the result of a repository replication problem, so that you accidentally downloaded corrupted package files.  If their checksums don't match the digitally signed manifest, you very rightly get an authentication error.

First thing to try:```
sudo aptitude clean
```
This will clear out previously downloaded *.deb package files from /var/cache/apt/archives.  Freshly downloaded copies might be correct.

Second thing to try: download from a different mirror of the repositories.  Your initial mirror is selected automatically to give good bandwidth based on your Timezone city choice.  The easiest way to try a different mirror is to go to System -> Administration -> Software Sources and use the *Download from* drop-down button dialog to try somewhere else.

If neither of those helps, the third thing to try is removing all 3rd party repositories, if you had added any.

---

### Post by cariboo on 2009-07-04
Adding to what lemming465, before attempting an upgrade make sure any third party repositories and ppa's are disabled. Also make sure you current version is up-to-date.

---

