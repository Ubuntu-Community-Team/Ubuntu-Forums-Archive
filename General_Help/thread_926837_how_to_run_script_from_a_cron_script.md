---
title: "how to run script from a cron script"
date: 2008-09-22
forum: General Help
---

### Post by starkes on 2008-09-22
hi.

I'm trying to write a script that runs every minute, using cron, to process render jobs.
I have a script that is called with cron and can take a shell script with a bunch of commands in it and move it to another filename, to get ready for execution. but when i try to run the script from the cron script, nothing happens.

```

nodenumber="$1"
if [ -f "/db/PSIrender/jobs/$nodenumber.jobs" ]
then
	if [ ! -f "/db/PSIrender/jobs/$nodenumber.working" ]
	then
		mv "/db/PSIrender/jobs/$nodenumber.jobs" "/db/PSIrender/jobs/$nodenumber.working"
		echo "rm -rf $nodenumber.working" >> "/db/PSIrender/jobs/$nodenumber.working"
                sh "/db/PSIrender/jobs/$nodenumber.working &"
fi

```

basically, in the above code, i just cant figure out why i cant execute the line: ```
sh "/db/PSIrender/jobs/$nodenumber.working &"
```

the cron script runs as root so im not sure but i dont think its a permissions problem all the files are chmod 777'd as well, and if i were to go to the right folder and type that command in manually, it runs. just not when the cron script does the same. How could this script be able to move the file from one name to another, but not have the rights to run it?


any ideas?

---

### Post by fwre01 on 2008-09-22
two possible things that may be causing it...

make sure you use absolute paths in your script on EVERYTHING! and also check on the top line of your crontab you have this

MAILTO=""

i have found that without it cron does not run.

Hope that fixes it

---

### Post by starkes on 2008-09-22
yeah. ive got all absolute paths now. (had one relative before but ive since changed that). seems to be no difference. and also, i do have the MAILTO and the cron script is running, i can see it changing 0.jobs 1.jobs etc files into 0.working, 1.working. it just doesnt run the line right after that.

---

### Post by fwre01 on 2008-09-22
can you repost your script since the changes have been made, and post the contents of your crontab file?

---

### Post by koenn on 2008-09-22
```
sh "/db/PSIrender/jobs/$nodenumber.working &"
```

I don't know if you really need to call that line with 'sh' in stead of just calling the script, but if you do need 'sh',
then you might want to give the absolute path : /bin/sh

like fwre01 said : absolute paths on EVERYTHING

---

