---
title: "How Do I: LDAP &amp; SAMBA"
date: 2008-10-12
forum: General Help
---

### Post by cyauch on 2008-10-12
Still working on setting up an Ubuntu server to provide central net logon authentication for a few Linux clients, and followed steps in this link a few times, but to no avail ([http://www.rrcomputerconsulting.com/view.php?article_id=3#22](http://www.rrcomputerconsulting.com/view.php?article_id=3#22)).  It appears I haven't been able to work out the DNS issue, so going to leave it dynamic (re: router will assign IP for now).  Right now, I can't get a linux client to authenticate against the server.  No biggie for now.  

So my question is this: what, at a minimum, do i need to install on the server to provide file sharing?  

From doing tons of reading, it looks like all i really need is Samba to do this.  Windows clients won't be connecting the server, and my printer is working via wireless great.  Because windows clients won't be connecting, I am assuming I won't need OpenLDAP / LDAP installed? 

For user authentication, do I need to add each user on the server as a Samba user?  Is there a quick and dirty How To on this? 

Because I won't be using a domain, do I have to worry about ntp time problems with regards to possible file locks and corruption issues?  This is for a home  office setup, so the number of users will be limited to those that live in the house. 

By trade, I'm a Windows Server admin, so Linux is throwing a curve ball my direction.  A person in another thread pointed me to an article that helped me to understand some differences between Window Server networks and Linux Server networks, but I still have some learning to do.  My goal for right now is to setup a server that will allow my family and I to access shares on the server.  At a later date, I will re-investigate using a Linux server for central user authentication.  I think because I have DNS issues, LDAP is not working correctly.  I can attempt to login on another machine using a user created in LDAP, but won't authenticate.  Again, that's another issue, so I'm not to worried about it.  

Any info / help on Samba and the best way to share a network drive would be appreciated.  THanks.

---

### Post by taladan on 2008-10-12
As a windows server admin, there's one tool out there that will help you administer your linux server that you will doubtless find very handy.  It's a tool that I myself use to administer several linux boxes as it gives me the ability to do it over the intranet via a web interface from any workstation with a web browser.

At the terminal type:

```
sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

```

When that is complete, type:

```

wget http://prdownloads.sourceforge.net/webadmin/webmin_1.430_all.deb

```

Then type:

```
sudo dpkg -i webmin_1.430_all.deb
```

If you get any complaints from the server about missing dependencies, type:

```
sudo apt-get install -f
```

You can then log in to your webmin by pointing your browser at:

```
https://localhost:10000
```

or

```
https://<hostname>:10000
```
(from another machine on your network)

Use your usual login/pw account that has sudo access to login to webmin.

This will allow you to have a web-based interface to administer any services on the box (including samba).  Samba configuration should be listed under Servers in the left-hand menu as 'Samba Windows File Sharing' (or something similar).  You'll note in the samba server configuration that you can create new shares and such - this is where you'll add your shares in.  Once you do that there will be a security and access control option for each share that you have.  This is the place where you can determine which users may access the shares.  If you want anyone on your network to be able to access the shares then you should be able to allow guest access and this should keep you from having to duplicating your user structure.  If you want more fine grained control then you'll likely have to set up samba users within the server itself (there's options for that as well) to restrict access to only a few people within your network.

I hope this helps somewhat, and keep in mind, this is only one option available to you - there are other graphical web-based samba tools available, as well as the capability to configure anything through the /etc/samba/smb.conf file by putting in the correct values.  Webmin is a useful tool though if you're used to having some sort of click and work interface for systems administration and I use it fairly regularly as a central clearing house for server configuration on several machines.

Tal

---

