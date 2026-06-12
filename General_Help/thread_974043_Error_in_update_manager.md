---
title: "Error in update manager"
date: 2008-11-07
forum: General Help
---

### Post by SamSlater on 2008-11-07
Im getting the following error when checkin for updates using both the update manager and terminal:

> [FONT="Courier New"]"Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  multiversedeb/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead."[/FONT]

My network connection is fine and I've had no trouble installing anything from the repo's (for now).

Can anyone tell me what it means and if it's a problem? It only started after I installed Picasa, yesterday.

Thanks.> [QUOTE][/QUOTE]

---

### Post by dburnett77 on 2008-11-07
> **SamSlater said:**
> Im getting the following error when checkin for updates using both the update manager and terminal:



My network connection is fine and I've had no trouble installing anything from the repo's (for now).

Can anyone tell me what it means and if it's a problem? It only started after I installed Picasa, yesterday.

Thanks.


try

sudo apt-get update

then,

sudo apt-get upgrade


If that doesn't correct it, I hate to say it, but I'd go with a re-install.  There's so many hacks available these days to any goer that there just so easy; and it may be the case you downloaded a contaminated file.

And, although I've not recommended it before:  clamav, clamav-daemon, and if you want clamtk for the gui is highly recommended.  I used to not have trouble with virii, but these days it's different.  There available in synaptic.

---

### Post by SamSlater on 2008-11-07
Thanks for the quick reply, dbunett77.

"sudo apt-get update" returns with the same error:
> W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  multiversedeb/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.


"sudo apt-get upgrade" returned with no errors but it didn't solve the errors for update and update manager.

I'll do a reinstall and take notice on what packages I'm installing incase it happens again.

Thanks for the help.

P.s. Plural for 'virus' is 'viruses' ;-b ...I know, 'virii' sounds better doesn't it?

---

