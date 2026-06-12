---
title: "Installation problems -&gt; way to debug?"
date: 2012-04-02
forum: Hardware
---

### Post by patman0623 on 2012-04-02
I had an absolutely hideous time getting Ubuntu installed on my laptop. First off, it didn't recognize the video driver, so I had to hack the installation to use *nomodeset*. Then, after installation it got stuck on [checking battery state...]("http://ubuntuforums.org/tags.php?tag=checking+battery+state"). In all, I actually had to remove the hard drive physically from my laptop and plug it into another computer with hardware which I knew would work, and install proprietary video drivers.

It was a harrowing enough experience that I don't want anyone to have to go through it again (I won't even mention it badly goofing up my hard drive partition). I would like to submit debug logs to Ubuntu, Linux, or whoever would best be able to use them. Does my computer keep debug logs that far back and if so, how could I go about reporting it?

---

### Post by Rodney9 on 2012-04-03
[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)

View log files in Ubuntu Linux
by VIVEK GITE 

Q. Can you explain me log files in Ubuntu Linux and how do I view logs?

A. All logs are stored in /var/log directory under Ubuntu (and other Linux distro).

Linux Log files and usage

=> /var/log/messages : General log messages

=> /var/log/boot : System boot log

=> /var/log/debug : Debugging log messages

=> /var/log/auth.log : User login and authentication logs

=> /var/log/daemon.log : Running services such as squid, ntpd and others log message to this file

=> /var/log/dmesg : Linux kernel ring buffer log

=> /var/log/dpkg.log : All binary package log includes package installation and other information

=> /var/log/faillog : User failed login log file

=> /var/log/kern.log : Kernel log file

=> /var/log/lpr.log : Printer log file

=> /var/log/mail.* : All mail server message log files

=> /var/log/mysql.* : MySQL server log file

=> /var/log/user.log : All userlevel logs

=> /var/log/xorg.0.log : X.org log file

=> /var/log/apache2/* : Apache web server log files directory

=> /var/log/lighttpd/* : Lighttpd web server log files directory

=> /var/log/fsck/* : fsck command log

=> /var/log/apport.log : Application crash report / log file

To view log files at shell prompt

Use tail, more, less and grep command.
tail -f /var/log/apport.log
more /var/log/xorg.0.log
cat /var/log/mysql.err
less /var/log/messages
grep -i fail /var/log/boot

---

