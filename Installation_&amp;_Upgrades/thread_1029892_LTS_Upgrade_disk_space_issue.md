---
title: "LTS Upgrade disk space issue"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by adamcrosby on 2009-01-03
I'm upgrading from Dapper to Hardy, in a VM with an 883M / partition.  
When I run 'do-release-upgrade', I get this:

"Not enough free disk space 

The upgrade aborts now. The upgrade needs a total of 367M free space 
on disk '/'. Please free at least an additional 6916k of disk space 
on '/'. Empty your trash and remove temporary packages of former 
installations using 'sudo apt-get clean'. "

But I have a decent amount more than 367M free:
root@ns2:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             883M  422M  414M  51% /

(/ is my only disk partition).

I've tried removing and removing extraneous crap, big packages, cleaning out logfiles, etc.
How much space do I *really* need for the upgrade script to run?  It's obviously not 367M...

Thanks!

---

### Post by taurus on 2009-01-03
> **adamcrosby said:**
> I'm upgrading from Dapper to Hardy, in a VM with an 883M / partition.  
When I run 'do-release-upgrade', I get this:

"Not enough free disk space 

The upgrade aborts now. The upgrade needs a total of 367M free space 
on disk '/'. [B]Please free at least an additional [COLOR="Blue"]6916k[/COLOR] of disk space 
on '/'.[/B] Empty your trash and remove temporary packages of former 
installations using 'sudo apt-get clean'. "

But I have a decent amount more than 367M free:
root@ns2:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             883M  422M  414M  51% /

(/ is my only disk partition).

I've tried removing and removing extraneous crap, big packages, cleaning out logfiles, etc.
How much space do I *really* need for the upgrade script to run?  It's obviously not 367M...

Thanks!

It already told you.

---

### Post by adamcrosby on 2009-01-03
That number changes every time it runs, and the preceding message says it only needs 367M of free space.  I have over 400M of free space when I began the update, but it then fails.
Is the preceding message incorrect, and the update actually needs 420.916MB of free space?

---

### Post by Claus7 on 2009-03-19
Hello,

still exists a dapper user? Remarkable! Have you found out how much disk space really is needed for the upgrade. My guess is that this should be 4gb, yet I do not know for sure. I had more than 1.2 gb freed, yet it still complained. If someone has any knowledge on the subject I'll be glad to hear.

Regards!

---

### Post by Claus7 on 2009-03-22
Hello,

with 4,1GB free the updrade didn't complain about the hard disk space availability. It gave me the opportunity to decide whether I will actually want to do the upgrade or not and which packages will be upgraded.

Regards!

---

