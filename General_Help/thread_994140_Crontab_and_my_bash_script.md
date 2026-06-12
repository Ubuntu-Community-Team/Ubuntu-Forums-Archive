---
title: "Crontab and my bash script"
date: 2008-11-26
forum: General Help
---

### Post by panda-linux on 2008-11-26
Hello all,

 I been having troubles running bash scripts with crontab, i have looked for answer in several sites, seems to be a classical error: my script works when i do it on my terminal but it does not when crontab tries to use it. Currently my script looks like this:

```
#!/bin/bash
SHELL="/bin/bash"
/usr/bin/top -n 1 | /bin/grep Cpu | /usr/bin/awk -F " " '{print $2"\n"$4}' | /usr/bin/tr -d "%,usni" > /home/panda-linux/cpu.txt

```

my sudo crontab -e looks like:

```
# m h  dom mon dow   command
SHELL=/bin/bash

PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/panda-linux/

HOME=/

*/1 * * * * bash /home/panda-linux/cputest.sh > /home/panda-linux/script.log
```


since i am becoming rather frustrated all files have chmod 777
When i run the script on my terminal (be it as panda-linux or sudo) it works, i do a echo " " > to both files to clear them, and when i isntall the cron job, it wont do it and both log files are empty, the syslog does have the entries of crontab trying to execute the scripts.

As you can see i am working with absolutes paths and i try to tell crontab to work in bash shell every time i can, i tried adding my working directories to the PATH variable, all the suggestions i have found and nothing works. Does anyones sees something i do not? any suggestion please? thanks

---

### Post by unutbu on 2008-11-26
Use the -b switch (batch mode) with top.
```
#!/bin/bash
/usr/bin/top -b -n 1 | /bin/grep Cpu | /usr/bin/awk -F " " '{print $2"\n"$4}' | /usr/bin/tr -d "%,usni" > /home/panda-linux/cpu.txt

```

Also, there is nothing in this script which requires root powers.
Therefore, it is better to run this through your personal cron.

You could type
```

crontab -e

```
and put this in the crontab file:
```

USER=panda-linux
HOME=/home/panda-linux
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/panda-linux/bin
DISPLAY=:0.0
MAILTO=panda-linux

#min hr    day   mon dow
*    * 	   * 	 *   *   /home/panda-linux/cputest.sh > /home/panda-linux/script.log
```

---

### Post by panda-linux on 2008-11-26
Thanks a lot, that did the trick :)

---

