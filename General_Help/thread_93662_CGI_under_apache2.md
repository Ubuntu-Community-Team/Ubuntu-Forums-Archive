---
title: "CGI under apache2"
date: 2005-11-22
forum: General Help
---

### Post by jonathanhayward on 2005-11-22
I've installed apache2, but apache2.conf makes zero reference to a cgi-bin directory or any ExecCGI references, even in comments. What do I add to have a working cgi-bin directory?

++ Jonathan Hayward, [email]jonathan.hayward@pobox.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

** If you'd like a Google Mail ( gmail.com) account, please tell me!

---

### Post by suRoot on 2005-11-22
Can you post your httpd.conf?  All you should need is to load the module, eg:

```
LoadModule cgi_module modules/mod_cgi.so
```

create a script alias:

```
ScriptAlias /cgi-bin/ "/var/www/cgi-bin/"
```

and set the directory parameters:

```
<Directory "/var/www/cgi-bin">
    AllowOverride None
    Options None
    Order allow,deny
    Allow from all
</Directory>
```

I've not run apache on Ubuntu, but I can't imagine it being any different than other platforms.  The paths may be different, that's all.

---

### Post by jliedeka on 2005-11-22
Did you check out the README file in /etc/apache2?  The Debian/Ubuntu way of doing things is to make everything modular.  You can create symbolic links in mods-enabled to files in mods-available to include whatever modules you need.  You can then create site configurations in sites-available and symlink then to sites-enabled.  

You can ignore all that if you want but it makes it easier to change things later.

The default site uses /usr/lib/cgi-bin as the CGI directory.  Here is the stanza for it:

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>
The ScriptAlias just maps [http://your.site/cgi-bi](http://your.site/cgi-bi) to /usr/lib/cgi-bin
The Directory stanza sets the permissions.  Options ExecCGI is the important one.  You can have cgis in any directory you want as long as that option is turned on.

That use of ScriptAlias is a little puzzling to me.  Normally I would just use a plain Alias because all they are doing is aliasing a directory.  Normally I'm used to script aliases pointing to actual scripts.

---

