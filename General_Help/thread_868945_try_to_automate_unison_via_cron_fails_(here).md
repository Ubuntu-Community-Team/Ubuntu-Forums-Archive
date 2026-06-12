---
title: "try to automate unison via cron fails (here)"
date: 2008-07-24
forum: General Help
---

### Post by gercokees on 2008-07-24
Hi,
I try to automate a unison-sync using a root cron-job. I can see it is propagating changes but it does not copy all the files which have been changed. When i ran the job once manually the next cron-jobs will succeed. 

Any ideas?

Thanx in advance...
This is my preferences file:

```
# Unison preferences file
# General prefs
logfile = /home/gercokees/bin/log/unison.log
auto = true
group = true
owner = true
prefer = newer
#times = true
batch = true

root = /home
root = ssh://root@laptop//home

# Paths to keep in sync
path = gercokees/docjes
path = gercokees/bin
path = gercokees/afb/2009
path = gercokees/afb/2008
path = gercokees/afb/2007
path = gercokees/.gconf
path = gercokees/.gconfd
path = gercokees/.themes

# Individual files
path = gercokees/.mozilla/firefox/gercokees.default/places.sqlite
path = gercokees/.gnome2/f-spot/photos.db

# Some regexps specifying names and paths to ignore
ignore = Name temp.*
ignore = Name *~
ignore = Name .*~
ignore = Name *.o
ignore = Name *.tmp
ignore = Name *.log
ignore = Name {,.}*{.lock}
ignore = Path projects/.metadata

```

---

### Post by roquefilipe on 2008-07-24
I have found that some problems with cron are due to different environments. check this [http://linuxshellaccount.blogspot.com/2007/10/crontab-and-your-environment.html](http://linuxshellaccount.blogspot.com/2007/10/crontab-and-your-environment.html)

Try to give full paths to all programs and files. also dump any errors to a log file. Append ">> logfilename" to the command to do that.

---

### Post by gercokees on 2008-07-25
Hi,
Thanx for your comment but i am almost sure this is not the problem.
The job starts very well and unison is correct propagating changes (according to logfiles) and starts syncing those. But a few seconds after the start the process stalls usualy after 10 - 12 files. I have not any clue why this happens...

---

