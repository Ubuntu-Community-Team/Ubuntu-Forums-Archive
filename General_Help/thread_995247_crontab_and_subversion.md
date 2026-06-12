---
title: "crontab and subversion"
date: 2008-11-27
forum: General Help
---

### Post by DEpurpnijM on 2008-11-27
Hi there!

I'm having a problem using subversion in the crontab. 

I've created a crontab by doing a "crontab -e"

For example the following command succeeds:

15 * * * * mkdir /home/user/test

but as soon as I'm trying to do a 

15 * * * * svn update /home/user/test

(test of course is under version control) crontab simply doesn't do anything. I've tried to log it by using a "> /home/user/logfile" but it stays emtpy. Then I've tried to use a script an so created svnscript which was like:

#!/bin/bash
cd /home/user/test
svn update

(also tried "/usr/bin/svn update)
The script works excecuted through a console - but doesn't do anything if I crontab:

15 * * * * /path/to/script/svnscript

(and of course the script is mod 0755)

So I'm running out of ideas. Can anybody help me out?

Thanx

---

### Post by kevstar31 on 2008-11-27
Try
```
15 * * * * **"**svn update /home/user/test**"**
```
Post the script you tried to use.

---

### Post by DEpurpnijM on 2008-11-28
> **kevstar31 said:**
> Try
```
15 * * * * **"**svn update /home/user/test**"**
```
Post the script you tried to use.

Hi kevstar31, 

that didn't work either :(

And my script, named "svn-script", simply consists of three lines:

***************
#!/bin/bash
cd /full/path/to/svn-folder
svn update
***************

I also tried "svn update /full/path/to/svn-folder". As said - running this script manually works just like a charm. And every substituion of the command "svn update" by anything else also works fine - even in crontab. So I think it must have something to do with a specific subversion problem. (If I just change the command in my script - leaving the crontab as it is - for example:

#!/bin/bash
cd /full/path/to/svn-folder
mkdir test

everything works as intended.:confused:

Thanks

---

### Post by DEpurpnijM on 2008-11-28
Well - I solved the problem.

Accidently found out that there's been a problem with the locales in crontab. So adding "LANG=en_US.UTF-8" to your crontab makes even svn run as a cron job...

---

