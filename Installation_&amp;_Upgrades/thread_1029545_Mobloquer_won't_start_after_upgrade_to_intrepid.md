---
title: "Mobloquer won't start after upgrade to intrepid"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by falafalaf on 2009-01-03
When trying to start Mobloquer 0.5.1-intrepid after upgrade from Hardy to Intrepid I get the following error:```
** Fatal: Mobloquer is already running.
Aborted
```This occurs after several restarts and shutdowns.  Moblock seems to be working fine, though.  Any clues?

---

### Post by jre on 2009-01-04
This is the relevant source part.
/src/main.cpp:
```
        //Stolen from qgrubeditor :-P
        //Check if mobloquer is already running
        QFile lockFile( QDir::tempPath() + "mobloquer.lock" );
        if ( lockFile.open( QIODevice::ReadOnly ) )
        {
                QTextStream lockStream( &lockFile );
                QString pid = lockStream.readLine();
                if ( QDir( "/proc/" + pid ).exists() )
                {
                        qFatal( "Mobloquer is already running." );
                        return 1;
                }
                lockFile.close();
        }
```
But I don't get it where the lockfile resides. Furthermore I can even start several instances of mobloquer at the same time...
To get the source and investigate yourself do a
```
mkdir mobloquer
cd mobloquer
apt-get source mobloquer
```

Otherwise I recommend to completely uninstall mobloquer and then scan your harddisk for remaining mobloquer files and delete them.
```
sudo aptitude purge mobloquer
sudo find / -name "*mobloquer*"
```

Indeed moblock will work independently of mobloquer, because MoBlock is started automatically by moblock-control as a daemon.

---

### Post by falafalaf on 2009-01-04
Thanks for your help.  I had reinstalled but I had not done a search for leftover files.  It turns out that Mobloquer puts a lockfile, called "tmpmobloquer.lock," in the root directory.  It seems that it doesn't get removed with the rest of the program so it has to be removed manually.  The file consists of a four digit code that I'm not going to try to decipher, but likely was the cause of the problem as everything works now.

*Addendum*  The four digit code is the PID.  I should have read the file before I deleted it the first time to see what could have been the problem.  Possibly it was listing a PID that was in use by another program.

---

### Post by jre on 2009-01-05
> **falafalaf said:**
> It turns out that Mobloquer puts a lockfile, called "tmpmobloquer.lock," in the root directory.

Glad you could solve your problem.

The file /tmpmobloquer.lock will only be created if you run it as root (or perhaps with sudo). A normal user does not have the right to write there.
Running applications with superuser privileges is generally not recommended. Instead you should start mobloquer as normal user and give (if necessary) the user password for sudo within the application.
That's the way I do it, and therefore I did not see this behaviour. Note that this is just a general recommendation, independently of your last problems.

The root directory as place for a lockfile is a bug in mobloquer. I don't know if I can solve this, but I have changed the packages (mobloquer 0.5-3 to be released later) so that this file is deleted on "purge" - thanks!

---

### Post by falafalaf on 2009-01-05
You are right that it would be a bad idea to run such a program as root and, accordingly, I do not and have not run it as root.  I did not enter my password to run as su, either, so there would be no way, that I know of, that it could run as root without my knowing.  The lockfile has the user set as owner, so I'm pretty sure that it is not somehow mysteriously been run as su or root.  I have no idea how it is possible for it to have been written to root and, unfortunately, I'm probably not an advanced enough user to figure it out. It likely should have put the file in /tmp, as there are a few mobloque files that are placed there. I don't know C++, but if Google be an honest prophet then ```
QFile lockFile( QDir::tempPath() + "mobloquer.lock" );
``` should write the file to /tmp, regardless of whether the user or the root runs it.  That it is written to root is probably a sign that something is wonky with my system.  I can write a file to the root directory as user, though; is that not normal?

---

### Post by jre on 2009-01-05
Probably /var/lock/ would be the correct place.

If I start mobloquer as root or with sudo I also get the file directly in the root directory (/tmpmobloquer.lock).

If I start it as normal user and give the user password for gksu within the app I don't get the lockfile.

Anyway, the root directory should not be writable for a normal user.
```
$ ls -al /
total 105
drwxr-xr-x  23 root root  4096 2009-01-05 18:37 .
drwxr-xr-x  23 root root  4096 2009-01-05 18:37 ..
drwxr-xr-x   2 root root  4096 2009-01-03 12:26 bin
drwxr-xr-x   4 root root  1024 2008-12-29 15:43 boot
lrwxrwxrwx   1 root root    11 2008-04-17 22:58 cdrom -> media/cdrom
drwxr-xr-x  14 root root  4360 2009-01-05 15:29 dev
drwxr-xr-x   3 root root  4096 2008-04-17 23:13 emul
drwxr-xr-x 138 root root 12288 2009-01-05 18:22 etc
drwxr-xr-x   8 root root  4096 2008-08-18 17:45 home
drwxr-xr-x   2 root root  4096 2008-04-17 22:59 initrd
lrwxrwxrwx   1 root root    30 2008-10-16 20:27 initrd.img.old -> boot/initrd.img-2.6.26-1-amd64
drwxr-xr-x  16 root root 12288 2009-01-03 12:26 lib
lrwxrwxrwx   1 root root    20 2008-04-17 23:13 lib32 -> /emul/ia32-linux/lib
lrwxrwxrwx   1 root root     4 2008-04-17 22:59 lib64 -> /lib
drwx------   2 root root 16384 2008-04-17 22:57 lost+found
drwxr-xr-x   3 root root  4096 2009-01-05 15:28 media
drwxr-xr-x   2 root root  4096 2007-11-19 19:21 mnt
drwxr-xr-x   2 root root  4096 2008-04-17 22:59 opt
dr-xr-xr-x 150 root root     0 2009-01-05 11:45 proc
drwxr-xr-x  18 root root  4096 2008-12-15 18:48 root
drwxr-xr-x   2 root root  4096 2009-01-03 12:26 sbin
drwxr-xr-x   2 root root  4096 2008-09-16 09:22 selinux
drwxr-xr-x   3 root root  4096 2008-04-18 02:54 srv
drwxr-xr-x  11 root root     0 2009-01-05 11:45 sys
drwxrwxrwx  13 root root  4096 2009-01-05 18:39 tmp
drwxr-xr-x  11 root root  4096 2008-07-03 17:59 usr
drwxr-xr-x  15 root root  4096 2008-12-27 21:33 var
lrwxrwxrwx   1 root root    27 2008-10-16 20:27 vmlinuz.old -> boot/vmlinuz-2.6.26-1-amd64

```
The rwx triplets (read,write,execute) are for owner,group,other.

You can change privileges with chmod and the owner with chown.
E.g
```
chown root.root /
chmod 755 /
```

---

