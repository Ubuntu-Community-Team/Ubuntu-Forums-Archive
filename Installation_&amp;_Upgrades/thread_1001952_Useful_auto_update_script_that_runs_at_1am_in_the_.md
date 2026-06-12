---
title: "Useful auto update script that runs at 1am in the mornings"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by nightowl77 on 2008-12-04
Hi 

My ISP only deducts 20% of actual bandwidth used between 1am and 7am and therefore I put together this little script. It's been posted before but I made some modifications to it. Hope it helps

Log in as root (su -) and save this in the root folder under the filename autoupdate

```

# Ubuntu Late Night Updater  
# Author: Werner Avenant 
#
# Instead of adding PATH to crontab - I prefer to have it here
# to make 100% sure things like ldconfig is on the path
# (otherwise things can get screwed up after the package is updated)
PATH=/usr/local/sbin:/usr/sbin:/sbin:"${PATH}"

# Make the logfile a bit more readable and add a timestamp
echo "\n\n\n=========================================" >> /var/log/autoupdate.log
date >> /var/log/autoupdate.log

echo "\n\n" >> /var/log/autoupdate.log

(aptitude -y update && aptitude -y safe-upgrade) 2>&1 >> /var/log/autoupdate.lo

# you shouldn't really do a "full-upgrade" while not watching the machine
# The next line will download all the packages for you, but won't install
# anything. When you're at the machine you can just do aptitude 
# full-upgrade and all the packages would be ready for install
aptitude -y full-upgrade --download-only 2>&1 >> /var/log/autoupdate.log


```

Save the file and make it executable from the command line

```

chmod 700 autoupdate

```

Edit the root user's cron - enter this at the command prompt

```

crontab -e

```

Enter the following and save the file

```

0 1 * * * /root/autoupdate

```

You're all done. Wait a day and then check /var/log/autoupdate.log for problems.

Let me know if you find any bugs (i just installed this myself and won't know until 1am if it will work)

---

