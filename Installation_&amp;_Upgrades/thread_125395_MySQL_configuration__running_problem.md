---
title: "MySQL configuration / running problem"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by guitar.is.good on 2006-02-03
Hi,

Quite new to linux and I basically wanted to build a fileserver and a webserver with php and MySQL.  Fileserver / SAMBA works fine, apache and PHP work fine, just having some teething problems with MySQL that for the life of me I can not figure out, so would appreciate any help in order to get me up and running :) 

I followed the instructions located [https://wiki.ubuntu.com/ApacheMySQLPHP]("https://wiki.ubuntu.com/ApacheMySQLPHP")

Basically followed it word for word execpt php4 id not exist, substituing in php5 instead worked fine for everything.

Ok, installed it all and executed the line below for the post mysql installation

sudo ./bin/mysql_install_db --user=mysql

I read the post MySql installation advice as well from the Mysql website, [http://dev.mysql.com/doc/refman/5.0/en/unix-post-installation.html]("http://dev.mysql.com/doc/refman/5.0/en/unix-post-installation.html")
 
Ok, it turns into a bit of a blur but my current ubuntu state is that apache is running with php installed and I can access the php info from pc's on my LAN.  

However, I basically cannot touch MySql :(

The mysql_install_db said to set a root password for the root using the command:

mysqladmin -u root passoword 'password'

I tried that and am unsure what happened.

Basically now I cant do anything,  if I run mysql with the following commands

myslq 
mysql -u mysql
mysql -u root

etc, + having sudo infront  I get the following error

ERROR 1045: Access denied for user: 'home@localhost' (using password: NO)
ERROR 1045: Access denied for user: 'mysql@localhost' (using password: NO)
ERROR 1045: Access denied for user: 'root@localhost' (using password: NO)

I get the same errors when trying to turn off mysql using the command:

mysqladmin -u mysql shutdown

like

error: Access denied for user: 'root@localhost' (using password: NO)

I have a feeling this is a stupid little configuration or command line error on my belhaf, so I apologise in advanced!  But I can just not figure out how to get this working.

I have done a small amount MySQL / php webdevelopment in the past on university servers but never really any setup / running the server myself.  And since a graduated in spectember I do not have access to these servers, but would like to continue to learn web design with php and mysql, hence why I am building this server.

Any help would be most appreciated! tia

---

### Post by BenTyreman on 2006-02-03
It looks like MySQL has set a password to your root account. To connect on the command line, you will need to use the command
```
mysql -u root -p
```
to tell it you will be supplying a password.

By far the easiest way to administer a MySQL installation to to use phpMyAdmin, available in the repos.

---

### Post by guitar.is.good on 2006-02-03
Thanks for your reply, unfortunately I am still stuck.

Using the -p does prompt for a password, but I do not believe I have entered one yet becuase I was getting those previous errors, certainly now when I try that it is not acctepting my password.  I have tried vaious combinations for the user, such as root, home (my main/admin account) and mysql all with my system password and the password I intend to use for mysql (the one I used when attempting to set the root password).

But any time I try and do anything I am still being denied access.  :(

The php Adim in php looks good, and I will certainly give that a go when I get it up and running, but I would like to be able to be able to access mysql and do things like shut it down first.

hmm, spent nearly 5 hours now just trying to get access with no avail :cry: 

I'm stumped! :confused: 

Thanks again for your reply

---

### Post by BenTyreman on 2006-02-03
Try doing this to reset the password
> 
   1.

      Stop mysqld and restart it with the --skip-grant-tables --user=root options (Windows users omit the --user=root portion).
   2.

      Connect to the mysqld server with this command:

      shell> mysql -u root

   3.

      Issue the following statements in the mysql client:

      mysql> UPDATE mysql.user SET Password=PASSWORD('newpwd')
          ->                   WHERE User='root';
      mysql> FLUSH PRIVILEGES;

      Replace &#8220;newpwd&#8221; with the actual root password that you want to use.
   4.

      You should be able to connect using the new password.


---

### Post by guitar.is.good on 2006-02-03
Thanks again for your reply.

Unfortunately I am stugelling to shut mysql down, all attempts via mysqladim result in those same errors.

Tried rebooting etc but the MySQL service started automatically, tried searching for the MySQL process, but it apperars to be hidden :(.  Trying to start a new one it comes back to me and says that one is already in process.  Any chance you know how to kill the process behind the scenes or prevent it from automatically starting?

Is there anyway to verify the mysql_install_db was done correctly.  Not too sure why the --user mysql was included in that line.

I honestly dont think I did, but is it possible I could of somehow set the password with something and basically locked myself out big time. (I double checked for no typos when trying in, + i got on of those errors anyone saying access denied afterwards)

Could there be anything wrong with the user setup? i.e. that line was run with --user mysql (quite new to linux but that account doesnt exist but seems to exist in the background)

I'm very tempted to wipe the pc and start again unless theres any more help you can offer (If I could be cheeky, do those wiki installation instructions look ok :D )

I'm running a standard installation of the current iso download of Ubuntu on a standard desktop pc.  

Thanks so much for all you help so far! 4am time for sleep...

---

### Post by BenTyreman on 2006-02-03
```
sudo /etc/init.d/mysql stop
```
to stop the mysql daemon

```
sudo /usr/sbin/mysqld --skip-grant-tables --user=root
```
to start the mysql daemon, ignoring the permissions (grant) tables

```
mysql -u root
```
to connect to the mysql daemon as the root user

```
UPDATE mysql.user SET Password=PASSWORD('newpwd') WHERE User='root';
```
to set the root password to "newpwd" (choose your password here)

```
FLUSH PRIVILEGES;
```
to reload the grant table

```
sudo /etc/init.d/mysql restart
```
to restart the mysql daemon, this time it will load the grant table

Should do the trick.

Incidently, I don't think you needed to run the mysql_install_db. In fact, the man pages suggest this should not needed to be used by standard users.

---

### Post by Horndog on 2006-02-03
I have a less than high opinion about some of those HowTo's. Anyway just go into the system monitor and look for  MySQL running and just right click and Kill it. To restart just reboot. Unless you want to get fancy and do some kind of command.

---

### Post by guitar.is.good on 2006-02-04
Aha! Success! \\:D/ 

Thanks you so much Ben, woke up this morning saw your new post and worked instantly.  The only slight difference I had to use --mysql for the initial startup when skipping the grant tables (said something on the lineof using msql becuase was enetered into the command line earlier + it did it automatically) but it seems to work perfectly :), updated the root passwords, can start the server normally and access it now with the -u root -p.

Thanks so much for all your help and sticking with it! :D 

Cheers! :D

Cheers for your reply as well Horndog, couldnt see the Mysql process in system monitor, but the command Ben suggested did the trick nicely. thanks.

---

### Post by lizardfoot on 2006-02-11
Ben,

You saved my head from exploding.  I was trying to get mysql working all day and was almost ready to throw the machine out the window.  Then I read your post and somehow, magically, mysql started working for me.

Thanks.

---

### Post by jinacio on 2006-02-12
same here, thanks everyone for the help

(btw i had to use "sudo mysql -u root -p")

Cheers

---

### Post by urbansurfer on 2006-04-02
Thanks a million guys I was having the same problem and this post saved me after spending 5/6 hours Ben you are a genius !!!!!

---

### Post by superfiko on 2007-01-07
One more person saved by Ben's post. I wonder why ubuntu's guys decided to make it work this way.

Andrea

---

### Post by jvelasco on 2007-01-11
It worked for me too, thanks ben ! 

Note that I also had to use mysq instead of root since it said I could not use root because mysql had already been used from the command line

---

