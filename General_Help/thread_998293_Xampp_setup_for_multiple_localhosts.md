---
title: "Xampp setup for multiple localhosts"
date: 2008-11-30
forum: General Help
---

### Post by retrodans on 2008-11-30
I am having trouble setting up xampp on my recent ubuntu install.  I have installed xampp, created my working directory, and checked out my site to the path:
```
/home/retrobadger/working_files/retrobadger.net
```

Then I modified the file 'httpd-vhosts.conf' so it now read:

```
#
# Virtual Hosts
#
# If you want to maintain multiple domains/hostnames on your
# machine you can setup VirtualHost containers for them. Most configurations
# use only name-based virtual hosts so the server doesn't need to worry about
# IP addresses. This is indicated by the asterisks in the directives below.
#
# Please see the documentation at 
# <URL:http://httpd.apache.org/docs/2.2/vhosts/>
# for further details before you try to setup virtual hosts.
#
# You may use the command line option '-S' to verify your virtual host
# configuration.

#
# Use name-based virtual hosting.
#
NameVirtualHost *:80

#
# VirtualHost example:
# Almost any Apache directive may go into a VirtualHost container.
# The first VirtualHost section is used for all requests that do not
# match a ServerName or ServerAlias in any <VirtualHost> block.
#
<VirtualHost *:80>
	DocumentRoot home/retrobadger/working_files/retrobadger.net
	ServerName local.retrobadger.net

	<Directory "home/retrobadger/working_files/retrobadger.net">
		Options Indexes FollowSymLinks Includes ExecCGI
		AllowOverride All
		Order allow,deny
		Allow from all
	</Directory>
</VirtualHost>


```

Finall I add the line to my hosts file:
```
127.0.0.1	local.retrobadger.net
```

I also deleted the index.html file that was in htdocs.

Now when I put 'http://local.retrobadger.net/' into the browser, it shows me a directory view of al the folders within htdocs (including xampp).  This should point to my working files directory.  Can anyone help me understand why this is not working?

Thankyou for your help
Dan

---

### Post by Dr Small on 2008-11-30
DocumentRoot and Directory should be:
```
**/**home/retrobadger/working_files/retrobadger.net
```

Also, did you restart XAMPP?
```
sudo /etc/init.d/lampp restart
```

---

### Post by retrodans on 2008-11-30
Yeah, I tried it both with and without a slash at the beginning, it now has the slash as suggested.  I also restarted xampp using the line:

```

/opt/lampp/lampp reload
```

Which I assume is the same as the way you suggested, just in a different folder.

Cheers for your advise, Dan

---

### Post by Dr Small on 2008-11-30
Just asking since you never mentioned it; Did you uncomment the httpd-vhosts.conf line in /opt/lampp/etc/httpd.conf?
```
#Include etc/extra/httpd-vhosts.conf
```

After you do that, restart XAMPP again.

---

### Post by retrodans on 2008-12-02
Ah, well I feel a little embarrassed now, should have guessed vhosts may not have been getting run.  All sorted now.  Thankyou for your help.

Dan

---

