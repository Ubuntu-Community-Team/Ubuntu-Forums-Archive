---
title: "Apache isolated virtualhosts"
date: 2008-09-28
forum: General Help
---

### Post by Exaby1e on 2008-09-28
I'm using ubuntu server on my VPS and I'm trying to find a way to let users on my server set up their own independent websites. I've installed Apache, MySQL and PHP. I also use virtualhosts i Apache for each site. The files for each site are stored in the users home directory.

The problem is that apache needs read and eventually write access to each website, which causes a high security risk because someone could write and simple php-script to access other users website files.

My goal is to make Apache run each virtualhost as the user the site belongs to, instead of the standard www-data user (and group). I have spent many hours searching for a tutorial or instructions how to solve this problem, but I haven't found any good solution. Some of them only works for Apache 1.3 and I'm using 2.2.
The closest thing I've found is SuEXEC, but it seems like it doesn't work with PHP at all, only CGI.

So, if someone knows any way to solve this problem, please help me. :neutral:

---

### Post by ju2wheels on 2008-09-28
PHP has a setting for this... its user_dir. [http://us.php.net/security.cgi-bin.doc-root](http://us.php.net/security.cgi-bin.doc-root) 

It will restrict PHP access to that directory for the user or to doc_root if no user is specified in the url.


Also for the virtualhost part, research Apache URL rewriting. Essentially if you want user1.mysite.com/url to point to the users home directory then I think you have to use URL rewriting to change it to whateversite.com/~user/url. The point is that regardless of the virtual domain, I think the end result has to have ~user/url so PHP knows where to point it (this is assuming you are using only one instance of Apache and PHP).

---

### Post by Exaby1e on 2008-09-29
> **ju2wheels said:**
> PHP has a setting for this... its user_dir. [http://us.php.net/security.cgi-bin.doc-root](http://us.php.net/security.cgi-bin.doc-root) 

It will restrict PHP access to that directory for the user or to doc_root if no user is specified in the url.


Also for the virtualhost part, research Apache URL rewriting. Essentially if you want user1.mysite.com/url to point to the users home directory then I think you have to use URL rewriting to change it to whateversite.com/~user/url. The point is that regardless of the virtual domain, I think the end result has to have ~user/url so PHP knows where to point it (this is assuming you are using only one instance of Apache and PHP).

Thanks for your answer. This solution seems to work, but not exactly as I want it. The problem is that i want a user to be able to access files in his/her home directory through php, which isn't possible this way.

The best way to solve the problem would be to get Apache to run each virtualhost as the user and group which the site belongs to. I found this tutorial, [http://tigreraye.org/Using%20PHP%20with%20fcgid%20&%20suexec%20on%20Apache%202.2](http://tigreraye.org/Using%20PHP%20with%20fcgid%20&%20suexec%20on%20Apache%202.2), but it requiers the fcgid-module, which I don't have. It also says PHP has to support the FastCGI interface. Anyone who knows how to do this?

---

