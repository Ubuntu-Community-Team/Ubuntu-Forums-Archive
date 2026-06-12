---
title: "How can I run php(cgi) with root privilege in Crontab?"
date: 2008-07-29
forum: General Help
---

### Post by realkoyu on 2008-07-29
Hi all,

I want to run a php script every minute. 
Because there are some system commands (such as system("/sbin/iptables -D INPUT -s ipaddress -j DROP");) which needs root privilege, I will have to run it in root account.
And this php runs happily when i type "sudo php somephp.php", however it doesn't work in crontab...

There are the lines in the crontab job list.
# m h  dom mon dow   command
* * * * * root /usr/bin/php /somefolder/somephp.php

Can anyone give me some idea to solve this problem?
Any help would be appreciated.

Thanks

Victor

---

### Post by 3rods on 2008-07-29
Curious, are you editing root's cronfile? 

```
sudo crontab -e -u root

```

Or something to that effect?

I don't think you need to specify "root" before the command if you're editing root's crontab. I could be wrong though.

---

### Post by realkoyu on 2008-07-29
Hi, 3rods,

Thanks for your reply.
Yes, I did edit the crontab job list in root account, and I can see the job with "sudo crontab -l"

Regards

---

### Post by 3rods on 2008-07-29
Just a thought, but maybe you could try writing some text into a file to make sure your cron is working. Once, you're sure that's fine, let the cron run and then check your log files.

Is the script being executed in the same directory from cron as you did from the command line? If not, maybe suExec it messing with it. Can you modify the script to do a fopen(), write and just write some text to a file? See if you can get that working with cron. Or just try it with an easier script.

---

### Post by realkoyu on 2008-07-29
Hi, 3rods,

I worked it out. It was the "root" which blocked my command.

Thanks for your kind help.

---

### Post by 3rods on 2008-07-30
Cool, glad to help.



Oh, yeah, don't forget to mark the thread SOLVED.

---

