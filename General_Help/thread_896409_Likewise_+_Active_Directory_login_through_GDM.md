---
title: "Likewise + Active Directory login through GDM"
date: 2008-08-21
forum: General Help
---

### Post by psylo on 2008-08-21
Hi all,

I'm tearing my hair out on this one now as I've spent a few days trying to get it to work and it is so close but really don't know where to go next. 

Here's what I have: 

My laptop running Ubuntu 8.04

On that I have installed the Likewise Open software to manage the joining to a Windows Active Directory we have set up at work.

I can join and leave the Active Directory absolutely fine now when I am logged in as my personal sudo capable user - ie the default user of my laptop who is not a real member of the DOMAIN.

Assuming I've joined the domain using Likewise GUI or CLI I can then SSH back into my local machine using a user from the domain. That user will then be dropped into a new home directory residing in /home/EXAMPLE.LOCAL/username

This all works fine and I'm happy with this part.

However if I switch user and try and login through the main login prompt I get the error "Cannot set your user group. You will not be able to login. Contact your system administrator". Obviously I can't get beyond that point of login

If the group can't be set then why can I SSH into the box with the same credentials?

Indeed after SSHing into the box I can see all of the groups to which I belong however most importantly these are all DOMAIN groups and not groups that exist on the physical machine.

I tried creating a group on the local machine that mapped to one of the domain groups however that didn't do anything at all. IE there was no change to the login effect.

I'm sure I'm really close and I'm hoping someone has had a similar problem as I know that if I can get this sorted we can possibly start to roll out some Ubuntu machines into the office but having them Authenticate to AD is an absolute requirement.

Any help on this would be most welcome.

Cheers
AndrewF

---

### Post by psylo on 2008-08-21
Bump?

---

### Post by wirelessben on 2008-08-22
I seem to have the same problem. Likewise let me join the AD domain, but I can't login using "domain\username" from the login GUI. 

The GUI did not ask to set my home directory. Maybe that's it.

---

### Post by psylo on 2008-09-01
Yeah I tried adding a user directory etc and that didn't seem to resolve it. Also added the user to a group and that didn't resolve it either.

Definitely need to get this sorted because I can't roll out anything to users if they can't login to the domain properly... pretty simple as that but I'm not sure where to go from here.

We're at a critical junction here as we need to make a decision over the next few months whether we migrate users to Linux or to Vista from XP so it's a big deal and AD support is a central part of that.

---

### Post by darkpaw on 2008-09-11
I'm having the same problem.  I can login via ssh and if I spawn a "login" prompt from a local user via sudo (ie: sudo login).  But if I logout and try to login as the domain user with GDM, it fails with:

Sep 11 10:16:04 ubuntu-test4 gdm[5059]: pam_winbind(gdm:auth): getting password (0x00000000)
Sep 11 10:16:07 ubuntu-test4 gdm[5059]: pam_winbind(gdm:auth): user 'XXXXX' granted access
Sep 11 10:16:07 ubuntu-test4 gdm[5059]: pam_unix(gdm:account): could not identify user (from getpwnam(XXXXX))

where XXXXX is the username.  Can ssh and login with CLI just fine.  Just not with a window manager.

Ideas?

---

### Post by silverglade00 on 2008-09-11
Are you using the Likewise from the repos or from the website? I had many problems with the repo one, but the website one dropped right in and worked like a charm.

[www.likewisesoftware.com](www.likewisesoftware.com)

---

### Post by darkpaw on 2008-09-11
I'm actually not using Likewise, sorry.  I didn't notice that part of the message until now. 

I've setup samba and krb5 for active directory authentication via stringing together from several web pages on doing so.  I found this page in a search for my similar problem (AD login via ssh but not GDM).

---

### Post by gkaragoulis on 2008-09-16
So I may have useful information for you guys.  I was having the same problems with my PAM account settings: "could not identify user (from getpwname(XXX))", and it wasn't allowing anyone to login.

Those problems appeared precisely after I removed 'nscd' from my computer.  As soon as I re-installed it everything was right as rain.  Maybe give that a try?

---

### Post by gkaragoulis on 2008-09-16
I discovered some more information after reading the winbindd man page.  It says that winbind first checks getpwnam() to see if the local computer can resolve the user/group id, which means that you must have some sort of caching going on otherwise getpwnam() will fail.  NSCD serves this caching purpose.

However, I have found that nscd also causes problems.  For instance if I add a user to a domain group, then that membership does not refresh no matter how many times I restart winbind or nscd.  To fix that, edit /etc/nscd.conf and change "persistent = no".  That makes it so cached domain memberships do refresh when you restart nscd.

I'm still looking into how this works, but that's what I got so far.  Hopefully it helps others in similar situations.

---

### Post by likeWiseGuy on 2008-10-02
> **psylo said:**
> Yeah I tried adding a user directory etc and that didn't seem to resolve it. Also added the user to a group and that didn't resolve it either.

Definitely need to get this sorted because I can't roll out anything to users if they can't login to the domain properly... pretty simple as that but I'm not sure where to go from here.

We're at a critical junction here as we need to make a decision over the next few months whether we migrate users to Linux or to Vista from XP so it's a big deal and AD support is a central part of that.

Hi psylo,

I hope I'm not too late to assist in your migration to Linux and Active Directory integration.

It seems that others have provided some useful tips to help you out. If the issue persists, please respond back and I'll be glad to have a look with you on what is going on. 

Good luck to you and your company. :-)

---

### Post by jbird80 on 2010-01-21
Hello, just in case this is still an issue I was able to get the my domain\username in the list by adding it to /etc/passwd file manually. I have no idea if this will cause other issues but it hasn't on my system so far.

domain_name\usr:x:1001:1001:Domain User,,,:PATH TO HOME DIR:/bin/bash

this only seems to put the name in the list so i can click on it and login with out having to type in my full credentials. I was hoping it would solve the issue with the domain user being put into the sh shell but it did not.

Hope this helps someone.

---

### Post by javier.rotelli on 2010-03-30
i have the same problem, but i dont want to put the user in passwd file.
i hvae installed nscd, but the problem remains...

any idea?

thanks

---

### Post by KwiRa on 2012-07-02
Some problem with powerbroker but easy fix from document:

modify /etc/pam.d/common-session

add:
session optional pam_gnome_keyring.so auto_start_if=gdm

run as root:
/opt/pbis/bin/domainjoin-cli configure --enable pam

restart gdm

---

### Post by oldos2er on 2012-07-02
Closed; please don't bump old threads.

---

