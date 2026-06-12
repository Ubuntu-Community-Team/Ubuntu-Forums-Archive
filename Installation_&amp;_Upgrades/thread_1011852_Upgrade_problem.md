---
title: "Upgrade problem"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by flebas on 2008-12-15
Today I ran Update Manager and after waiting for download an install I got some error message with task to manually run dpkg --configure-a. When I try to do this I get this 

 unknown option --configure-a

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

and after running aptitude I get

Setting up ufw (0.23.2) ...
Can't exec "/var/lib/dpkg/info/ufw.config": Permission denied at /usr/share/perl/5.10/IPC/Open3.pm line 168.
open2: exec of /var/lib/dpkg/info/ufw.config configure 0.23.2 failed at /usr/share/perl5/Debconf/ConfModule.pm line 59
dpkg: error processing ufw (--configure):
 subprocess post-installation script returned error exit status 255
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted


I'm totally new in Linux just to know.

Help, please!

---

### Post by ajgreeny on 2008-12-15
```
sudo dpkg --configure -a
``` will do it, or it should.  You must run dpkg as root, hence the sudo in front of the command.  Type your password when asked, though nothing will show, and you should be OK.

---

### Post by wphampton on 2010-10-14
Obviously this is an old thread, but I also had this problem which was the result of messing up the permissions of everything below /var/.  Stupidly I ran some recursive permissions script at /var thinking I was in /var/www/.  

Anyway, all I had to do in this case was make that ufw.config file executeable again.

```
sudo chmod +x /var/lib/dpkg/info/ufw.config
```

Then run the command that ajgreeny explained.

```
sudo dpkg --configure -a
```

Wesley

---

