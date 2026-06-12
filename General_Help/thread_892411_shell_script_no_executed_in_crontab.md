---
title: "shell script no executed in crontab"
date: 2008-08-17
forum: General Help
---

### Post by be4truth on 2008-08-17
I have no clue why suddenly my shell scripts are no executed any more in crontab.

-rwxr-xr-x myscript

I enter this with crontab -e
# m h  dom mon dow   command

22 15 * * * /home/user/myscript

but it doesn't execute. Does anybody know where to look for the problem?

---

### Post by bingoUV on 2008-08-17
How are you sure that it did not get executed?

Try adding another simple cron job, and see if it gets executed. Use tips from here to make sure what happened: [http://ubuntuforums.org/showpost.php?p=5197147&postcount=3](http://ubuntuforums.org/showpost.php?p=5197147&postcount=3)

---

