---
title: "cron job question"
date: 2008-10-28
forum: General Help
---

### Post by fouadk on 2008-10-28
hi everyone....

i am trying to make a command run on a daily basis at a sprcific time....

what i did is that inside /etc/cron.daily i created an empty document and wrote to it the following:
0 18 * * * sudo ntpdate 192.168.0.3

and then saved this document as update_ntp
and then gave it mode 755
and then did sudo crontab update_ntp

my question is the following: how can i make sure that the command is being executed successfully especially that the command i want to run requires "sudo" priviliges ????

please help

thanks in advance.

---

### Post by forger on 2008-10-28
add your cron in:
a) the root crontab:
```
sudo crontab -e
```

Press ctrl+x to exit and press "y" to save changes

OR
b) the file /etc/crontab:
```
gksu gedit /etc/crontab
```

and restart cron:
```
sudo invoke-rc.d cron restart
```


Note: these two are **two different methods** that use different files!
To remove the root crontab (**NOT** /etc/crontab):
```
sudo crontab -r
```

---

