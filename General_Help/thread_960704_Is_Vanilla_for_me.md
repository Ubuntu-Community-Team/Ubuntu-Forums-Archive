---
title: "Is Vanilla for me?"
date: 2008-10-27
forum: General Help
---

### Post by Absinthe Minded on 2008-10-27
Hello all,

I have a couple of websites and I'd like to create discussion forums for them. I'm a Windows user who's making the switch to Ubuntu and I have absolutely no knowledge of installing a forum.

Yesterday I stumbled across [Vanilla]("http://getvanilla.com/") and thought it would be a great idea to use it since it's free. After poking around, I found I need to have MySQL installed on the server from which I want to host the forum and after a bit more poking around, I found that the company hosting my sites wants £200 to add MySQL.

So, is there a way to get a MySQL package for free? I'd really love to run a forum and learn some new skills like how to do it but I don't want to pay out that much since it's more a resource for those who visit my site and that are local to me. It's not like I'll earn anything for it and I don't expect there to be a massive uptake on the forum.

So, if anyone's up showing me how to do this for free, or pointing me in the right direction, I'd really appreciate it.

Thanks,
Nick.

P.S. I'm running Hardy here, if that matters!

---

### Post by ad_267 on 2008-10-27
Wow that's a lot of money just to add MySQL. Nearly all web hosts provide MySQL by default. No you can't add it for free to your web hosting. I suggest switching hosts.

You can easily install a web server (Apache), MySQL and PHP on your Ubuntu installation for testing purposes. See [http://howtoforge.com/ubuntu_lamp_for_newbies](http://howtoforge.com/ubuntu_lamp_for_newbies)

It is also possible to use the web server so that other people can access your site from your computer, but that requires your internet service provider to give you a static IP address and they often aren't happy about people hosting websites.

Edit: Do you have Windows or Linux hosting? Maybe they want that much money because you have Windows hosting.

---

### Post by jimv on 2008-10-27
My host costs me $8/month, and I get more bandwidth than I'll ever use, along with all the features I'd ever need.

I don't know if you can get it, but check Hostgator.com.

---

### Post by Absinthe Minded on 2008-10-27
Hi ad,

Thanks for that, what do you make of [these guys]("http://www.db4free.net/index.php?section=1")?
Also, I've just noticed that, as a home user, I can't even get MySQL from my hosting bunch - so it looks like I'd have to upgrade the account (which will cost even more!)

The guide you posted looks like just what I need, it's comprehensive and written for the newbie, so thanks for that.

So if I install via the tutorial, can I host the forum via my own PC? I have a spare box that I could install it all on and then just leave it running 24/7. Would that work, or have I got things entirely wrong?

Cheers,
Nick.

---

### Post by Absinthe Minded on 2008-10-27
> **jimv said:**
> My host costs me $8/month, and I get more bandwidth than I'll ever use, along with all the features I'd ever need.

I don't know if you can get it, but check Hostgator.com.

Cheers, jimv - I'll take a look!

---

### Post by ad_267 on 2008-10-27
It is possible to host the site from your own PC but it's probably a **lot** easier to use another host. Your ISP also has to let you have a static IP address (usually your IP address changes) so that people can access your site from the internet. Most ISPs aren't that happy about people hosting websites from their home internet accounts. It will also be a lot slower than a dedicated website host and you'd have to keep your computer running 24/7.

The point of installing a web server on your own computer is usually just for testing a website before uploading it to your host. So you can make sure you have the forum working on your own computer and then upload it to the host.

I'm not sure the db4free place is really what you're after, it's probably better to find a cheap webhost that provides MySQL support rather than using a separate database host. Most web hosts have MySQL in their most basic packages, the host you're with now sounds like a bit of a rip-off. The hostgator.com site that jimv posted has everything you need for $4.95 a month so that could suit you. 

I don't really want to post any web hosts as I've only used New Zealand based hosts before and don't have any experience with other hosts, but you should be able to find something that's cheap and local. With a google search I found this site offers hosting in the UK from £99 a year with MySQL: [http://www.firstserv.com/hostingServices/sharedHosting/linux/](http://www.firstserv.com/hostingServices/sharedHosting/linux/)

---

### Post by Absinthe Minded on 2008-10-27
Ok, ad, thanks so much for your help.

I'm going to install Ubuntu on my spare machine and install lamp, then see how I get on with it all. I may well be back with more questions!

My sites are hosted on a Linux server at the moment, btw.

So, thanks again - I'm installing Ubuntu on the other machine as I type!

Cheers,
Nick.

---

### Post by NullHead on 2008-10-27
Using a lamp server isn't as hard as it may seem. I host my own website and it's actually pretty easy, but I'm not that good of a security freak, so I'm always concerned that someone will hack into my web server. 

If you use a dedicated host that you pay for, they're usually very secure and you don't have to worry about it. 

My good friend uses [http://www.hostgator.com/](http://www.hostgator.com/) and it's extremely reliable and works great. It even comes with database and cpanel access. 

I'm not sure what you're looking for in a host, but I highly recommend hostgator as a host.

---

### Post by Absinthe Minded on 2008-10-29
Hi NullHead,

Thanks for that, I'm going to install it later so I'll let you know how I get on.

BTW, how do you go about actually putting stuff on the server? Is it GUI, or do I have to learn some command line gobbledygook?

Thanks again,
Nick.

---

### Post by NullHead on 2008-10-29
> **Absinthe Minded said:**
> Hi NullHead,

Thanks for that, I'm going to install it later so I'll let you know how I get on.

BTW, how do you go about actually putting stuff on the server? Is it GUI, or do I have to learn some command line gobbledygook?

Thanks again,
Nick.

Well I hate to break it to you, but there's is no GUI at all. The whole interface is through the command line. 

If can manage, install webmin. Learn how to use it. It will make your whole server experience a whole lot better than doing all the configuration by hand (on the command line). 

A few pointers though, you put your .html documents in /var/www ... that's on a default setup, but I highly using webmin to help you configure apache2.

---

### Post by ad_267 on 2008-10-29
If your server has a gui (eg if it is just your desktop) then you don't have to use the command line. What I did is set up symbolic links from /var/www/website_name to point to somewhere in my home directory where I had access to and then I could edit my websites without any worry and just drag and drop files into the website.

Yes you could use the command line to set up databases but you can also do this with something like phpMyAdmin.

---

### Post by NullHead on 2008-10-29
Webmin can handle databases.

---

### Post by Absinthe Minded on 2008-10-30
OK, guys,

Thanks for your continued help and support.

I've been following the LAMP install guide and I've hit a bit of a snag.

I Installed and tested Apache, getting the 'It Works!' page and then I moved onto installing and testing PHP - all went there too and I was able to access the test PHP page through the browser.

All good up until there.

The problem arose on setting up MySQL (as the guide said it might). Here's what I entered in the terminal:

```
sudo apt-get install mysql-server
```

During the install, the package asked me to set a password, which I did. it then asked me to repeat, so I did that and the install seemed to continue without problems.

Next I opened the my.cnf file using:

```
gksudo gedit /etc/mysql/my.cnf
```

and edited the bind address to match my IP so that I have access over the network.

Next up, the guide says to enter this:

```
mysql -u root
```

So I did, and I got the following error:

```
ERROR 1045: Access denied for user: 'root@localhost' (Using 
password: NO)
```

I looked at the link at the bottom of the guide [here]("https://help.ubuntu.com/community/MysqlPasswordReset")

The problem comes with the second line of code:

```
/usr/bin/mysqld --skip-grant-tables --user=root
```

I get:

```
/usr/bin/mysqld: No such File or Directory
```

So, that's where I'm stuck - I haven't got a clue what to do so any advice from you guys would be gratefully received!

Cheers,
Nick.

---

### Post by ad_267 on 2008-10-30
For your first problem just use "mysql -u root -p" so that it asks for your password. 

I don't think you need mysqld, I don't have it and my MySQL server works fine.

---

### Post by Absinthe Minded on 2008-10-30
Cheers, ad,

Now I'm getting:

```
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

Should I start at the beginning again?

Thanks,
Nick.

---

### Post by NullHead on 2008-10-30
I'd try re-installing the mysql server.

---

### Post by Absinthe Minded on 2008-10-30
Looks like that did it, I now have:

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.
```

Do I now continue with the rest of the guide, NullHead?

Thanks, btw!

---

### Post by NullHead on 2008-10-30
I'd say you're done if you have mysql working. Try using phpmyadmin, or using webmin to setup a sql database.

---

