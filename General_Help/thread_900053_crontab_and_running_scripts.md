---
title: "crontab and running scripts"
date: 2008-08-24
forum: General Help
---

### Post by Krupski on 2008-08-24
This post is not a question, but rather an FYI.

I've looked all around for help on "things not being run by crontab" and I *finally* got it all figured out!

So, here's what I learned... so that it might help others:

The key to making scripts *ACTUALLY RUN* via crontab is to do the following:

(1) Make sure the script is executable (i.e. chmod 0755).
(2) The *VERY FIRST LINE* of any script to be run by crontab (i.e. scripts in '/etc/cron.daily' or '/etc/cron.monthly', etc... must be THIS:

```

#!/bin/sh

```

or this:

```

#!/bin/bash

```

This is the key to making a script run as opposed to failing. The very first line MUST be present, as described above.

Lastly, here's a copy of my 'crontab' file which is basically the stock Ubuntu file, but with help included inside as comments as well as an additional line which triggers scripts at bootup.

Note: If you use this crontab file, you must ALSO create a directory named '/etc/cron.boot' and place anything you want run at bootup in there.

Here's the crontab file:

```

###############################################################
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the 'crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.
#
# ==> NOTE!!! Scripts to be placed in /etc/cron.daily, weekly, etc
#             must have '#!/bin/sh' or '#!/bin/bash' as their FIRST
#             line or else they will not work!
#
#
# TIME FIELDS:
#       * * * * * * command to execute && next command && ...
#       - - - - - -
#       | | | | | |
#       | | | | | +--- run command as 'username'
#       | | | | +----- day of week (0-7) (Sunday=0 or 7)
#       | | | +------- month (1-12)
#       | | +--------- day of month (1-31)
#       | +----------- hour (0-23)
#       +------------- minute (0-59)
#
# SPECIAL STRINGS:
#
#       special string  meaning
#       --------------  -------
#
#       @reboot         Run once, at startup.
#       @yearly         Run once a year  [0 0 1 1 *]
#       @annually       (same as @yearly)
#       @monthly        Run once a month [0 0 1 * *]
#       @weekly         Run once a week  [0 0 * * 0]
#       @daily          Run once a day   [0 0 * * *]
#       @midnight       (same as @daily)
#       @hourly         Run once an hour [0 * * * *]
#
###############################################################

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# min   hour    day     month   dow     user    command
# ---   ----    ---     -----   ---     ----    -------

# at bootup
  @reboot                               root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.boot )

# hourly at xx15
  15     *       *       *       *      root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.hourly )

# daily at 0425
  25    04       *       *       *      root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )

# weekly at 0435
  35    04       *       *      00      root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )

# monthly at 0445
  45    04      01       *       *      root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

```


To *TEST* a new script, just run the same command that crontab would run, like this:

```

sudo run-parts /etc/cron.daily

```

Of course, choose the particular directory you wish to test rather than 'cron.daily' as shown in the example.

If it is right, it will run. If it's got an error (like the missing '#!/bin/bash' line), you will see "Exec format error".


I hope this helps someone and/or saves them some grief... :)

-- Roger

---

