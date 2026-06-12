---
title: "Firefox upgrade splashy conflict"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by cwsnyder on 2009-06-15
I am not sure this is the place to report a bug during an upgrade.  I searched the forums for 'Firefox 3.0.11 upgrade' with no results.

I ran into a problem which stopped the ```
sudo apt-get update
sudo apt-get upgrade
``` process in its tracks during the upgrade to Firefox 3.0.11.  I forgot to save the error message, but it was because the package **splashy** was using one of the log files in /etc which would have been affected by the upgrade.  Using ```
sudo rm filename
``` I removed the offending file as a trial to see if that would allow the process to continue.  This did not work.  This was Saturday, June 13.  Tonight (Monday, June 15) I decided, since splashy was having problems which I had not had enough time to troubleshoot, that I would simply remove splashy with ```
sudo apt-get remove splashy
``` which removed splashy and a file that depended on it.  I finally was able to get the upgrade process to finish after removing splashy.

This is more of a notice that I solved a problem than a question, but I am open for questions and will check back tomorrow to see if there are any comments and/or questions;)

---

