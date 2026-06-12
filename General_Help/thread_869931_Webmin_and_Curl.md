---
title: "Webmin and Curl"
date: 2008-07-25
forum: General Help
---

### Post by Ginger The Cat on 2008-07-25
Hi,

I am trying to install [Jomres]("http://www.jomres.net/")  which is a Joomla product.
To try it out I want to install it locally on my Ubuntu Hardy laptop and have decided to use Webmin to make things easier.

I have installed Webmin 1.420 from a .deb without any problems.

When I start the jomres_webinstall.php script I get the following error

> Starting download of [http://updates.jomres.net/joomla/Joomla_1.5.3-Stable-Full_Package.zip](http://updates.jomres.net/joomla/Joomla_1.5.3-Stable-Full_Package.zip)

Fatal error: Call to undefined function curl_init() in /var/www/jomres/jomres_webinstall.php on line 102

I assume this is because my Webmin doesn't have Curl built in (The is no mention of curl when I do a phpinfo().)

Is there some way of doing a partial rebuild to somehow add in a --with_curl or whatever the command is?

Or does anyone know where I can find info on how to build webmin from scratch.

Cheers

Mike

---

### Post by gimlithedwarf on 2008-07-25
Hi mike, my suggestion would be to get curl with ```
sudo apt-get install libcurl3 liblua5.1-curl-dev liblua5.1-curl0
```
be careful before running anything with sudo in front of it though

---

### Post by Ginger The Cat on 2008-07-25
Thanks for the reply.

I don't think that will work because that will install curl for me and my Ubuntu system.

What I want is for Apache/PHP to be installed with Curl in Webmin?

---

### Post by gimlithedwarf on 2008-07-25
that will install the curl modules for ubuntu so that curl is available to everything that wants to use it. I'm guessing thats what will make the whole thing work

---

### Post by Ginger The Cat on 2008-07-25
nope. Just tried it and its the same error.

---

