---
title: "bash script - tilde expansion"
date: 2008-11-24
forum: General Help
---

### Post by mkramer on 2008-11-24
Hi guys.  I've got a tiny bash script to do rsyncing.  I want to use tilde expansion in my script but it's not expanding.  On the command line ~ expands to $HOME.  In the script, echo $HOME and echo ~ will echo the same, correct directory.  But when I read a line using read, I do not get shell expansion of the path name.  And when I redirect to ~/Library/Logs, I also do not get shell expansion.  

The backuplist file contains paths to directories and files to backup.  Many of them are specified using a tilde, eg ~/Documents/. 

 ```
 #!/bin/bash

TARGET=masonkramer@masonmb:	
BACKUPLIST=~/txts/backuplist.new			#a plain text list of file paths relative to 


echo "
#################################################
INITIATING ONE WAY BACKUP AT `date`
" >> ~/Library/Logs/rsync.log

exec<$BACKUPLIST
while read f
echo ~
echo $HOME
do
if [ ! -e $f ]
	then
	echo could not find $f  # this always happens because ~ expansion is not occuring
fi
if [ -e $f ]
	then
	echo Backing up ${f} to ${TARGET}$f on `date`... >> ~/Library/Logs/rsync.log
    rsync -Cavzu -e ssh --delete ${f} ${TARGET}${f}  >> ~/Library/Logs/rsync.log
fi
done

echo "##############
END BACKUP at `date`
" >> ~/Library/Logs/rsync.log 
```

I read in the man page that tilde expansion is applied during variable assignment.  So I tried assigning f to another variable, as in nf=$f but that also did not produce the desired expansion.  `echo $f` also does not cause expansion.   Help appreciated.   Thanks in advance.

---

### Post by The Cog on 2008-11-24
Maybe it depends on how you are running the script. The environment variables like your home directory get set as part of the login process, but I'm not sure if they get set if (for instance) you schedule to run the script from cron or something like that.

---

### Post by mkramer on 2008-11-24
As I was saying, the $HOME variable contains the correct path.  Bash is simply failing to expand ~'s

---

### Post by mike2357 on 2008-11-24
Is there a space on the first line before the #!/bin/bash ?  If so, please remove it and re-run.  Scripts are very particular about the first line.

---

### Post by mkramer on 2008-11-25
hi guys.  Apparently it's not my script, but the way Bash works. I read in the file to Awk, replaced leading ~'s with $HOME, and piped it using the | while read line construct.  It works.

---

### Post by nicco on 2009-09-17
This thread is old as the hills, but since it's still showing up in Google searches I thought I'd provide the 'correct' answer to anyone who find this (like I just did.)

If you have an environment variable that contains the literal character '~', or any other kind of expandable bash-magic, you can forcefully expand it using the 'exec' command. Example:

```

$ a='~'
$ echo $a
~
$ eval echo $a
/home/user
$ eval a=$a
$ echo $a
/home/user

```
Hope this helps ;-)

---

### Post by victor.zamanian on 2011-05-18
> **nicco said:**
> If you have an environment variable that contains the literal character '~', or any other kind of expandable bash-magic, you can forcefully expand it using the 'exec' command.

You mean the [FONT="Courier New"]eval[/FONT] command. :)

---

