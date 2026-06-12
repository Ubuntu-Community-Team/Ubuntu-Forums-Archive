---
title: "critical files and directories to backup?"
date: 2008-10-29
forum: General Help
---

### Post by ryharv on 2008-10-29
Hello,

I use my ubuntu machine primary as a *destination* for backing up my Apple laptop.  But it occurs to me that I might be wise to backup some elements of Ubuntu as well.

I'm thinking things like apache config files, the ssh keychain, networking preferences, any other configuration files.  

Any recommendations for a single directory or set of directories that I should, as a matter of practice, keep backed up on an external drive (likely back to my laptop) -- in case my ubuntu machine's hard drive fails and I need to reinstall the OS without having to reconfigure everything?

I don't need any system files that could be found on a regular Ubuntu install CD -- just anything that has become customized.  I suppose I am wondering if these customized files would all likely reside in the same place.  

Thanks for your help!!

---

### Post by sdennie on 2008-10-29
I would recommend installing Simple Backup.  The default things it decides to backup are a good starting point:

```

sudo apt-get install sbackup

```

Then System->Administration->Simple Backup Config

I don't recall if it does a backup of all of /etc by default but, if not, that's a good thing to have backed up.  Determining what to backup will always depend on how you use your system but, Simple Backup is a good start.

---

