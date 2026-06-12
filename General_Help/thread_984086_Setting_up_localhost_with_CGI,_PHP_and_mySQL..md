---
title: "Setting up localhost with CGI, PHP and mySQL."
date: 2008-11-16
forum: General Help
---

### Post by Melindrea on 2008-11-16
I was unsure on whether this should go in general help or server, but it's not technically a full server I'm looking to set up, so I decided here was probably more relevant.

I've been using [this]("https://help.ubuntu.com/community/ApacheMySQLPHP") guide to set it up. The only difference is that in /etc/apache2/sites-available/mysite I changed the standard cgi-bin things to this:

```
ScriptAlias /cgi-bin/ /home/marie/public_html/cgi-bin/
	<Directory "/home/marie/public_html/cgi-bin/">
```

However, trying to get a script (one that is at least legit perl) to work was impossible, as it gives me a error 500, Internal Server Error. 

Then I tried installing PHP5, still according to the guide. Instead of running the PHP-page (a very simple one, it's just a page that happens to be named .php) it insists on wanting to save it. libapache2-mod-php5 is installed (and the newest version). Running sudo a2enmod php5 tells me that PHP5 is already enabled. 

So. Anyone have any idea on where to start? =)
Thank you,
Melindrea

---

### Post by bodhi.zazen on 2008-11-16
The php issues is a *little* annoying :twisted:

See this post : [http://ubuntuforums.org/showpost.php?p=5780073&postcount=12](http://ubuntuforums.org/showpost.php?p=5780073&postcount=12)

As far as your cgi-bin my first guess is a permissions problem. In ubuntu apache runs as www-data, so make sure that directory is readable by this user

---

### Post by Melindrea on 2008-11-16
Thanks, I'll look it over =) Once I have a fully functionable local server, I'll mark the topic as solved =)

---

### Post by Melindrea on 2008-11-16
Hmm. My /etc/apache2/apache2.conf file doesn't have a DirectoryIndex...

---

