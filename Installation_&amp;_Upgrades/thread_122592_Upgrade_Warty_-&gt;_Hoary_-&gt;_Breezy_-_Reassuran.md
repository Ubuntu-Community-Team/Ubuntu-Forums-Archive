---
title: "Upgrade Warty -&gt; Hoary -&gt; Breezy - Reassurance required"
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by sjtravers on 2006-01-28
For a long time now, I've been running a very old PC with Redhat 5 as a server in a small workgroup of mixed Windows/Linux desktops to provide web, mysql, imap, samba services. I pretty much haven't used Linux extensively the past couple of years, other than the occasional e2fsck when I got a power failure, and I'm out of practice.

Last week I came across some free hardware (PC being thrown out) and, armed with a copy of Warty I'd downloaded some time ago, decided to see if I could replace my existing server with something more modern.

So I did, and everything's working perfectly, BUT Warty seems to have been passed over in favor of the more recent Hoary Hedgehog (God I love these names!) and now Breezy Badger. 

I would REALLY like to upgrade to the latest Ubuntu, but of course I've spent about 24 hours re-learning everything I knew, learning all the new stuff, and learning how debian/ubuntu does it as opposed to redhat (must remember - apt-get not rpm), and getting everything working beautifully, and I don't want to have to start from scratch (clean install) if I can avoid it.

Now as I understand it, I should be able to upgrade from warty to hoary and then to breezy by simply:

1. Update /etc/apt/sources.list, replacing "warty" with "hoary"
2. apt-get update
3. apt-get dist-upgrade
4. reboot
5. Update /etc/apt/sources.list, replacing "hoary" with "breezy"
6. apt-get update
7. apt-get dist-upgrade
8. reboot

And I should be on a nice, spanky, new Breezy Badger (did I mention I LOVE these names) and everything should work properly.

Can someone please tell me:

Is that right? 
Did I miss anything?
Are there any "gotchas"?
Will I have to reconfigure anything/everything?

Oh, and can I suggest "Woolly Wombat" for the post-Dapper Drake release, being an Aussie and all.

Cheers,
Stu

---

### Post by polt on 2006-01-28
On upgrade to Breezy, I did have to reconfigure some stuff.  It was a little buggy, but not too bad and the problems got fixed fairly rapidly.  However, it asks if you want to keep your old configuration files.  You do not want to keep your old configuration files.  They will mostly not work anymore.  I messed up my whole login screen by keeping those.  

Breezy is awesome.  You do want to upgrade.  If there are any problems it should be no sweat to find the answer here!  Just make sure your data is backed up, just in case.

---

### Post by sjtravers on 2006-01-28
Thanks for that, sounds quite encouraging. I think I just have trouble dealing with the possibility that anything that sounds so simple can be so simple and actually work.

Not to worry re the data, it's all still on the old Redhat box.

Anything else I need to worry about?

Cheers,
Stu

---

### Post by sjtravers on 2006-01-28
OK upgrade is happening now from Warty to Hoary. Packages have downloaded and things are installing (and I'm keeping whatever config files it asks me about as per previous advice).

Right now, I can't access the web server or the imap server, both saying connection refused. SSHD and Samba both seem to be going ok. Hopefully all will come good later.

I REALLY hope I'm not going to have to connect a monitor for this, cos that means scrabbling around under the desk (did I mention I'm running in console mode?). With any luck SSHd will behave itself all the way through.

Maybe.

Everybody keep fingers crossed, I'll post my learnings later.

Cheers,
Stu

---

### Post by sjtravers on 2006-01-28
All seems well. Rebooting.

---

### Post by sjtravers on 2006-01-28
OK, post reboot, and it seems all is OK.

I've got imap, samba, apache2, mysql, php, ssh and everything else I need.

I'm not sure how to check to see if I actually have "Hoary Hedgehog" or not, but so far I am LOVING this.

Time to see if  I can repeat the process with Breezy.

---

### Post by sjtravers on 2006-01-28
This is extremely strange. I updated my sources.list (change hoary to breezy), ran apt-get update, then apt-get dist-upgrade.

All seemed to be going well, but apt was telling me there were 2 hours worth of downloads at 11.30pm so I decided to leave it overnight.

When I came back, there was a prompt asking me if I wanted to restart a bunch of services, which I did, and all seemed ok but looking through the log apt was claiming that hardly anything had actually been upgraded as the files were missing.

A re-run of apt-get dist-upgrade tells me it requires a further 500MB of files to perform the upgrade.

This suggests to me that either the files didn't actually download in the first place (given the time it took, this is unlikely) or that at some point in the night my system has "cleaned up" (eg. 'apt-get clean' or similar) and so the files have gone bye-bye by the time apt-get tried to install them.

I suspect there's a cron job somewhere, as I noticed a file in /etc/cron.daily called "apt" which has the potential to clean out downloaded files, but I can't confirm that it ran and did what I think it did.

Does anyone have any information on this?

Also, I have encountered a locale error starting perl, but I've read about that elsewhere and it should be easy enough to fix, yes?

Cheers,
Stu

---

### Post by sjtravers on 2006-01-28
It doesn't look like anyone's viewing this thread, but here's the final outcome:

After upgrading from Warty to Hoary to Breezy using the commands shown above, everything is working properly as far as I can tell.

There were a couple of things I encountered along the way, perhaps this information will help someone. Perhaps not.

1. Errors installing a few packages (notably of the gstreamer variety) showed an error along the lines of:

Illegal instruction execution in liboiltest.c (line 247)

According to Bugzilla, however, this is a warning, and can be safely ignored. It certainly doesn't seem to have broken anything.

2. Postfix wouldn't start.

I had read a message somewhere saying that I may have problems with postfix and that i should run "apt-get install --reinstall postfix", which I did but the problem was still there.

I had a look in /var/log/mail.err and found this:

postfix/master[7171]: fatal: /etc/postfix/master.cf: line 84: bad hostname or network address: ::1:smtp

A quick look in /etc/postfix/master.cf and found:

127.0.0.1:smtp inet n   -       -       -       -       smtpd
::1:smtp       inet n   -       -       -       -       smtpd

Commented out the second line, ran /etc/init.d/postfix start, and Robert was my mother's brother (Bob's my uncle in case you're wondering).

I don't know where this came from, but it's gone now and all is well.

Cheers,
Stu

---

### Post by christhemonkey on 2006-01-30
This also worked fine for me!
Id say to all those still on hoary, that this is well worth doing upgrding to breezy is the best thing i did today!

---

