---
title: "Automatically back up entire /var/www and /etc/apache2 directories to external drive"
date: 2008-09-15
forum: General Help
---

### Post by jamieh on 2008-09-15
Hey,
Okay I have a web server with Ubuntu 8.04 and Apache. I was wondering if there was a way to make it so every morning at 3am it automatically backs up the entire /var/www and /etc/apache2 directories to an external USB hard drive, replacing the backup of the previous night.

The internal drive is a 4 year old Maxtor 60gb  and I don't know how much longer it will last, so I want to keep a backup.

---

### Post by SBJ95 on 2008-09-15
I'm not sure on this, but maybe you could try Bacula.  Supposedly, it's pretty versatile, but I haven't used it.  I think it is geared more towards backing up networks, but it should work fine for a single server.  Plus, if you aren't comfortable editing config files, it has a web config interface, I think.

I found a [tutorial](http://www.bacula.org/fr/dev-manual/Automated_Disk_Backup.html) that tells you how to do it, but it is for multiple machines.

I don't know if that's any help, but I tried.  :D

---

### Post by deijsman on 2008-09-15
mkdir /media/YOUREXTDRIVE/rsync/
sudo rsync -vaP --delete /var/www /media/YOUREXTDRIVE/rsync
sudo rsync -vaP --delete /etc/apache2 /media/YOUREXTDRIVE/rsync

make a cron job to run this at 3am...

---

### Post by Cheesehead on 2008-09-15
> **jamieh said:**
> every morning at 3am it automatically backs up the entire /var/www and /etc/apache2 directories to an external USB hard drive,

If you're not allergic to the command line, this is fairly easy using cron for the timer to start an rsync job (or two)


1) Build a command to do the job: "/usr/bin/rsync -av /var/www /media/yourdrive/backup/" or some such. The first time you run it, it will take a while, but the second time may be very short! Rsync transmits only the *changes*.

2) Edit/create your crontab with 'crontab -e' (no sudo)
You crontab entry will look like:
* 3 * * * usr/bin/rsync -av /var/www /media/yourdrive/backup/
* 3 * * * usr/bin/rsync -av /etc/apache2 /media/yourdrive/backup/
depending, of course, on the exact shell script you settle on.


You can also back up even more easily than that - you can build a quick script that will rsync your backups *every time that specific USB drive* gets mounted, or every time you logoff (or startup), or even if you type an alias command like 'backup' into a terminal.

---

### Post by jamieh on 2008-09-15
The only things in /media are "cdrom" and "cdrom0" :confused: :confused: :confused: . I don't even have a CD drive. Ubuntu was installed with an external one.

---

