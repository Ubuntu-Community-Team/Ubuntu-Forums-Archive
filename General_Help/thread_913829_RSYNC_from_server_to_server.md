---
title: "RSYNC from server to server"
date: 2008-09-08
forum: General Help
---

### Post by chrislynch8 on 2008-09-08
Hi,

I have two servers, I use rsync to backup a subserver and my main server and I back my main server to a USB Drive.

RSYNC works fine when I'm backing my server to the USB Drive but when I'm backing up from sub server to main server (just the home directory) - rsync won't transfer anything that has the permissions 700 - or anything that dosn't allow others or group access.

In the home folder I have users private directory as well as open shares so I need to keep the permissions...

I have the sub server running as a daemon and the main server connects in using

rsync -avz server02::home /backups/server02

::::::This is now solved it was the option to enter the uid and gid in the modules::::::::

---

