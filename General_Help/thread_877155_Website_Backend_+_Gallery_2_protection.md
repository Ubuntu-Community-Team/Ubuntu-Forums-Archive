---
title: "Website Backend + Gallery 2 protection"
date: 2008-08-01
forum: General Help
---

### Post by jay0316 on 2008-08-01
Gallery is part of a back end website (a parent directory that is not gallery2) that I would like password protected. So, once the user logs into the backend website, I want them to be able to click a link that takes them to gallery 2 without entering in their password info again.

I tried removing the password protection for Gallery 2 and just dropping it below a password protected parent directory, but because gallery2 installs itself outside the web directory when installing on ubuntu, the Gallery does not inherit the protection from the parent directory.  So, you can by pass the homepage of the backend and navigate directly to gallery 2 without a password, which of course is a problem.

Is there a way to protect gallery 2 using the protection that should be inherited from the parent directory?

Here is some more info:

[I]Gallery installed itself in var/lib/gallery2. In order to get apache to view this directory (since it is outside of the normal var/www/htdocs structure) I had to create a alias in the apache config file example:

Alias /gallery2 "/usr/share/gallery2"
<Directory "/usr/share/gallery2">
AllowOverride None
Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
order deny,allow
</Directory>

Everything works fine I can browse to [www.example.com/gallery2/main.php](www.example.com/gallery2/main.php) and view files. The problem I'm having is that I want to password protect this directory. I successfully protected the main [www.example.com](www.example.com) directory, but if I browse to [www.example.com/gallery2/main.php](www.example.com/gallery2/main.php) I'm not prompted to log in. I believe that is because the "gallery2" actually resides outside of the var/www/ directory.[/I]

Thanks!
J

---

### Post by jay0316 on 2008-08-04
bump :confused:

---

