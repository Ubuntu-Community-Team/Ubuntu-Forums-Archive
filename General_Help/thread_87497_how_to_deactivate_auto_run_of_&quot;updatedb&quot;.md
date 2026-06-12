---
title: "how to deactivate auto run of &quot;updatedb&quot;"
date: 2005-11-08
forum: General Help
---

### Post by oskude on 2005-11-08
hi,

while writing this post i found out that this seems to be the place where "updatedb" is started automaticly
```
/etc/cron.daily/slocate
```
if thats the only one, how do i deactivate it ?
(i wouldnt want to just delete the file)

and when im at it, is "updatedb" essential for system stability, or is it only for convenience for the user (locate) ?

cheers
osku[de]

---

### Post by kperkins on 2005-11-08
It's an executable shell script, just change the permissions to 644 (rw-r-r), that should stop it from executing, although I don't know if it'll cause errors not having done this. Alternatively you could just mv the file to another location (say ~/disabled-crons/)
(Although why you'd want disable updatedb, I don't understand)

---

### Post by oskude on 2005-11-08
[QUOTE=kperkins]...just change the permissions to 644...[/QUOTE]
but of course,
thanx for a simple and effective (allround) tip :)
(i'll think ill hide that file too so i dont have to read the file permissions to know whats de/active)
[QUOTE=kperkins]Although why you'd want disable updatedb, I don't understand[/QUOTE]
hmm, i thought i made it clear.
i dont use "locate" and thats the only thing that uses upadedb, as far as i _know_. and thats why my question, is "updatedb" crucial for system stability ? or what else uses "updatedb" than "locate" ? (or does a "crucial-system-tool" use "locate" ?)

what i do know:

man updatedb
"updatedb  is  simply  a  link  to slocate that implies the -u option."

man slocate
" -u     Create slocate database starting at path /."
"Secure  Locate provides a secure way to index and quickly search for files on your system. It uses incremental encoding just like GNU locate to  compress  its  database  to make searching faster, but it will also store file permissions and ownership so that users will not  see  files they do not have access to."

so "updatedb" update/creates an index of my files so i can find files faster than with "find", right ?

i search allways with "find".

cheers
osku[de]

ps. and if i need "locate", i run "updatedb" manually anyway cause i definetly have newer files than the daily(once) updated index...
pss. and i dont want to delete the /etc/cron.daily/slocate cause i want to still have it as reference...

---

### Post by kperkins on 2005-11-08
Well it seems like a lot of work for something that can be done automaticaly, in  the background, but that's just me. :D

---

### Post by vayu on 2005-11-09
updatedb drives me crazy too.  

I moved three files to my home directory, (instead of deleting them I saved them)

/etc/cron.daily/slocate 
/etc/cron.daily/find.notslocate
/etc/updatedb.conf

You can always put them back.  Actually what you want to do is manually run "sudo updatedb" anytime before you want to use slocate.

Here's a link with some info:
[http://ubuntuforums.org/showthread.php?t=25128&highlight=updatedb]("http://ubuntuforums.org/showthread.php?t=25128&highlight=updatedb")

---

### Post by nagilum on 2005-11-09
There's also a little trick, you don't have to remove the files from /etc/cron.daily. By default the run-parts program (which is used to run all the files there) only accepts files which contain letters, numbers and hyphens. Renaming the file to something with a dot in it for example will cron stop from executing this file.

---

