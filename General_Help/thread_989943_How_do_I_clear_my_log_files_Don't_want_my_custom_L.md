---
title: "How do I clear my log files? Don't want my custom LiveCD to have my passwords on it!"
date: 2008-11-22
forum: General Help
---

### Post by Panarchy on 2008-11-22
Hi

Just wondering how to clear my logs?

Pretty sure they are all stored in /var/log

Once in the past, I completely deleted via command line both my tmp directory and my log directory using the rm -r command.

Then after I had made sure that they were gone, I recreated the directories using the mkdir command.

Still haven't been able to get that computer to boot up!!! :(

It was Ubuntu 8.04 BTW...

So anyways, back on topic, what I need to do is clear all logs (and tmp directory, though I think that's deleted at poweroff).

Including firefox logs.

Please tell me how to do this.

Thanks in advance,

Panarchy

PS: I don't know how much Ctrl+Shift+Del does... I tick all the boxes of course...

---

### Post by geirha on 2008-11-22
Deleting /tmp while the system is running is a bad idea as many programs store data in there, and thus deleting them may cause odd behavior in such programs. And if you have deleted /tmp (including the directory), you need to make sure you recreate it with correct permissions, which is full access to all users plus the sticky bit.
```
sudo mkdir /tmp
sudo chmod 1777 /tmp
```

As for passwords, I doubt any program would store passwords in /tmp or /var/log. To remove firefox's stored password, open firefox and select Tools -> Delete private data (or something like that). Other applications that store passwords will store them in your home folder somewhere.

---

### Post by Panarchy on 2008-11-22
Okay, thanks.

Also, how do I delete my log files?

EG: My cmd history (*cough* to new to linux, I mean my... what is it called? Bourne Again shell? I dunno... whatever the default shell/bash is!)

Please reply once more

Thanks in advance,

Panarchy

PS: If I delete the log directory, what chmod should I use once I've recreated it? Or is deleting the log directory a bad idea?

---

### Post by geirha on 2008-11-22
Your command history is stored in the hidden file ~/.bash_history , and yes, the default shell is bash.

Deleting the log files should be safe, though it contains subdirectories that also need to be recreated if you remove it with rm -r. Instead, use find to only remove the files.
```
sudo find /var/log -type f
```
will list all files under /var/log. Adding -delete behind that command will delete those files.

However, I haven't created a liveCD myself, but isn't it possible to just choose to skip those directories from whatever commands/programs you use?

---

### Post by Panarchy on 2008-11-22
Thanks, you just helped me delete;

```
/var/log/samba/log.winbindd
/var/log/samba/log.wb-HACKER-DESKTOP
/var/log/messages
/var/log/lpr.log
/var/log/user.log
/var/log/mail.info
/var/log/Xorg.0.log
/var/log/news/news.err
/var/log/news/news.notice
/var/log/news/news.crit
/var/log/Xorg.0.log.old
/var/log/user.log.0
/var/log/debug
/var/log/mail.info.0
/var/log/mail.log
/var/log/wtmp
/var/log/fsck/checkroot
/var/log/fsck/checkfs
/var/log/bootstrap.log
/var/log/fontconfig.log
/var/log/dmesg.0
/var/log/boot
/var/log/mail.log.0
/var/log/syslog.0
/var/log/wvdialconf.log
/var/log/pycentral.log
/var/log/debug.0
/var/log/dmesg
/var/log/gdm/:0.log
/var/log/gdm/:0.log.1
/var/log/gdm/:0.log.2
/var/log/daemon.log.0
/var/log/udev
/var/log/messages.0
/var/log/kern.log
/var/log/mail.warn
/var/log/mail.err
/var/log/cups/access_log.1.gz
/var/log/cups/access_log
/var/log/daemon.log
/var/log/installer/casper.log
/var/log/installer/initial-status.gz
/var/log/installer/version
/var/log/installer/partman
/var/log/installer/syslog
/var/log/dpkg.log
/var/log/lastlog
/var/log/auth.log.0
/var/log/btmp
/var/log/apt/term.log
/var/log/wpa_supplicant.log
/var/log/ConsoleKit/history
/var/log/syslog
/var/log/kern.log.0
/var/log/faillog
/var/log/auth.log

```

:guitar:

Thanks.

Oh, and what you said about just being able to leave it out of the livecd build, well this will be my first liveCD build, so I'm not so confident in my skills at leaving things out (and all that!).

And I've got exams next week, so don't expect a public release until at least next Saturday... (7 days from now)

And thanks again for all your help,

Panarchy

EDIT: How do I delete my other logs?

Like my sudo bash log

My sudo su bash log

And my backup logs for all of them

(I think that there's a default logrotate, so I need to delete the ones 'rotated' as well as any backup ones.)

Please tell me how to do this

Thanks in advance,

Panarchy

---

### Post by philinux on 2008-11-22
Passwords are not stored in the bash history and if you set FF not to store passwords and then tools clear private data all clear. Log files dont contain passwords either. Have a look through them. System>Admin>system Logs. Pretty mundane stuff.

---

