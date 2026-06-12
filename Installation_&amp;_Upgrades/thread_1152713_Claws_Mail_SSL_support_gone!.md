---
title: "Claws Mail SSL support gone!"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by msbarker on 2009-05-08
I upgraded to jaunty from hardy today.  The upgrade went well with no real problems except I lost ssl support in claws mail.  Initially, claws mail worked as before, but after upgrading the plugins from the jaunty repositories I have no more ssl to my imap server.  I have tried reverting to previous claws versions and reinstallations with no luck.  I also deleted my imap server certificates, and claws has not picked up new certs yet.  It will connect just fine without ssl.  Any ideas out there?

---

### Post by ahbart on 2009-05-08
I did not see this problem on my system, but I'm using the Claws repository directly. These are newer versions. [link](https://launchpad.net/~claws-mail/+archive/ppa)

---

### Post by msbarker on 2009-05-08
Thanks ahbart for the suggestion.  It was actually after using the binaries from the Claws repository directly that I lost ssl.  After installing jaunty I lost notifications, and redirected my sources to the launchpad claws jaunty sources.  After upgrading everything to 3.7.1 that's when I lost ssl.  Even if I completely remove claws and reinstall from the Ubuntu repository I have no ssl for claws.  Pretty odd. Nothing that I can in my firewall is blocking it.

---

### Post by ahbart on 2009-05-08
Is it only a claws problem? Did you try to completely remove claws from synaptic? and install it after that?

---

### Post by msbarker on 2009-05-08
Yes, it only seems to be a claws problem.  Evolution appears to access the server (fastmail) with ssl just fine.  I just completely removed claws from the system, backups and deleted my profile, and started with a compeltely clean claws install and profile.  No ssl.  I'll try a new account to my university's servers.  It seems that either ssl is broken with my particular installs of claws, or something is blocking claws from using ssl.

---

### Post by msbarker on 2009-05-08
Just tried setting up a ssl connection to my university's servers.  Same problem as connecting to my other servers.  Note that non-ssl imap connections work fine.  Any ideas?  For now, I am just using unauthenticated connections or ultimately switching to evolution.  Any other ideas?

---

### Post by albinootje on 2009-05-08
> **msbarker said:**
> After upgrading everything to 3.7.1 that's when I lost ssl.  Even if I completely remove claws and reinstall from the Ubuntu repository I have no ssl for claws. 

It could be a configuration/settings upgrade issue. 
Can you create a new user account (or use the guest account) and test with a completely fresh usage of claws ?

---

### Post by ahbart on 2009-05-08
You could try to create an new account in claws with a different name, but the same pop/imap settings.

edit: I just saw your reaction Albinootje. Little to late then.

---

### Post by msbarker on 2009-05-08
Just tried making a completely new ubuntu profile, reinstall claws, and still no ssl.  Evolution does ssl and I may move over this weekend.  I have been a claws user for over 2 years and this is the only time I have been frustrated by it.  Thanks for all the help so far and any additional advice is welcomed.

---

### Post by albinootje on 2009-05-08
> **msbarker said:**
> Just tried making a completely new ubuntu profile, reinstall claws, and still no ssl.  Evolution does ssl and I may move over this weekend.  I have been a claws user for over 2 years and this is the only time I have been frustrated by it.  

I've been using Sylpheed since many years, and switched to Claws a few years ago, and I'm a bit sad to read your response here.
I think you should try to clearify and fix this problem with us together, it is e.g. possible that the PPA Claws was compiled without SSL support by mistake.

---

### Post by msbarker on 2009-05-08
Thanks albinootje!  I would prefer to keep working with claws as well - it is a very productive e-mail client.  I'll contact the people at PPA and see if this problem has been reported before.  If anybody has any other ideas, I am open to them.

---

### Post by albinootje on 2009-05-08
> **msbarker said:**
> I would prefer to keep working with claws as well - it is a very productive e-mail client.  I'll contact the people at PPA and see if this problem has been reported before. 

Thanks :) And I forgot that I have Ubuntu Jaunty on my netbook, I'll do some testing now.

---

### Post by albinootje on 2009-05-08
I just tested it with Claws from Jaunty with a fresh start (No old configuration/preferences used), and that worked without problems.
Then I upgraded Claws to the version from the mentioned PPA (3.7.1), and that also worked without problems.

I'm connecting via SSL to an imap server running on port 993, which 
does not even support plain imap without SSL on port 143 :)

Can you describe what exactly goes wrong, or what the error messages are ?

---

### Post by msbarker on 2009-05-08
I get a "ssl handshake failed" error with claws.  I am connecting with ssl to port 993 with no luck.  Immediately before the claws upgrade it worked just fine, and had been working for over a year.

---

### Post by albinootje on 2009-05-08
> **msbarker said:**
> I get a "ssl handshake failed" error with claws.  I am connecting with ssl to port 993 with no luck.  Immediately before the claws upgrade it worked just fine, and had been working for over a year.

Here's someone with a similar problem, but on Hardy, and longer ago : [http://www.nabble.com/claws-mail-3.6-from-launchpad-and-SSL-td19824279.html](http://www.nabble.com/claws-mail-3.6-from-launchpad-and-SSL-td19824279.html)

I wonder why I don't have a problem with 3.7.1-PPA for reading email via imap-ssl on Jaunty.

By the way, instead of switching to Evolution you could go back to Claws 3.6.x, or does 3.7.1 feature changes that you really need ?

---

### Post by msbarker on 2009-05-08
Thanks for the link, I'll check it out.  I would go back to Claws 3.6.x or even 3.5.x but they have the same problem now.  SSL is completely gone from Claws, even older versions (as mentioned in earlier posts).  Thanks for the help.

---

### Post by albinootje on 2009-05-08
> **msbarker said:**
> Thanks for the link, I'll check it out.  I would go back to Claws 3.6.x or even 3.5.x but they have the same problem now.  SSL is completely gone from Claws, even older versions (as mentioned in earlier posts).

Did you try the following :
1) shut down Claws
2) type this in a terminal :
```

mv .claws-mail .claws-mail-OLD

```
3) start Claws, and test again.

After this still doesn't work, put the settings back like they were :
```

mv .claws-mail .claws-mail-test
mv .claws-mail-OLD .claws-mail

```

---

### Post by msbarker on 2009-05-08
Already tried a completely fresh .claws-mail with new installs.  I wonder if there is some problem with gnutls or openssl?

---

### Post by msbarker on 2009-05-08
I solved my problem!  Instead of using the PPA for Jaunty, I uninstalled and used the claws mail 3.7.1 ppa for Hardy.  I noticed that there was no libetpan for jaunty, but I don't know if this is the problem.  Anyway, reverting to the version compiled for hardy works great on my jaunty system.

---

### Post by albinootje on 2009-05-08
> **msbarker said:**
> I solved my problem!  Instead of using the PPA for Jaunty, I uninstalled and used the claws mail 3.7.1 ppa for Hardy.  I noticed that there was no libetpan for jaunty, but I don't know if this is the problem.

I noticed that too.
> 
Anyway, reverting to the version compiled for hardy works great on my jaunty system.

Cool, congrats :)

---

