---
title: "rsync: mkstemp fails when filename has 'special' characters"
date: 2008-09-29
forum: General Help
---

### Post by skelooth on 2008-09-29
Long story short: I need to back up a folder of images that have  bad characters in them (such as # and ?). These are files not created by me. "Fixing them" will break their associations in a related database (it's over 5k of files). 

Really, I don't want to have to write a script to fix the file names both in the FS and the DB because it leaves room for error on my part. Is there anyway to make rsync work with the tainted file names? I've tried changing the temp directory but it still gets that same problem. After googling a great deal I am 99% sure it has to do w/ the file names

```

rsync: open "/mnt/backups/nix_server/www/image_catalog/DBA_96/.~tmp~/DBA_96HOS-7CapobiancoInviteHOS-7Sinatraphotoslogo?singlesjpg.gif": No such file or directory (2)

```

---

### Post by skelooth on 2008-09-29
[shameless] bump. I know this is a different type of question than the board is used to, considering there seems to be no answer on the googles.

---

### Post by skelooth on 2008-09-30
I'll give it one last bump to see if anyone can help. I temporarily got around it by taring the files for the purpose of rsyncing then --excludeing the directory w/ all the funky names.

---

