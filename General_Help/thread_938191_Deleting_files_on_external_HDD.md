---
title: "Deleting files on external HDD"
date: 2008-10-04
forum: General Help
---

### Post by one_ro on 2008-10-04
Hi all,

I have a question about using external HDDs. I use one to back-up my data, and from time to time I need to delete old files from that HDD.

The trouble is, when deleting some files, Kubuntu does not create a .Trash folder on the external HDD but it insists on using the local trash, in:
$HOME/.local/share/Trash/

This has two unwanted effects:
1. The deleted files eat up my local drive (and sometimes I need to delete GBs of files)
2. It takes forever to delete some files, because they get transfered on the local computer (in the local trash).

I remember in the past that Kubuntu created remote Trash folders, is there a way to enforce that?

Thanks very much in advance,
Adrian

---

### Post by SuperSonic4 on 2008-10-04
I'm not sure how you'd do that although creating a directory such as /media/external/.trash and redirecting it's deletions to their might work?

You could just do shift+delete or ```
rm -rf <file or directory>
```. Preface with sudo if you need to be root.

Both of these will **immediately** delete your data with no easy means of recovery

---

### Post by one_ro on 2008-10-04
Right, this might be a better solution.
Deleting from the command line seems both fast and avoids the Trash problem.

Cheers,
Adrian

---

