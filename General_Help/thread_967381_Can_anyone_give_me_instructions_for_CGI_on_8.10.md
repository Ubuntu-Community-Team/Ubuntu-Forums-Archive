---
title: "Can anyone give me instructions for CGI on 8.10"
date: 2008-11-02
forum: General Help
---

### Post by Rarez on 2008-11-02
Hi there,

Could anyone advise me as to how to setup apache2 with cgi say running in folder /var/www/cgi-bin. I cannot seem to get it to work.

Thanks in advance.
rarez

---

### Post by ju2wheels on 2008-11-02
I think it should be enabled by default when you install Apache.

Check the 000-default file in /etc/apache2/sites-enabled and look for a section like this:

```

	#ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	#<Directory "/usr/lib/cgi-bin">
	#	AllowOverride None
	#	Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
	#	Order allow,deny
	#	Allow from all
	#</Directory>

```

I dont remember if I commented out mines or not but if it has #'s on the beginning of each line like above then just remove them and restart apache.

Do not create a "cgi-bin" folder in /var/www. Put your cgi files in /usr/lib/cgi-bin/.

---

### Post by Rarez on 2008-11-02
Still following your advice does not work. Should there be something inserted into /etc/apache2/apache2.conf ??

---

### Post by Rarez on 2008-11-02
Got it working thanks for your help. Didn't know it had to go into /usr/lib/cgi-bin/ that helped along with rewritting my cgi scripts to reflect correct directories :-)

---

