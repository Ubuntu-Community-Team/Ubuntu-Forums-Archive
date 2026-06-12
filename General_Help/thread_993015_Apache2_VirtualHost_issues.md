---
title: "Apache2 VirtualHost issues"
date: 2008-11-25
forum: General Help
---

### Post by somethingkindawierd on 2008-11-25
I am trying to get a virtual host set up on Apache. Here is what I want: a virtual host [www.stkw.local]("http://www.stkw.local") that points to my /home/beebe/Dropbox/Sites folder. I have set up the /etc/hosts file and the sites-available and sites-enabled files, and ran "sudo a2enmod userdir" as directed by various tutorials online in this forum ([like here]("http://ubuntuforums.org/showthread.php?t=984872")). But, I continually get either a 403 error, or the browser is directed to the default /var/www/ folder. Any ideas? Here are my hosts file and my virtual host file:

/etc/hosts
```
127.0.0.1 localhost
127.0.0.1 www.stkw.local stkw.local

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```/etc/apache2/sites-available
```
NameVirtualHost 127.0.0.1:80
<VirtualHost 127.0.0.1:80>
ServerName www.stkw.local
ServerAlias stkw.local *.stkw.local
DocumentRoot /home/beebe/Dropbox/Sites
        <Directory /home/beebe/Dropbox/Sitess>
                Options Indexes
                AllowOverride All
                Order Allow,Deny
                Allow From All
        </Directory>
</VirtualHost>
```

---

### Post by reality1011 on 2008-11-25
First, I noticed a typo:

 <Directory /home/beebe/Dropbox/**Sitess**>

Second, I think you should use the directory as the / for the root of the directory root, otherwise I believe apache thinks you are trying to access  /home/beebe/Dropbox/Sitess within your DocumentRoot /home/beebe/Dropbox/Sites

---

### Post by Coreigh on 2008-11-25
I agree with the possible typo issue that Reality1011 mentioned. You will also likely have to alter permissions to allow apache to access your DocumentRoot folder (/home/beebe/Dropbox/Sites) < spelling?

the group www-data needs to have at least read access and if it is a"drop box" then write access too. I recommend some sort of file creation limits, unless this is a secure site accessible only by you.

---

### Post by somethingkindawierd on 2008-11-25
You're right about the typo...not sure how that made it into this post cause I caught it before I saved the original file...but fixing it did not help. Still get the error. As long as 127.0.0.1 points to /var/www/ I can access the files. But if I point it to my dropbox then I get the permission denied error. What should I set the permissions to? Do I change the owner, the read-write access? I tried setting the permissions of the /Dropbox/Sites folder to www-data but that did not help.

I noticed that in the apache2/sites-enabled default site it has /var/www/ set as the directory. I tried changing this to my /home/beebe/Dropbox/Sites folder and I get the same permission denied error.

Furthermore, I noticed in the apache2/mods-enabled usirdir module that it has two lines at the top that appear to specify which directories are allowed as user-specified directories. It did say home/*/public_html so I changed it to home/*/Sites but that also had no affect.

---

### Post by Coreigh on 2008-11-25
Here is a snippet from one of my VirtualHosts files where I alias the documentation folder:
> 
    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128 192.168.0.5
    </Directory>


And as long as the folder has read access (drwxr--r--) then you should be able to access the files.

Is it maybe the Alias line? The way mine works is [http://web.domain.com/doc/](http://web.domain.com/doc/) and not ...com/usr/share/doc/

Also just a sanity check you are trying to access the site from the local computer where it is hosted and not from a different computer, right?

---

### Post by redilyn on 2008-11-25
> **somethingkindawierd said:**
> You're right about the typo...not sure how that made it into this post cause I caught it before I saved the original file...but fixing it did not help. Still get the error. As long as 127.0.0.1 points to /var/www/ I can access the files. But if I point it to my dropbox then I get the permission denied error. What should I set the permissions to? Do I change the owner, the read-write access? I tried setting the permissions of the /Dropbox/Sites folder to www-data but that did not help.

I noticed that in the apache2/sites-enabled default site it has /var/www/ set as the directory. I tried changing this to my /home/beebe/Dropbox/Sites folder and I get the same permission denied error.

Furthermore, I noticed in the apache2/mods-enabled usirdir module that it has two lines at the top that appear to specify which directories are allowed as user-specified directories. It did say home/*/public_html so I changed it to home/*/Sites but that also had no affect.

Easiest way I know to solve this problem is to type the following in the terminal

sudo chown www-data -R /home/beebe/Dropbox

This should solve your permission denied errors.

After this you will have to change the permissions so your user account can write to the folder (it is now owned by www-data). I do not know the chmod numbers but perhaps something like chmod 766 would work. I'm sure someone can/will reply with the right chmod command.

Hope this helps

---

### Post by somethingkindawierd on 2008-12-04
Ok, I figured it out :)


[LIST=1]
[*]The user directory */home/userdir* needs *Group* and 
*Other* Folder Access set to 'Access Files'. I had it set to 'None'.
[*]The */etc/apache2/mods-enabled/userdir.conf* file needs to have 'UserDir public_html' changed to the correct folder if you want to access a folder other than '/home/userdir/public_html'. I changed it to 'UserDir Sites'.
[*]Then, in the same *userdir.conf* file, update the *<Directory /home/*/public_html/>* to read *<Directory /home/*/Dropbox/Sites/>*.
[/LIST]
So, here are all the changes I made:
/etc/hosts
```
127.0.0.1 localhost beebe-imac-ubuntu www.virtualhost.local

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```/etc/apache2/sites-enabled/virtualhost.local.conf
[html]NameVirtualHost 127.0.0.1:80

<VirtualHost 127.0.0.1:80>
    ServerAdmin email@email.com
    
    ServerName stkw.local
    ServerAlias www.stkw.local *.stkw.local
    
    DocumentRoot /home/userdir/Dropbox/Sites/
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /home/userdir/Dropbox/Sites/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>[/html]/etc/apache2/mods-enabled/userdir.conf
[html]<IfModule mod_userdir.c>
        UserDir Sites
        UserDir disabled root

        <Directory /home/*/Dropbox/Sites/>
                AllowOverride FileInfo AuthConfig Limit Indexes
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
                <Limit GET POST OPTIONS>
                        Order allow,deny
                        Allow from all
                </Limit>
                <LimitExcept GET POST OPTIONS>
                        Order deny,allow
                        Deny from all
                </LimitExcept>
        </Directory>
</IfModule>[/html]

---

