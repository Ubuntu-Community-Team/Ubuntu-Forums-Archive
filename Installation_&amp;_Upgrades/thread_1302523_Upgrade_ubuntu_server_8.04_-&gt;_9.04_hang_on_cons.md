---
title: "Upgrade ubuntu server 8.04 -&gt; 9.04 hang on console setup"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by mansonthomas on 2009-10-27
Hi,


  I'm upgrading an ubuntu  8.04 server to 9.04,

and the upgrade process hang on this : 

[PHP]Setting up nmap (4.76-0ubuntu4) ...

Setting up console-terminus (4.26-2.1) ...
Setting up console-setup (1.28ubuntu8) ...
 * Setting up console font and keymap...[/PHP]


processes : 

[PHP]14526 14528 14526 14526 ?           -1 S     1000   0:00  \_ sshd: thomas@pts/0
14528 14529 14529 14529 pts/0    22893 Ss    1000   0:00      \_ -bash LANG=en_US.UTF-8 USER=thomas LOGNAME=thomas HOME=/home/thomas PATH=/usr/local/sbin:/us
14529 22893 22893 14529 pts/0    22893 S+       0   0:19          \_ /usr/bin/python /tmp/tmpuorI1M/jaunty --mode=server --frontend=DistUpgradeViewText
22893 22970 22893 14529 pts/0    22893 S+       0   0:01              \_ /usr/bin/python /tmp/tmpuorI1M/jaunty --mode=server --frontend=DistUpgradeViewText
22970 16583 16583 16583 pts/1    16583 Ss+      0   0:00                  \_ /usr/bin/dpkg --force-overwrite --status-fd 54 --configure libc6-i686 libgmp3c2
16583  1292 16583 16583 pts/1    16583 S+       0   0:00                      \_ /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/console-setu
 1292  1433 16583 16583 pts/1    16583 S+       0   0:00                          \_ /bin/sh /var/lib/dpkg/info/console-setup.postinst configure 1.25ubuntu4
 1433  1453 16583 16583 pts/1    16583 S+       0   0:00                              \_ /bin/sh /tmp/tmpuorI1M/imported/invoke-rc.d console-setup start
 1453  1469 16583 16583 pts/1    16583 S+       0   0:00                                  \_ /bin/sh /etc/init.d/console-setup start
 1469  1477 16583 16583 pts/1    16583 S+       0   0:00                                      \_ /bin/sh /bin/setupcon --force --save
 1477  1478 16583 16583 pts/1    16583 S+       0   0:00                                          \_ /bin/echo -n -e \033%G
[/PHP]

and in /var/log/dpkg.log

I can see this : 

[PHP]2009-10-27 11:51:24 status unpacked console-terminus 4.26-2.1
2009-10-27 11:51:24 status half-configured console-terminus 4.26-2.1
2009-10-27 11:51:24 status installed console-terminus 4.26-2.1
2009-10-27 11:51:24 configure console-setup 1.28ubuntu8 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status unpacked console-setup 1.28ubuntu8
2009-10-27 11:51:24 status half-configured console-setup 1.28ubuntu8
[/PHP]

any idea of what to do in order to complete the upgrade setup ? 

Thomas.

---

### Post by mansonthomas on 2009-10-27
anybody ?

---

### Post by mansonthomas on 2009-10-27
I could kill the echo command that seems to be at the root of the hang?

---

### Post by mansonthomas on 2009-10-27
Well I tried to kill the echo command, and the parent process, it resumes the install then retry to reconfigure the console and hang exactly at the same point...

I'll open a bug ticket if no one has an idea...

---

### Post by mansonthomas on 2009-10-27
cheese...

The [https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect) ends with a timeout.

And ubuntu-bug is not installed on my system... I can't install it because of the dist-upgrade process.

---

