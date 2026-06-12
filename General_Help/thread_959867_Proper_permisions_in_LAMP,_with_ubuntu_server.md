---
title: "Proper permisions in LAMP, with ubuntu server?"
date: 2008-10-26
forum: General Help
---

### Post by TBOL3 on 2008-10-26
I'm fairly new to the world of LAMP, but I can't seem to get permissions right.

I'm trying to run opengoo, and it needs to have the ability to edit various files and folders.  As of yet, they only way I've been able to allow apache to edit the files, is to chmod them to 777.

Apparently, you're supposed to be able to add www-data to the root group, and then you can just chmod it to 775, but that still doesn't work.

So, can any of you give me a better, more secure, way to allow files to be edited, without the need to allow ANYONE to edit them?

Thank you.

---

### Post by alecjw on 2008-10-26
chown the files to the user www-data


Edit: wait, im confused... are they already owned by www-data?

---

### Post by TBOL3 on 2008-10-26
I've actually tried both.  I first added www-data to the groups root and admin.  That didn't work.

SO I chown(ed) opengoo to www-data. And it still doesn't work.

---

### Post by alecjw on 2008-10-26
Whats the output of
grep -R APACHE_RUN /etc/apache2/

---

### Post by TBOL3 on 2008-10-26
I can't really copy and paste it, because it's on another computer, but it says that the APACHE_RUN user, and group, is www-data.

---

### Post by TBOL3 on 2008-10-26
Alright, here is what it looks like:
/etc/apache2/envvars:export APACHE_RUN_USER=www-data
/etc/apache2/envvars:export APACHE_RUN_GROUP=www-data
/etc/apache2/apache2.conf:User ${APACHE_RUN_USER}
/etc/apache2/apache2.conf:Group ${APACHE_RUN_GROUP}

---

### Post by bodhi.zazen on 2008-10-26
Ubuntu does things a little different :

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

In general you can have things owned by root or root.www-data

readable by everyone is "OK".

---

### Post by TBOL3 on 2008-10-26
I apologize for my ignorance, but I didn't see any way that could help me set permissions.

Also, I'm not saying I shouldn't make it readable by everyone, I'm saying I shouldn't make it editable by everyone.

So, I'm still confused as to why it's not working, please help... Thanks.

---

### Post by bodhi.zazen on 2008-10-26
Set permissions with chown and chmod

chown = change ownership

chmod = change permissions

Ubuntu also uses sudo 

    [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) 
    gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

 
[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml) 

        [uhelp]community/FilePermissions[/uhelp]

---

### Post by TBOL3 on 2008-10-26
So, are you saying that I should set the permissions to root?

I already now how to set permissions, I just don't know what to set them to.

---

### Post by bodhi.zazen on 2008-10-27
I guess I am not sure what you are asking then.

In Ubuntu apache runs as the user "www-data" (without quotes obviously).

So if you want the user www-data to modify (write) a file, www-data must be allowed to write to the file or directory.

so, set the owner to root, group to www-data, and set group permissions to allow the group www-data to write to the file or directory.

IMO at least, that is how I would do it. 

Is this your question ?

---

### Post by TBOL3 on 2008-10-27
Yep, except that it's not working.  Maybe I did something wrong, I'll try again when I get home.

---

### Post by TBOL3 on 2008-10-27
Alright, let me try to clarify.

I add www-data to both root, and admin, by typing in

sudo usermod -G root -a www-data
I do the same for admin as well.

I then go to /var/www
and type

sudo chown -R www-data opengoo

But it still doesn't work.  Can you please help me?  Thank you.

---

### Post by alecjw on 2008-10-27
Probably a stupid question but is the user www-data still a member of the group www-data?

---

### Post by bodhi.zazen on 2008-10-27
What are you trying to do ?

apache runs as a user "www-data"

Say you have a directory "foo" in /var/www/html/foo

sudo chown root.www-data /var/www/html/foo
sudo chmod 770 /var/www/html/foo

If you are wanting to write to that directory you will either need to be root (sudo -i) or your user will need to be a member of www-data

---

### Post by alienprdkt on 2008-10-27
> **TBOL3 said:**
> So, are you saying that I should set the permissions to root?

I already now how to set permissions, I just don't know what to set them to.


Actually it is up to the user, but I have created a group just for Apache users. :)

1. Create a new group called webteam: 
groupadd webteam 
2. Add htmlguruuser to the webteamgroup: 
usermod –G webteam htmlguru 
3. Change the ownership of the DocumentRootdirectory (and all the subdirectories below it): 
chown –R httpd.webteam /www/htdocs 
This command sets the directory ownership to Apache (that is, the httpd user) and the group ownership to webteam, which includes the htmlguru user. In other words, both Apache and htmlguru will both have access to the document tree. 
4. Change the permission of the DocumentRootdirectory (and all the subdirectories below it) as follows: 
chmod -R 2570 /www/htdocs 
This command ensures that the files and subdirectories under the DocumentRootare readable and executable by the Apache user and that the webteamgroup can read, write, and execute everything. It also ensures that whenever a new file or directory is created in the document tree, the webteam group will have access to it. 

adding new users to the webteam is as simple as running the following command: 
usermod -G webteam new_username 
Similarly, if you wish to remove an existing user from the webteamgroup, simply run: 
usermod -G username [group1,group2,group3,...] 
where group1, group2, group3,and so on are groups (excluding webteamgroup) that this user belongs to. 
You can find out which group(s) a user belongs to by running the group 
usernamecommand. 

If httpdis your Apache user and webdevis your developer group, you should set permission for /www/cgi-binas follows: 
chown -R httpd.webdev /www/cgi-bin 
chmod -R 2570 /www/cgi-bin 
Alternatively, if you only wish to allow only a single user (say cgiguru) to develop CGI scripts, you can set the file and directory permission as follows: 
chown -R cgiguru.httpd /www/cgi-bin 
chmod -R 750 /www/cgi-bin 

Here the user cgiguruowns the directory and the group (specified by Group directive) used for Apache server is the group owner of the directory and its files. Finally, the log directory used in the CustomLogand ErrorLogdirectives should only be writable by the rootuser. Recommended permission setting for such directory (say /www/logs) is as follows: 
chown -R root.root /www/logs 
chmod -R 700 /www/logs 

this how to was taken from Apache2 Bible
chapter 18 web security

hope this helps out

---

### Post by TBOL3 on 2008-10-27
> **bodhi.zazen said:**
> What are you trying to do ?

apache runs as a user "www-data"

Say you have a directory "foo" in /var/www/html/foo

sudo chown root.www-data /var/www/html/foo
sudo chmod 770 /var/www/html/foo

If you are wanting to write to that directory you will either need to be root (sudo -i) or your user will need to be a member of www-data

I feel stupid now.  I think I know what my problem was.

I was typing in sudo chown www-data opengoo
when I should have been typing in:
chown root.www-data opengoo.

It works now.

THANK YOU!!!

---

