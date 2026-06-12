---
title: "Ebox or WebMin and vhosts problem"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by crazycoders on 2009-08-29
Allright, i had a box with the latest version of ubuntu installed and here is the setup:

Ubuntu server 9.x (don't remember the revision but it's recent, like 1 month not more)
Apache 2
MySql
Php
SVN
and... WebMin

Now old your horses, i know i'm not supposed to use WebMin, it seems it's not recommended anymore and not safe. I don't really care since i'm on a private server that no one will actually try to access, it's a dev server for my company. It has ties outside because we are doing telecomutting but it's not an officially published server.

So, i installed webmin. What made me search for answers was that i couldn't seem to setup two simple vhosts on my machine namely cmdb.domain.com and svn.domain.com. I shouldn't need to tell you what the SVN subdomain does right? It was my first install and it worked marvelously.

Now, this morning i tried setting up my cmdb.domain.com vhost and it seems everything went well until i realized that oops, my SVN subdomain stopped responding. And then i started searching for answers but what i got so far is... don't use webmin... wow how helpful.

I tried removing webmin, it worked, i installed ebox using apt-get install ebox-*. Bad idea, this thing installed a TON of modules i didn't need as all i needed was a vhost management module and a user/group management module. Remember this is a dev box. I can manage coding and server admin but not my partner, he's a CPanel user.

Ok, so now i fired up ebox, and then what... looking to setup vhosts, httpd proxy? Hummm nope, where is that damn thing! Can't find the web management module installed. I tried to reinstall ebox, enable disable some modules, still nothing working. So i ended up removing ebox and reinstalling webmin which actually WORKS.

Ok, so now after so much rambling, here is my question:

Why Ebox? Can it manage Web Server (apache2) vhosts? If so, how? If not... Why can't my vhosts configured with webmin work? I'm not new with all this... i've done it before on several other servers (not with webmin or ubuntu, but i'm not a newbie on linux at least)

Can anyone help? What do you need more?

---

### Post by crazycoders on 2009-08-29
Ok, forget the vhost question, i finally got it working after 3h of work on it :P

For anyone wondering the reason...

Change the entry in /etc/apache2/ports.conf:

NameVirtualHost *:80

to

NameVirtualHost *

And that is all. Probably i could have also fixed it specifying port 80 in all my vhosts, but anyway, it's fixed.

I now hope to get answers regarding Ebox...

---

