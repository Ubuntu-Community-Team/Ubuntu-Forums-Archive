---
title: "php5-cli cannot backround a script!!!"
date: 2008-09-14
forum: General Help
---

### Post by adamb305 on 2008-09-14
I cannot background any php script that I run from the command line! The same exact script works fine other servers.


#Script below
root@main-desktop:/# cat test.php 
<?php
$x = 1;
while ($x < 2) {sleep(2); $x++; }
?>

#Script executes fine
root@main-desktop:/# php test.php 
root@main-desktop:/# 

#Fails when I try to put in background
root@main-desktop:/# php test.php &
[5] 11757
root@main-desktop:/# jobs
[5]+  Stopped                 php test.php
root@main-desktop:/# 


This works on basically every single other server I have, which is a lot. So something is definitely wrong here. Its nothing to do with the code. 

Can someone please help with this?



Here is system info:

root@main-desktop:/# cat /etc/issue
Ubuntu 8.04.1 \n \l

root@main-desktop:/# php -v
PHP 5.2.4-2ubuntu5.3 with Suhosin-Patch 0.9.6.2 (cli) (built: Jul 23 2008 06:44:49) 
Copyright (c) 1997-2007 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies

root@main-desktop:/# uname -a
Linux main-desktop.judaman.com 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

---

### Post by frankvw on 2008-11-12
> **adamb305 said:**
> I cannot background any php script that I run from the command line! The same exact script works fine other servers.

Same problem here... ([http://ubuntuforums.org/showthread.php?t=977332]("http://ubuntuforums.org/showthread.php?t=977332"))

However I have found a workaround: it is possible to make your PHP program fork off a child process which will then continue to run as a daemon (i.e. in the background). Instructions here:

[http://bipinb.com/?p=68#comment-142]("http://bipinb.com/?p=68#comment-142")

Hope this helps...

// FvW

---

