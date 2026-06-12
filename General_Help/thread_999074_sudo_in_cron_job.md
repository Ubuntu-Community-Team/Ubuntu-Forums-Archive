---
title: "sudo in cron job"
date: 2008-12-01
forum: General Help
---

### Post by happypig on 2008-12-01
I have a server and I want to run cron jobs on it that require a password putting in (starting/stopping an azureus process).
How do I get the cron job to accept the password ?

---

### Post by ju2wheels on 2008-12-01
I assume that by password you mean you need to enter your superuser password in order to disable the service.

You can omit the password all together by writing a script to start/stop the azureus process and set the scripts owner/group to root and also enable the execute and sticky bits on the script. Then add the script to cron.

For example if I create a start_azureus.sh script:
```

#!/bin/bash

#Im not sure if this command is correct, just replace it with the path to the correct executable
/etc/init.d/azureus start

```

Then do the following to the script file:
```

sudo chown root:root start_azureus.sh
sudo chmod a+sx start_azureus.sh
sudo chmod a-wr start_azureus.sh

```

Then add it to root's cron using crontab (be sure the crontab file has an empty line at the end or it will not execute any of the cron jobs).

---

### Post by bodhi.zazen on 2008-12-01
It seems counter intuitive , a cron job that requires a password, so be it.

Look at expect (you can also pass a password with sudo, see man sudo).

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

	[http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

---

### Post by hyper_ch on 2008-12-01
why not add it to root cron instead?

---

