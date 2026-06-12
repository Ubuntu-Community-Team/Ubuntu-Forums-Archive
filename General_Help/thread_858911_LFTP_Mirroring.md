---
title: "LFTP Mirroring"
date: 2008-07-14
forum: General Help
---

### Post by sameerarora on 2008-07-14
We are planning to use lftp to mirror some of the files and
directories on to the remote server.

What we exactly want to do is mirror some of the directories and
exclude some of the the directories from "/" i.e. main root. . What
lftp is doing is mirroring all the directories. It seems the include
and exclude doesnt work properly.

The script that we are trying to run is as below:

HomeBackUpDir=/
RemotePath=/data/
lftp -u $RemoteUser,$RemotePass -e "mirror --dry-run --reverse
--delete -I '/home/*/web/' -I '/home/*/data/' -i
'/home/cla_backup/scripts/' -i '/etc/apache2' -X
'/home/*/data/lucene_data/' -X '*data/temp/*' -X '*backup/*' -X
'*templater_cache/*' --only-newer --ignore-time --verbose=4
$HomeBackUpDir $RemotePath" $RemoteHost

What we intend to do is to mirror
/etc/apache2/
in the home/ directory wherever there is a web/ directory mirror that
in the home/ directory wherever there is a data/ directory mirror that
/home/cla_backup/scripts

Exclude:
in the home/ directory wherever there is a data/lucene_data/
/data/temp/
backup/
templater_cache/


The above script tries to mirror even directories like /dev, /proc and
all other directories that are present in "/".

---

