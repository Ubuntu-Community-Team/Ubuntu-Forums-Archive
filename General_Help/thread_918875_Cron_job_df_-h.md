---
title: "Cron job df -h"
date: 2008-09-13
forum: General Help
---

### Post by Mailme on 2008-09-13
Why doesn't this work?

#!/bin/sh

df -h | sendmail mymonitor@localhost


It runs fine from the prompt, but when I put it in 

/etc/cron.daily/df.sh as a script (755) it never sends an email.

---

### Post by hyper_ch on 2008-09-13
Hmmm, I'd rather add it as real cronjob (and for that I rather like to operate with a text file):

```

sudo nano /root/cron.txt

```

add your crons:

```

0 0 * * * /root/df.sh > /dev/null 2>&1 

```
(although I have to say I rather prefer cron to send email and not the script)

Then add the crons to cron:
```

sudo crontab cron.txt

```

Then check if it was added:
```

sudo crontab -u root -l

```

By having cron send the email I know if something is not working with the script ;)

---

### Post by derjames on 2008-09-13
Why don't you use

```
crontab -e
```

This launches nano automatically. Introduce the command there, remember that you should specify the full path to the script:

/path/to/your/script/df.sh

---

### Post by Mailme on 2008-09-13
So what does

> /dev/null 2>&1

actually do?

---

### Post by derjames on 2008-09-13
When you execute 

```
crontab -e
```

you will see yout crontab empty, follow these guidelines to set your scheduled tasks, 

[http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

hope this helps

j

---

### Post by Mailme on 2008-09-13
Have actually tried to run in crontab but it seems as though DF doesn't run in this enviroment. Is it a sh/bash thing?

---

### Post by hyper_ch on 2008-09-13
the > dev ... part will route the output of the script to /dev/null. Otherwise you'd get a copy in your root mail queue.

---

### Post by keithweddell on 2008-09-13
Unless you set the $PATH variable, I think you will need to use the full paths for /bin/df and /usr/sbin/sendmail.

Keith

---

### Post by hyper_ch on 2008-09-13
paths normally don't need to be set...

---

### Post by derjames on 2008-09-14
Ok, this is what I did...

I created the file called 'monitor' in this folder

```
/home/james/scripts/monitor
```

with the following content

```
#! /bin/bash
df -h > /home/james/scripts/output.txt

```

Then for the automation

```
crontab -e
```

nano appears

write the following

```

# m h  dom mon dow   command
*/2 * * * * bash /home/james/scripts/monitor

```

This will send the output of 'df -h' every two minutes to the file output.txt

hope this helps

j

---

