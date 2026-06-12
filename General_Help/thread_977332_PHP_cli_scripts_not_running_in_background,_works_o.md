---
title: "PHP cli scripts not running in background, works on other distro's - what to do?"
date: 2008-11-10
forum: General Help
---

### Post by frankvw on 2008-11-10
For some reason I am unable to run PHP cli scripts in the background (or from a cron job or a log-on script). On other Linux distro's this works fine, but on Ubuntu the process immediately enters a 'stopped' state.

This is a HUGE problem for me; I'm developing this for a client and we're quite a way into the project, and so far Ubuntu has been a great platform for it, but this is a major showstopper. I so totally need to resolve this or find a work-around. I already tried wrapping the PHP script in a regular bash script by adding a #!/usr/bin/php on top and running it as a shell script from the command line, but that didn't solve anything. Google tells me that this has occurred on Debian-based distro's before with previous PHP versions, and that it seems to have something to do with libraries, but the solution so far escapes me.

All suggestions would be appreciated! 


Ubuntu version:
Linux 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

PHP version:
PHP 5.2.4-2ubuntu5.3 with Suhosin-Patch 0.9.6.2 (cli) (built: Jul 23 2008 06:44:49) 
Copyright (c) 1997-2007 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies


How to reproduce:

script.php:
<?php
  while (true)
    sleep (10);
?>

php script.php &
[1] 7970

me@hostname:~/scripts$
[1]+  Stopped                 php script.php


Thanks in advance for reading this... I'm so hoping that there is a way out of this, or I'll have to scrap Ubuntu in favor of another distro, and I really don't want to give up Ubuntu's many good features, not to mention having to go through a platform change this late in a project! :-(

// Frank

---

### Post by frankvw on 2008-11-12
OK. I found a workaround: make the PHP program fork off a child process that then continues to run as a daemon (i.e. in the background).

Instructions here: [http://bipinb.com/?p=68#comment-142]("http://bipinb.com/?p=68#comment-142")

// FvW

---

### Post by alidrus2000 on 2009-03-15
I have been aware for quite some time that php cli can fork off using the pcntl extension. However, I have wanted to run ubuntu server porting an application my company has been running over CentOS 5.2 (the reason being ubuntu server 8.04 has a more recent version of postgresql, apache and php out of the box).

Changing all our daemon scripts to use pcntl_fork() is not really a very good option at this point as the software application we're develop has reached maturity and changing things now would introduce some instability not to mention another round of debugging.

Basically my scripts as they are running in CentOS is something like this:

> 
#!/bin/bash
while true
do
   php -q daemon.php
   sleep 5
done


and this script is run (more or less) as follows from /etc/rc.local:

> 
daemon.sh &


On Ubuntu, this just doesnt work as the php process stops right after it is invoked. So, after a lot of trial and error, I found that the reason the script stops is that it is expecting some input from php://stdin. I managed to solve it temporarily by changing the shell script to this:

> 
#!/bin/bash
while true
do
   php -q daemon.php < /dev/null
   sleep 5
done


After this, the php process no longer stops but I'm still not very happy that I have to do it this way. Is there some option (command line or ini file) that can be set to disable this feature?

---

### Post by Nphyx on 2009-08-24
I had the same problem when trying to run a background process after adding support for command line switches. It worked fine as long as I didn't background it, so I was quite perplexed :P

Thanks a ton for the /dev/null redirect solution. It's not ideal but it works just fine for me.

---

### Post by dancablam on 2009-09-04
I hope this is something ubuntu fixes in the future. Is this a bug that perhaps needs to be posted? Anyways, thanks for the shell script work-around since it seems to have allowed me to get up and running.

Cheers,
Dan

---

### Post by justcarroll on 2010-01-18
You guys saved me from a lot of grief! Thank you.

I have been able to just use:

php -q main.php < /dev/null &

---

### Post by francesco.spegni on 2010-03-22
hi there,

i had the same problem and solved through the trick you mentioned. btw, did anybody find the real reason for this problem?

is it a bug of the php-cli package, a mis-configuration or something else i can fix?

thanks a lot for helping

---

### Post by Benjy1979 on 2011-03-18
What is the -q option on the php, it's not in the manual!

---

### Post by AndrewX192 on 2011-03-19
> **Benjy1979 said:**
> What is the -q option on the php, it's not in the manual!

The -q parameter suppresses any headers that PHP would otherwise output (eg: for a HTTP connection).

---

### Post by jakon on 2012-04-23
(I know this thread is old, still it's the number one google result for the problem)
I'm just adding a link to the bug report that does exist:
[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/907905](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/907905)

---

### Post by oldos2er on 2012-04-23
Old thread closed.

---

