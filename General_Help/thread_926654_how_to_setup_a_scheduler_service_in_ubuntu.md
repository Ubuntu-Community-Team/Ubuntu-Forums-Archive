---
title: "how to setup a scheduler service in ubuntu"
date: 2008-09-22
forum: General Help
---

### Post by jittopjose on 2008-09-22
hello friends,
i am creating an intranet application in cakephp for my company. its hosted in ubuntu lamp server. i want to send a reminder mail to the employees at 4pm each day. how to setup this in ubuntu server. currently this system is working in a windows system, there we have setup a windows service. now we are migrating to cakephp and lamp. am using ubuntu 8.04. plz help me if anybody have any idea about it.
thanks
jittos....

---

### Post by stickmangumby on 2008-09-22
Do you want to run a php script at a particular time each day, and have php send the email?

If so, you want to set up a cron job that does this. For example, you might run:

```

crontab -e 

```

And create a new entry such as:

```

0 16 * * * /path/to/script/myphpscript.php

```

---

