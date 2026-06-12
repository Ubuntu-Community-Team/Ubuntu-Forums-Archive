---
title: "How to install phpBB3 on Ubuntu?"
date: 2008-11-18
forum: General Help
---

### Post by UranUtan on 2008-11-18
Hi,

I am looking to install phpBB3 on Ubuntu for practice. I am novice in Ubuntu and know nothing about phpBB. If you have any links, documentation guidelines to share, I would greatly appreciate.

I assume I should use Ubuntu Server. But is it possible to use Ubuntu Desktop? I currently have a computer with Ubuntu Desktop 8.10 32 bits.

Thanks in advance for any help.

---

### Post by john183 on 2008-11-19
You can run phpBB3 on your Ubuntu 8.10 32bit system that you already have setup. you will need to install the LAMP server software (LAMP is Linux [which you already have], Apache, MySQL, and PHP), instructions are here: [http://ubuntuforums.org/showthread.php?t=976550](http://ubuntuforums.org/showthread.php?t=976550)

Then, if you haven't done so, download the phpBB3 software and install it. I have never used it myself, but they do have and extensive guide on their website: [http://www.phpbb.com/support/documentation/3.0/](http://www.phpbb.com/support/documentation/3.0/)
They also have links for flash tutorials, IRC support, knowledge base and support forums at:
[http://www.phpbb.com/support/](http://www.phpbb.com/support/)

Hope this helps you.

---

### Post by UranUtan on 2008-11-23
Super, Thanks for your help.

There should be a post rating system in this forum to reward expert points to members who give correct answers.

---

### Post by phillw on 2009-07-15
All went well !! - Synaptic Package manager took care & asked for passwords, the fact i wanted to use MySQL etc ..... But .... Can I find the blooming thing ? - can I heck - where, oh where, will it have put it ?!!!!

Not in ~home/phillw  not in  /var/www   - Any ideas where I point [http://localhost/](http://localhost/)..........

The config file is here ...

./usr/share/phpbb3/www/config.php

how do i get localhost to look there ?


Many thanks.

Phill.

---

### Post by az on 2009-07-15
> **phillw said:**
> All went well !! - Synaptic Package manager took care & asked for passwords, the fact i wanted to use MySQL etc ..... But .... Can I find the blooming thing ? - can I heck - where, oh where, will it have put it ?!!!!

Not in ~home/phillw  not in  /var/www   - Any ideas where I point [http://localhost/](http://localhost/)..........

The config file is here ...

./usr/share/phpbb3/www/config.php

how do i get localhost to look there ?


Many thanks.

Phill.

Either create a new site or change the default site to use /usr/share/phpbb3/www/ as it's DocumentRoot

Look in /etc/apache/sites-enabled and change the default site or copy it and change the copy.  (The files are actually in sites-available, but symlinked to sites-available so that some apache utilities work properly.)

---

### Post by phillw on 2009-07-15
Thanks for the reply - as i have a few test bits (like osCommerce) running in /var/www linked to localhost, i unistalled phpBB3, moved directories and popped it there !!

the index.php link now comes up ok, but there seems to be a different problem, it knows it is a new board & *should* allow me to configure it. alas no.

I've also popped a note onto the phpbb forum to ask if anyone there can help. I'm pretty sure it's me doing something wrong, but, as a rule, things install okay.

I got LAMP running doing it the manual way, osCommerce for me to learn and build an e-selling site etc. So not too sure what i have goofed up on this one !!

Still, you learn more when things don't work straight away, and I've had a pretty good run !!

Regards,

Phill.

---

### Post by phillw on 2009-07-16
Well,
        after mucho messing about - The EASY way to install phpBB is manually - I tried using Synaptics system and had a nightmare !!!

I removed the package, followed the simple instructions from the phpBB site and it was a piece of cake. Puzzled as to why Synaptics install went so horribly wrong, but the phpBB people told me that start screen wasn't even thiers - As the default one doesn't show 'powered by Debian" !!!!

Phill.

---

### Post by Friqenstein on 2009-10-19
I tried to use the Synaptic manager to install phpbb3 as well, but it botched itself pretty bad. Right around the part it was asking which database I wanted use and then it asked for a password for the database user... supplied the info and the damn thing just sat there in a grayed out screen for an eon before I killed it and started over.
Same crap again.

I'm going to attempt the manual install since I've done that in the past I know it should work.
I will say this is the only problem I've ever had with a package via Synaptic, but that doesn't make it OK in any regards. Curious as to what's causing the issue with this particular package.

Edit: *1* Now Synaptic cannot figure out how to remove the borked phpbb3. Go figure. Again it asks if I want to purge the database of all phpbb3 so I tell it yes... and again the grayed out screen when it's 'working'. No HDD activity, nothing.
Now it crashes and tells me that it may leave my system in an unstable state. And there is a big RED highlighted phpbb3 package in my Synaptic manager.

Anybody have a clue how to resolve this? Just want to clean up the mess that Synaptic has left behind.

Edit: *2* Nevermind. I just used my own method. I nuked the phpbb3 database from my postgresql server and re-created a pseudo phpbb3 database then re-tried the Synaptic un-install. It seemed to work this time.
Still not certain why the package doesn't seem to work with Synaptic very well.

---

### Post by phillw on 2009-10-19
> **Friqenstein said:**
> I tried to use the Synaptic manager to install phpbb3 as well, but it botched itself pretty bad. Right around the part it was asking which database I wanted use and then it asked for a password for the database user... supplied the info and the damn thing just sat there in a grayed out screen for an eon before I killed it and started over.
Same crap again.

I'm going to attempt the manual install since I've done that in the past I know it should work.
I will say this is the only problem I've ever had with a package via Synaptic, but that doesn't make it OK in any regards. Curious as to what's causing the issue with this particular package.

Edit: *1* Now Synaptic cannot figure out how to remove the borked phpbb3. Go figure. Again it asks if I want to purge the database of all phpbb3 so I tell it yes... and again the grayed out screen when it's 'working'. No HDD activity, nothing.
Now it crashes and tells me that it may leave my system in an unstable state. And there is a big RED highlighted phpbb3 package in my Synaptic manager.

Anybody have a clue how to resolve this? Just want to clean up the mess that Synaptic has left behind.

Edit: *2* Nevermind. I just used my own method. I nuked the phpbb3 database from my postgresql server and re-created a pseudo phpbb3 database then re-tried the Synaptic un-install. It seemed to work this time.
Still not certain why the package doesn't seem to work with Synaptic very well.


You seem to have had the same problems that I had. I can only restate what they told me on the phpBB3 help forum. Following the instructions from their site worked like a dream. 

Phill.

---

### Post by ispyisail on 2010-01-02
[https://help.ubuntu.com/community/PhpBB3](https://help.ubuntu.com/community/PhpBB3)

---

### Post by ltan on 2010-04-17
[Edit]
BLEH!  Apologies for dregging up a 3 month old thread...
[/EDIT]

> **ispyisail said:**
> [https://help.ubuntu.com/community/PhpBB3](https://help.ubuntu.com/community/PhpBB3)

ispyisail:  Did you create that wiki page?  If so, could you add the following?  If  not, below is a modification for the previous tutorial.

[SIZE=4]http://forums.yoursite.com[/SIZE]

To get phpbb3 to run  from [http://forums.yoursite.com](http://forums.yoursite.com), enter the following, replacing  yoursite.com as appropriate:

```
sudo ln -s  /etc/phpbb3/apache.conf /etc/apache2/sites-enabled/phpbb3
```Edit the phpbb3 configuration, use whatever editor you like...  I  use vi:

```
 sudo vi /etc/phpbb3/apache.conf
```I  replaced everything inside this file with:

```

<VirtualHost  *:80>
        ServerAdmin webmaster@localhost
         ServerName forums.yoursite.com
        DocumentRoot /var/www/phpbb/
         DirectoryIndex index.html index.shtml index.php
         <Directory />
                Options FollowSymLinks
                 AllowOverride None
        </Directory>
         <Directory /var/www/phpbb>
                Options Indexes  FollowSymLinks MultiViews
                AllowOverride None
                 Order allow,deny
                allow from all
                #  Uncomment this directive is you want to see apache2's
                 # default start page (in /apache2-default) when you go to /
                 #RedirectMatch ^/$ /apache2-default/
        </Directory>
</VirtualHost>

```Reload  apache

```
sudo /etc/init.d/apache2 reload
```After  you setup your domain registration, you now have your own  [http://forums.yoursite.com](http://forums.yoursite.com) site setup!

---

### Post by OliverHaslam on 2012-04-07
Sorry to drag this up, but won't you need to alter settings at your domain company to point to a subdomain?

Just curious. 

Cheers.

---

### Post by SeijiSensei on 2012-04-07
> **OliverHaslam said:**
> Sorry to drag this up, but won't you need to alter settings at your domain company to point to a subdomain?

Not if you run your own web and DNS servers like I, and other people here, do.

---

### Post by OliverHaslam on 2012-04-07
> **SeijiSensei said:**
> Not if you run your own web and DNS servers like I, and other people here, do.

I'm running my own web server, and to get my domain to hit it I had to alter DNS records at the domain registrar. I'd need to do that again for a subdomain, right?

If you run your own DNS - how do you set things at your domain registrar?

Cheers.

---

### Post by SeijiSensei on 2012-04-07
My records at the registrar say that my DNS servers are authoritative for the domains I manage.  I use DirectNIC, but I'd be surprised if other registrars don't enable you to specify your own server.

At the registrar I enter the addresses for my primary and secondary DNS servers (you need two) so that requests for example.com come to my servers.  Then it's just a matter of creating the proper zone files for bind9 to advertise.  For name-based hosting, say "forums.example.com" as well as "www.example.com", I usually use a CNAME alias for "forums" that points to "www", or use identical A records for both hostnames.

It might be possible to use the registrar's server as the secondary; I've never tried that.

---

### Post by OliverHaslam on 2012-04-07
> **SeijiSensei said:**
> My records at the registrar say that my DNS servers are authoritative for the domains I manage. I use DirectNIC, but I'd be surprised if other registrars don't enable you to specify your own server.
 
At the registrar I enter the addresses for my primary and secondary DNS servers (you need two) so that requests for example.com come to my servers. Then it's just a matter of creating the proper zone files for bind9 to advertise. For name-based hosting, say "forums.example.com" as well as "www.example.com", I usually use a CNAME alias for "forums" that points to "www", or use identical A records for both hostnames.
 
It might be possible to use the registrar's server as the secondary; I've never tried that.
 
Sorry, I've not followed that at all :)
 
Right now I have both [www.oliverhaslam.com]("http://www.oliverhaslam.com") and oliverhaslam.com point to my server's IP. What do you gain from having your machine act as a DNS server over how I have it set up?
 
DNS/IPs are still coming back to me after a few years away :)

---

### Post by SeijiSensei on 2012-04-07
1) I run my own mail servers and need to have the appropriate MX records.

2) I can change the hostnames, address assignments, subdomains, etc., at will.

I've always maintained my own DNS servers starting way back when only Network Solutions could register domains, and everyone was expected to maintain their own servers.  Hosted domains weren't really available when I started doing this stuff in the mid-90's.  Those were the days when everyone was expected to read the RFCs and figure out how to conform to standards on their own.

The only thing you need a registrar for is to insert your domain into the root nameservers.  If the registrar hosts the domain, it will register your domain name with the roots and include its nameserver addresses as authoritative.  If you host your domain, the registrar will register your domain name with the roots and include your servers as authoritative.

---

### Post by OliverHaslam on 2012-04-08
> **SeijiSensei said:**
> 1) I run my own mail servers and need to have the appropriate MX records.

2) I can change the hostnames, address assignments, subdomains, etc., at will.

I've always maintained my own DNS servers starting way back when only Network Solutions could register domains, and everyone was expected to maintain their own servers.  Hosted domains weren't really available when I started doing this stuff in the mid-90's.  Those were the days when everyone was expected to read the RFCs and figure out how to conform to standards on their own.

The only thing you need a registrar for is to insert your domain into the root nameservers.  If the registrar hosts the domain, it will register your domain name with the roots and include its nameserver addresses as authoritative.  If you host your domain, the registrar will register your domain name with the roots and include your servers as authoritative.

This is interesting, and for some reason it's not quite sinking in :)

So if I have my records and names set at my registrar, what do I do to change over?

Thanks :)

---

### Post by SeijiSensei on 2012-04-08
I don't what else to tell you, Oliver. Somewhere in your registrar account there should be an option to specify the nameservers for your domain or to use the registrar's servers.  If you want to run your own nameservers, you would select the first option and enter the addresses of the two nameservers you've configured.  You'd first have to install bind9 on the two machines, and configure one of them as the primary.  That means taking the DNS records you have at the registrar and converting them into "resource records" in a DNS "zone file."  You'd then configure the secondary machine to be a "slave" to the first one.  With this arrangement, changes you make to the primary server will be automatically transferred to the secondary.

That said, I suggest taking the "if it ain't broke, don't fix it" approach.  Configuring bind9 isn't for the faint of heart, and you'll need to learn about how to construct zone files, set up primaries and secondaries, do zone transfers, etc.  You could either browse the Internet for help, or read a good book on the subject like [this one](http://shop.oreilly.com/product/9780596100575.do).

If you have a home or office network, you might start by installing bind9 on a couple of servers there and building an internal DNS server to answer requests for machines on your local network.  If you can figure out to set up forward and reverse resolution (the so-called in-addr.arpa domain) for your local network, you'll be ready to tackle running DNS servers on the public Internet.

---

### Post by nexx on 2012-04-28
Does anyone tried to install phpbb3 from the software center on ubuntu 12.04 ?

---

### Post by CharlesA on 2012-04-28
> **nexx said:**
> Does anyone tried to install phpbb3 from the software center on ubuntu 12.04 ?
I haven't tried it, I always install it manually from their website.

---

