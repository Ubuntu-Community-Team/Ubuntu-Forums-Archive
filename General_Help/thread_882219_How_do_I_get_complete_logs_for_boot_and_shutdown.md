---
title: "How do I get **complete** logs for boot and shutdown?"
date: 2008-08-06
forum: General Help
---

### Post by kung fu buntu on 2008-08-06
**GOAL**: I want to log to a file "all" messages that get printed to screen during system boot and shutdown.

**MOTIVE**: detect and fix the source of those error messages that get printed to screen (e.g. xpto failed to start). Eventually learn more about the boot process.

I have googled, I have debianed and ubuntued... but I haven't found an answer yet.

**DEAD ENDS**:
1) nor dmesg, nor bootlogd through /var/log/boot, nor /var/log/kern.log provide all messages, in fact nor /var/log
I know this because I was able to see the message "Activating swapfile...done." on screen, but wasn't able to find-grep it in /var/log

2) using a serial port is not an option

3) using a camera is not an option

4) (after the system boots) doing ctrl+alt+f1 doesn't lead nowhere because shift+pgup doesn't work


[Someone](http://www.linux-archive.org/ubuntu-user/112381-help-needed-enable-boot-log-hardy-heron.html) suggested the use of kopt in grub, but I didn't quite understood it. Maybe  someone can comment on it.
> 1 - Add kopt=console=tty12 to grub.1st and run update-grub
2 - edit /etc/syslog.conf - change the entry already there but
commented out to also use tty12



Thank you for any help.

---

### Post by kaivalagi on 2008-08-06
I am not sure, but whenever I need details I look at /var/log/syslog

There are also compressed log files under the same naming convention e.g./var/log/syslog.1.gz

Not sure whether this will do for what you want?

---

### Post by kung fu buntu on 2008-08-07
The thing is that there is information that is printed to the console during boot/shutdown that doesn't seem to be written to any file.

As I said, I find-grep'ed through /var/log and didn't find some information I saw printed.
The compressed log files refer to previous boot/reboots.

---

### Post by kaivalagi on 2008-08-07
> **kung fu buntu said:**
> The thing is that there is information that is printed to the console during boot/shutdown that doesn't seem to be written to any file.

As I said, I find-grep'ed through /var/log and didn't find some information I saw printed.
The compressed log files refer to previous boot/reboots.

Fiar enough, any logged info pertaining to the startup will only reside in /var/log as far as I am aware, if you can't find the details in there that you see on screen then I presume they aren't logged.

Maybe the logging process can be configured to log more details?

---

