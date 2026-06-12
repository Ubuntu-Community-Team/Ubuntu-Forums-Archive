---
title: "Cronjob setup for new user"
date: 2008-10-30
forum: General Help
---

### Post by Jaxisland on 2008-10-30
I am new to Linux as a whole. Im trying to setup a job to run automatically. I wrote the shell file fine, it works when you double click it and if you add it to the cron.hourly directory. 

Im trying to set it to a more specific time. This is what I have done so far:
cd /
cd etc/
sudo gedit crontab

I added this line at the bottom above the #
38 10	* * * 	root	/home/bob/Desktop/startvm.sh

Saved the file and at 10:38 am, nothing happened.

Please help and be gentle im new,  :)

---

### Post by fsmithred on 2008-10-31
Use the command, 'crontab -e' to edit your crontab. It should look something like this, and there has to be a blank line at the end of the file:

```
# m	h	dom	m	dow	command
38 10 * * * root /home/bob/Desktop/startvm.sh

```


ctrl-x, yes, then enter, to save file and exit.

---

