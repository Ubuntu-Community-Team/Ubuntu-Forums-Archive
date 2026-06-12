---
title: "MailScanner not working after 9.10 upgrade"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by dalto on 2009-11-03
I upgraded from 9.04 to 9.10 and I only have one issue.  However, I am having trouble finding a solution.

Ever since upgrade my MailScanner is not working correctly.  It just restarts every couple of seconds.

There are no errors in the log so I ran MailScanner in debug mode.  However, when I run it in debug mode it works fine.  I get no errors and it does just what it should.  However, when I re-enable it I just get this over few seconds in my logs and no mail is delivered.

```
Nov  3 20:44:22 gandalf MailScanner[10676]: MailScanner E-Mail Virus Scanner version 4.74.16 starting...
Nov  3 20:44:22 gandalf MailScanner[10676]: Read 848 hostnames from the phishing whitelist
Nov  3 20:44:22 gandalf MailScanner[10676]: Read 4278 hostnames from the phishing blacklist
Nov  3 20:44:23 gandalf MailScanner[10676]: Using SpamAssassin results cache
Nov  3 20:44:23 gandalf MailScanner[10676]: Connected to SpamAssassin cache database
Nov  3 20:44:23 gandalf MailScanner[10676]: Enabling SpamAssassin auto-whitelist functionality...
Nov  3 20:44:24 gandalf MailScanner[10676]: I have found clamd scanners installed, and will use them all by default.
Nov  3 20:44:24 gandalf MailScanner[10676]: Using locktype = flock
Nov  3 20:44:24 gandalf MailScanner[10676]: New Batch: Scanning 20 messages, 162600 bytes
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message 6C9DD3A023.27991
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message 3737C3A006.E18D3
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message B8D713A015.0F684
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message 59A4A3A007.0C4AD
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message EC7C23A134.17AE5
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message A060E3A032.14CA5
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message 5F3D93A029.2733C
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message 45EE53A00A.399D2
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message 3366A3A027.73BA9
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message 8A3D53A003.9C145
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message A98C93A025.30C01
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message 518723A02F.9A8E9
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message 0A8833A02A.30ED9
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message AEFB43A014.96AB1
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message CA0D53A004.8EE14
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message 149E13A00B.892E5
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message DF6E63A135.AD49D
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message 255813A028.044E8
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message 63AF13A009.F3A58
Nov  3 20:44:24 gandalf MailScanner[10676]: SpamAssassin cache hit for message 774033A008.56F6E
Nov  3 20:44:24 gandalf MailScanner[10676]: Spam Checks: Found 18 spam messages

```

Any help is appreciated.

---

### Post by tps on 2009-11-03
Same here. It looks like it never gets to the point that it's moving the mail to the outbound queue. I may change this to not deliver in the background to see if that helps...

Tim

---

### Post by tps on 2009-11-04
I'm now getting:

Insecure dependency in chown while running with -T switch at /usr/share/MailScanner//MailScanner/Message.pm line 2407.

---

### Post by dalto on 2009-11-04
> **tps said:**
> I'm now getting:

Insecure dependency in chown while running with -T switch at /usr/share/MailScanner//MailScanner/Message.pm line 2407.

You can't run it as root.  Run it as the user it normally runs as using sudo -u <username>.

---

### Post by tps on 2009-11-04
> **dalto said:**
> You can't run it as root.  Run it as the user it normally runs as using sudo -u <username>.

setting debug, and running '/etc/init.d/mailscanner start' should do the right thing, no?

---

### Post by dalto on 2009-11-04
> **tps said:**
> setting debug, and running '/etc/init.d/mailscanner start' should do the right thing, no?

I believe when you set debug you need to run it interactively.

I did it by using "sudo -u postfix MailScanner"

---

### Post by tps on 2009-11-04
> **dalto said:**
> I believe when you set debug you need to run it interactively.

I did it by using "sudo -u postfix MailScanner"

'cpan install IO' did the trick for me. It's now working again...

Tim

---

### Post by dalto on 2009-11-04
Still no luck for me.

If anyone has any ideas I would appreciate it.

---

### Post by tps on 2009-11-04
> **tps said:**
> 'cpan install IO' did the trick for me. It's now working again...


Well OK then... 12 hours later and it stopped working. From the logs, MailScanner processed the queue for about 90-odd minutes, and then went back to the former state. Grrr...

---

### Post by tps on 2009-11-10
Well, it looks like only two of us. I'm going to try to purge MailScanner tonight, and then reinstall. Not the way I'm used to working with Debian-based systems...

All my production systems are pure Debian...

Tim

---

### Post by tps on 2009-11-10
Success. The problem is with the init script. In /etc/init.d/mailscanner, I had to add -c ${user} to the start-stop-daemon line, since it had no idea what user to run as. It was strange that when called from the command line as (for me) sudo -u Debian-exim MailScanner, it would work.

So, the modified line in the init script should look something like:

        start-stop-daemon --start --quiet --startas $STARTAS --name $NAME --test > /dev/null \
                || return 1
        start-stop-daemon --start --quiet --nicelevel $run_nice -c ${user} --exec $DAEMON --name $NAME -- $DAEMON_ARGS \
                || return 2


Add the -c ${user}, restart mailscanner, and it'll be back working. At least this is working for me.

Tim

---

### Post by Shaker242 on 2010-03-12
Thank you for actually posting your fix!  I made the slight modification to the init script as you outlined and fired up mailscanner.

MailScanner --lint still has this error: 
Insecure dependency in chown while running with -T switch at /usr/share/MailScanner//MailScanner/Message.pm line 2407.

However, MailScanner is running is deliering mail again... so it'll due for now.

Shaker

---

### Post by bsgcic on 2010-04-29
Hey Tim (tps),
You're the Man!!!  Thank you Thank you Thank you!!!
 
Any thoughts on how to get the ubuntu mailscanner package manager to add that change to the default for future upgrades, etc?

---

### Post by NIT006.5 on 2011-02-08
Apparently this is still not fixed in 10.04. Thanks for the work-around - seems to be doing the trick.

---

### Post by ivomans on 2011-03-02
Same problem after upgrade from 8.04.
Tim's solution seems to solve this.

Regards, Ivo.

---

### Post by halfgaar on 2011-05-03
Same problem here, on Ubuntu 10.04. [Reported bug](https://bugs.launchpad.net/ubuntu/+source/mailscanner/+bug/776753). Please post your relevant information in that bug report.

BTW; why would the initscript need the user, if the Mailscanner config already states the user it should run as?

---

