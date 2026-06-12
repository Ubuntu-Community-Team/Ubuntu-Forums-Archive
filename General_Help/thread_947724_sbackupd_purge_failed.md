---
title: "sbackupd purge failed"
date: 2008-10-14
forum: General Help
---

### Post by SimonProven on 2008-10-14
Hello, my first question on here.  Can't find a reference to this issue on google.

I got an email this morning from cron, which contained the following backtrace from sbackupd:

Subject: Cron <root@librarian> if [ -x /usr/sbin/sbackupd ]; then /usr/sbin/sbackupd; fi;

Traceback (most recent call last):
  File "/usr/sbin/sbackupd", line 428, in <module>
    upgrader.upgrade_target( target, purge )
  File "/usr/share/sbackup/upgrade_backups.py", line 63, in upgrade_target
    self.purge( target, listing, purge )
  File "/usr/share/sbackup/upgrade_backups.py", line 253, in purge
    self.delete( target+"/"+adir )
  File "/usr/share/sbackup/upgrade_backups.py", line 262, in delete
    shutil.rmtree( uri, False )
  File "/usr/lib/python2.5/shutil.py", line 174, in rmtree
    onerror(os.remove, fullname, sys.exc_info())
  File "/usr/lib/python2.5/shutil.py", line 172, in rmtree
    os.remove(fullname)
OSError: [Errno 2] No such file or directory: '/mnt/mybook/librarian-backup/2008-09-14_04.00.03.811200.librarian.ful/files.tgz'


I don't understand why rmtree on the directory '/mnt/mybook/librarian-backup/2008-09-14_04.00.03.811200.librarian.ful/' would get an error with a file inside that directory not existing (I checked, it doesn't exist).

This has caused the daily backup last night to fail due to the script bombing out on the error so I'd like to fix it, if it's going to be repeated.  Might it be relevant that the backup is on a network drive, mounted over samba?

[update] As I wasn't able to post this at the time I wrote it due to admin issues with the forums, I saw what happened last night - it managed to delete the .ful directory but has left all the .inc directories that depended on it lying around.  This might be a separate issue.

I'm using 8.04.

Any help appreciated.

Simon

---

### Post by SimonProven on 2008-11-13
Happened again:

Traceback (most recent call last):
  File "/usr/sbin/sbackupd", line 428, in <module>
    upgrader.upgrade_target( target, purge )
  File "/usr/share/sbackup/upgrade_backups.py", line 63, in upgrade_target
    self.purge( target, listing, purge )
  File "/usr/share/sbackup/upgrade_backups.py", line 253, in purge
    self.delete( target+"/"+adir )
  File "/usr/share/sbackup/upgrade_backups.py", line 262, in delete
    shutil.rmtree( uri, False )
  File "/usr/lib/python2.5/shutil.py", line 174, in rmtree
    onerror(os.remove, fullname, sys.exc_info())
  File "/usr/lib/python2.5/shutil.py", line 172, in rmtree
    os.remove(fullname)
OSError: [Errno 2] No such file or directory: '/mnt/mybook/librarian-backup/2008-10-14_04.00.04.830467.librarian.ful/files.tgz'


Seems like it's whenever it tries to delete a .ful.  Any thoughts on how to debug this?  I could add some logging to the python - e.g. printing out the purge list.  I guess I'll need to download the sources and install a version with my own changes.

Unfortunately waiting a month to find out what the problem is could make this a slow debug cycle. :mad:

---

