---
title: "Problems installing MySQL"
date: 2008-08-15
forum: General Help
---

### Post by mb_webguy on 2008-08-15
Ok... I had this problem about a month ago, and was only able to fix it with a clean install of Ubuntu, and I'd rather not have to do that again if I can help it.

I'm having problems installing MySQL.  When I run "sudo apt-get install mysql-server-5.0" I get the following output:```
matt@the-tardis:~$ sudo apt-get install mysql-server-5.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl
  mysql-client-5.0
Suggested packages:
  dbishell libcompress-zlib-perl mysql-doc-5.0 tinyca
Recommended packages:
  libhtml-template-perl mailx
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl
  mysql-client-5.0 mysql-server-5.0
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/36.2MB of archives.
After this operation, 107MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package libnet-daemon-perl.
(Reading database ... 138337 files and directories currently installed.)
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.38-1.1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2017-1.1_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.601-1_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.005-1_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.51a-3ubuntu5.1_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.51a-3ubuntu5.1_i386.deb) ...
Setting up libnet-daemon-perl (0.38-1.1) ...
Setting up libplrpc-perl (0.2017-1.1) ...
Setting up libdbi-perl (1.601-1) ...
Setting up libdbd-mysql-perl (4.005-1) ...
Setting up mysql-client-5.0 (5.0.51a-3ubuntu5.1) ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
/var/lib/dpkg/info/mysql-server-5.0.postinst: line 143: /etc/mysql/conf.d/old_passwords.cnf: No such file or directory
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've tried uninstalling it using both the Synaptic "Complete Removal" option and "sudo apt-get remove --purge mysql-server-5.0", but when I try to install it again, I get the same output as above.  If I try "sudo dpkg --configure -a", I get:```
matt@the-tardis:~$ sudo dpkg --configure -a
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
/var/lib/dpkg/info/mysql-server-5.0.postinst: line 143: /etc/mysql/conf.d/old_passwords.cnf: No such file or directory
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0

```
...which is essentially the last bit of what I get when I try to install.

I really, *really* need to get MySQL working.  I've never had problems like this installing MySQL on any other machine, and am willing to do yet another clean install of my system if that's what it takes, but only as a last resort.  Please help!

---

### Post by mb_webguy on 2008-08-15
Bump for great justice.

---

### Post by mb_webguy on 2008-08-15
Update:  So I looked at line 143 of /var/lib/dpkg/info/mysql-server-5.0.postinst and discovered it's trying to create the /etc/mysql/conf.d/old_passwords.cnf file.  When I check, there's no /etc/mysql/conf.d directory, so I create it.  

The next time I run "sudo dpkg --configure -a", it can't read the /var/lib/mysql/mysql/user.frm file.  When I check it, the /var/lib/mysql/mysql/ directory is owned by root:root.  So I chown it do mysql:mysql.

The next time I run "sudo dpkg --configure -a", everything looks good.  Configuration finishes with no problem.  Then it tries to start the mysql daemon, and it throws an error, saying that it can't read the  /etc/mysql/my.cnf file.  Thinking that it must be another permissions problem, I look in the /etc/mysql directory, and... no my.cnf file.  I look in /etc for it, but no joy.  I do a system-wide find, and still nothing.  I change the permissions for the /etc/mysql directory and try reinstalling the mysql-server-5.0 package in an attempt to get it to write the my.cnf file, but still nothing.

I've looked online to find a copy of the my.cnf file for MySQL 5.0, to see if I could drop it in, but so far I haven't found it anywhere.  As I absolutely must get MySQL running on this machine, I guess I'm going to reinstall. Again.  

... *sigh* ...

Frak.  So much for my Friday night.

I'm still curious about this problem, especially since I've had it twice now, and so may likely encounter it again.  I can't believe I'm the only person to have encountered it.  It seems to me to be a file permission error in the package.  I'm not going to mark this thread as solved, since it isn't, even if I do manage to successfully install MySQL after *yet another* clean install of Hardy.  If anyone comes up with a solution or at least is able to successfully identify the problem, please post.

---

### Post by cariboo on 2008-08-16
Re installing the operating system is not going to solve your problem. Have you tried:

```
sudo dpkg-reconfigure mysql-server-5.0
```

After you created the old_passwords.conf file?

Jim

---

### Post by mb_webguy on 2008-08-16
> **cariboo907 said:**
> Re installing the operating system is not going to solve your problem.

Well, I just finished re-installing the operating system and it solved the problem.  :wink:  I made sure to reinstall MySQL, Apache, and PHP right after I set up all of the basics (e.g. video and wireless drivers, etc.), and everything went smoothly.

I still would like to know if anyone else has or had this problem, and ideas on how to fix it, since it's happened to me twice already, and I'll likely be doing another clean install of the operating system when Intrepid is released in October...

---

### Post by p_quarles on 2008-08-16
I would have tried deleting the entire /etc/mysql directory. It was most likely something in there causing problems, and by reinstalling Ubuntu you were really just getting rid of that bad config file anyway.

---

### Post by mb_webguy on 2008-08-16
I did that.  I did a complete removal with Synaptic, and then ran "sudo find / | grep mysql" and deleted everything I recognized as belonging to MySQL and not something else, like PHP or Apache.  Then when *that* didn't help any, I did a complete removal of PHP, Apache, Amarok, and everything else that used MySQL that I knew I could reinstall relatively painlessly.  I finally had it stripped down to the point that it was unlikely I'd ever get it back as it was without a clean install anyway, and yet I was still unable to get dpkg to write the my.cnf file.

---

### Post by grryf on 2009-10-09
I had The same situation and I managed to fix it basing on your post:

```
sudo bash
chown -R mysql:mysql /var/lib/mysql/mysql/
touch /etc/mysql/my.cnf
chown -R mysql:mysql /etc/mysql/
/etc/init.d/mysql stop
/etc/init.d/mysql start
```

.........[ OK ]


What I did was flushing privileges after moving to another server, then my new root password changed to this from old server but i didnt know that and i did remove mysql-server and reinstall it again. This causet so horrible-many-hours-wasing problem. BUG REPORT!!!

Best Regards,
grryf

---

### Post by amckenzie on 2010-03-29
I found the solution to this.  I know the thread is old, but it's the first one that came up in google when I searched for the error, so hopefully putting the solution here will solve someone's problem down the road.  I found it here:  

[https://lists.ubuntu.com/archives/ubuntu-server-bugs/2009-February/010085.html](https://lists.ubuntu.com/archives/ubuntu-server-bugs/2009-February/010085.html)

In short, the problem is caused by mysql-common needing to be reinstalled when you purge and reinstall mysql-server.  This can be forced without damaging dependencies by doing the following:  I've included the removal of mysql-server as well.

```

> sudo -i
> apt-get --purge remove mysql-server*
> apt-get install mysql-server
> dpkg --purge --force-depends mysql-common
> sudo apt-get install -f

```

Note that line 3 (the "install mysql-server" line) will fail.  It will be fixed in line 5, so don't worry about it yet.

At this point, MySQL should be working correctly, with a default set of databases and tables.

I hope this helps someone!

-Alex McKenzie

---

