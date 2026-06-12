---
title: "[SOLVED] help me set up weblog for wife"
date: 2008-11-09
forum: General Help
---

### Post by ARhere on 2008-11-09
My wife wants to start doing a blog on my apache server.  I could just create my own web page with frames that calls to a text file, but I was hoping for something a little more refined.

I have tried tDiary and pyB<something-or-other> and both attempts have been frustrating as heck!

Any suggestion?  I would like something that integrates into apache and has some sort of "read me to install and use" documentation.

-AR

---

### Post by m_duck on 2008-11-09
I've not done any blogging or anything myself but have heard that [wordpress](http://wordpress.org/) is pretty easy to set up?

---

### Post by Dr Small on 2008-11-09
Wordpress is simple to setup and install.
If you have Php5, MySQL and PhpMyAdmin along with your Apache installation, setting up Wordpress will be a breeze.

---

### Post by Paul41 on 2008-11-09
I use Wordpress also and it is very easy. My wife happily uses it also.

---

### Post by ARhere on 2008-11-09
Wordpress just looks like a client... is that true?

EDIT:  I have read through the documentation and now I feel stupid.  I have no idea how to run/install MySQL.  Am I heading down the wrong path?  My original goal was to setup a blog website for my wife using my own apache server.

-Andrew

---

### Post by th89 on 2008-11-09
You may be trying too much at first. I would suggest getting a domain name, and redirecting that to a WordPress Blog hosted on WordPress. Then, after 3 months or so, you could see if your wife still wanted to blog, and if she was still wanting to, you could set it up on your server, and export/import the information onto your own server. The reason I say this is statistics show that about 95% of people give up on their blogs, becuase they cannot get a decent reader base. I had a blog I maintained that had almost 800 readers a day, and ended up giving up on it, due to not having enough time to do it (I'm a full-time student). Just a suggestion.

---

### Post by ARhere on 2008-11-09
Ok, I have installed LAMP on my server, (*well, the 'l' part was already there  ;-)*) and setup a database and user.

The next step in the instructions say to run **/usr/share/wordpress/wp-admin/install.php** but every time I do, Firefox just wants to save the file and not open it.  When I do the same with **/var/www/test.php** it opens the PHP file in Firefox just fine.

I have changed the ownership of ./wp-admin to my account but same result.  What gives??

[color=blue]EDIT: I tried copying the install.php to /var/www/ and it open fine in Firefox, but gives me errors because the paths of other files is hard coded to the ./wp-admin folder.[/color]

-AR

---

### Post by mjpatey on 2008-11-09
Forgive me for asking, but why not just use Blogger or something similar?  Google hosts it (extremely reliable), and lots of well-known, professional, money-making blogs use it very successfully.  It's extremely easy to use if you need it to be (non-techies love it), and is easily customized in every way if you're comfortable with HTML and CSS.

---

### Post by baeksu on 2008-11-09
The problem is on the server side. It's not supposed to send the .php files, but process them and then send .html instead.

Make sure you've installed php5 and libapache2-mod-php5 packages. After that restart apache and test again.

As for which bloggin software to use, I've found [simplephpblog](http://www.simplephpblog.com/) to be quite adequate for a personal blog. It doesn't require mysql (only apache and php). Also, it's easy to back up (just copy the whole blog directory from the server).

---

### Post by ARhere on 2008-11-09
> **mjpatey said:**
> Forgive me for asking, but why not just use Blogger or something similar?  Google hosts it (extremely reliable), and lots of well-known, professional, money-making blogs use it very successfully.  It's extremely easy to use if you need it to be (non-techies love it), and is easily customized in every way if you're comfortable with HTML and CSS.

To quote Capitan Kirk from Star Trek V, "...because it's there."

Learning how to do stuff like this is rewarding to me.

-Andrew

---

### Post by mjpatey on 2008-11-09
I understand completely.  :-)  I've taken on lots of those projects, including the initial switch from Windows to Ubuntu.

More power to you!

---

### Post by ARhere on 2008-11-09
> **baeksu said:**
> The problem is on the server side. It's not supposed to send the .php files, but process them and then send .html instead.

Make sure you've installed php5 and libapache2-mod-php5 packages. After that restart apache and test again.

As for which bloggin software to use, I've found [simplephpblog](http://www.simplephpblog.com/) to be quite adequate for a personal blog. It doesn't require mysql (only apache and php). Also, it's easy to back up (just copy the whole blog directory from the server).

Ok, I rebooted but nothing has changed.  I have noticed something, when I try ```
$firefox /var/www/test.php
``` the browser opens up and asks me where I want to save the file.  But when I open the browser and type in **http://www.<mydomain>.com/test.php** the file is served correctly.  I am only able to do the latter because it is in my apache folder.

So how do I access the install.php file without copying the whole directory to the /var/www/ folder???

-AR

---

### Post by bodhi.zazen on 2008-11-10
check out this post :

[http://ubuntuforums.org/showpost.php?p=5780073&postcount=12](http://ubuntuforums.org/showpost.php?p=5780073&postcount=12)

---

### Post by Paul41 on 2008-11-10
/var/www is the only place apache will serve files from unless you tell it otherwise.

---

### Post by ARhere on 2008-11-11
ok,  I will check these suggestions this weekend. No time to play with new baby during weekday.

-AR

---

### Post by ARhere on 2008-11-14
Awesome!

Check it out, [http://www.arhere.com/jblog](http://www.arhere.com/jblog)

Got my wife's blog up and running and it is pretty sweet!

-AR

---

### Post by bodhi.zazen on 2008-11-14
> **ARhere said:**
> Awesome!

Check it out, [http://www.arhere.com/jblog](http://www.arhere.com/jblog)

Got my wife's blog up and running and it is pretty sweet!

-AR

Looks nice, congrats :)

---

