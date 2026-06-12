---
title: "[SOLVED] Task manager equivalent in Ubuntu"
date: 2008-11-13
forum: General Help
---

### Post by burmanabhay88 on 2008-11-13
I'm a newbie to Ubuntu/Linux. I usually keep my system on low PF usage(in Windows) by terminating programs that I'm not using currently(using TaskManager), or by disabling them from startup(msconfig).
I need to do something equivalent in Linux. I know the 'ps' command, but I don't have any idea which process is worth 'kill'ing.
Can any one help me out.

---

### Post by cdtech on 2008-11-13
Try:
System > Administration > System Monitor

---

### Post by Steve1961 on 2008-11-13
The equivalent of task manager is probably system monitor, which you'll find in the system/administration menu.  But be careful what you kill, you only tend to kill misbehaving programmes.  If you want to stop programmes starting up when you log in have a look at the system/preferences/sessions menu.  To disable unneeded services look in system/administration/services.

But...if you don't know what you're doing I'd suggest leaving well alone until you get more familiar with ubuntu.  Forget the windows mind-set because Ubuntu is a completely different bag of tricks :)

---

### Post by burmanabhay88 on 2008-11-13
Thanks.. to both of you. Just what I wanted. :)

---

### Post by TeXtonyx on 2008-11-13
[http://www.linux.com/feature/148189](http://www.linux.com/feature/148189)

A simple example

"ps-watcher can stop machines from crashing due to memory 
exhaustion, or make sure that a buggy program isn't leaving too 
many copies of itself running. One basic use for ps-watcher is 
ensuring that a certain program is running. Say that you want to 
make sure your CentOS Linux server always has one copy of the 
Network Time Protocol daemon ntpd running to maintain accurate 
time. Keeping ntpd running can be a challenge; for example, it 
exits on startup if the system time is too far from the reference
time. One way to keep ntpd running is to use ps-watcher to ensure
that at least one ntpd process is running at all times. Create a 
ps-watcher.cfg file with these contents:

[ntpd] occurs = none action = /etc/init.d/ntpd restart "

-----------------------------------

[http://technet.microsoft.com/en-us/sysinternals/bb795533.aspx](http://technet.microsoft.com/en-us/sysinternals/bb795533.aspx)
SysInternal Process Utilities (Process Explorer)

There are some cool tools there. You might not have known about
this, and with Powershell, Windows gets closer to Linux capability, 
but Linux has [http://www.opennms.org/index.php/Main_Page](http://www.opennms.org/index.php/Main_Page)
There are also a lot of scripts written for process actions.

---

### Post by burmanabhay88 on 2008-11-13
> **TeXtonyx said:**
> [http://www.linux.com/feature/148189](http://www.linux.com/feature/148189)

A simple example

"ps-watcher can stop machines from crashing due to memory 
exhaustion, or make sure that a buggy program isn't leaving too 
many copies of itself running. One basic use for ps-watcher is 
ensuring that a certain program is running. Say that you want to 
make sure your CentOS Linux server always has one copy of the 
Network Time Protocol daemon ntpd running to maintain accurate 
time. Keeping ntpd running can be a challenge; for example, it 
exits on startup if the system time is too far from the reference
time. One way to keep ntpd running is to use ps-watcher to ensure
that at least one ntpd process is running at all times. Create a 
ps-watcher.cfg file with these contents:

[ntpd] occurs = none action = /etc/init.d/ntpd restart "

-----------------------------------

[http://technet.microsoft.com/en-us/sysinternals/bb795533.aspx](http://technet.microsoft.com/en-us/sysinternals/bb795533.aspx)
SysInternal Process Utilities (Process Explorer)

There are some cool tools there. You might not have known about
this, and with Powershell, Windows gets closer to Linux capability, 
but Linux has [http://www.opennms.org/index.php/Main_Page](http://www.opennms.org/index.php/Main_Page)
There are also a lot of scripts written for process actions.
wohhh.... didn't get half the things you said. but thank's anyways...

---

