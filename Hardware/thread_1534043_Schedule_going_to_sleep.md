---
title: "Schedule going to sleep"
date: 2010-07-18
forum: Hardware
---

### Post by Gantlett on 2010-07-18
Hi Everyone,

I'm running Ubuntu Desktop 10.04 32-bit on an old Dell Inspiron (Intel Dothan 1.6GHz and 2GB of RAM). 

This machine is going to be my home server, running DNS server, SugarCRM CE, file services for Windows and Mac machines and maybe a virtual machine (quite a lot for such an old geezer, I know, but it actually works well!).

My questions:
1. Since it will not be serving anyone when everyone's asleep, I'd like to be able to automatically send it to sleep according to a daily schedule. Is this possible with Ubuntu?
2. A different approach would be using the standard "sleep after..." setting, but having the machine wake up on demand. Is this possible in any way?

Thanks in advance!

---

### Post by IcarusR on 2010-07-19
There are several methods of suspending/hibernating from the terminal in this thread...

[http://ubuntuforums.org/showthread.php?t=813387]("http://ubuntuforums.org/showthread.php?t=813387")

Test which one works for you then setup a root cron job to run the command at specified time. 

For info on cron in teminal type....

```
man cron
```

& 

```
man crontab
```

You will need to ensure that no processes are running that write to hdd or ram, otherwise your system will wakeup.

---

### Post by Gantlett on 2010-07-19
Thanks! I'll give that a go! ;)

---

### Post by Gantlett on 2010-07-25
OK &#8211; so I worked the solution and thought I&#8217;d share!

The above link suggests a few ways to control power management in Ubuntu. The way that worked for me was using the following command:
```
pmi action suspend
```

Type this command in the terminal and follow the prompts to install all missing components.
After the components are installed, make sure the command actually sends your computer to sleep.

Note: This command shouldn&#8217;t require the SUDO prefix.

Once you have verified the command is successful, continue to install gnome-scheduler. This is a GUI that allows you to schedule tasks (it's a front-end for &#8220;crontab&#8221; and &#8220;at&#8221;. I love the CLI as much as the next geek, but let's face it - GUI is much easier on our brains). This program might also require a few pre-requisites. Just follow the prompts to install them. You&#8217;ll find the program in the System section of the Applications menu (I think it&#8217;s called Task Scheduler).

Launch the program from the GUI and create a new task. Set your schedule and leave all settings at default.

Type the following command for the schedule to run:
```
/usr/sbin/pmi action suspend
```

Happy sleeping! :popcorn:

---

