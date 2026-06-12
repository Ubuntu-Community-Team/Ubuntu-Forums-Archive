---
title: "Cannot login to MSN account using Pidgin 2.4.1"
date: 2008-07-22
forum: General Help
---

### Post by D.Sync on 2008-07-22
Previously, which is about 4 months ago I can login to my MSN account successfully using Pidget. However, now I couldn't connect with it anymore.

Any way to rectify such problem?

---

### Post by KIAaze on 2008-07-22
Did you change your MSN password?
If it's longer than 16 characters, just enter the first 16 characters and it should work.

cf [http://developer.pidgin.im/ticket/4699](http://developer.pidgin.im/ticket/4699)

---

### Post by D.Sync on 2008-07-23
Nope my password is <10. Still cannot login.

---

### Post by KIAaze on 2008-07-23
I don't think I'll be able to help you much more then.

But are you sure your MSN login/pass still work?
Can you login with aMSN or Kopete? (Or try logging in directly on the MSN Live site)

What error messages do you get?
Also, maybe you should run pidgin from the command-line to get more error messages if any.

---

### Post by y-lee on 2008-07-23
That happened to me too and in my case i was getting a "Unable to retrieve MSN Address Book" error message. The problem was I had compiled Pidgin from source with MSNP14 enabled. In theory that enabled me to get offline MSN messages, when it worked that is. But now it seems MSN has blocked the ApplicationId that is used by msnp14. I uninstalled Pidgin and then updated to Pidgin 2.4.3 and did not enable MSNP14 and it connected with no problem.

Don't know if that is your problem or if the Pidgin in the repos has MSN14 enabled or not but I would suggest trying to uninstall Pidgin and upgrading to the newer version. (don't worry about MSNP14 as to enable that you have got to modify the configuration file in the source package. Default installation does not enable it)

---

### Post by Luke771 on 2009-01-12
Not working on 2.5.3 either, looks like MS blocked Pidgin, probably because they found out that Windows users are chosing to run Pidgin instead of the heavy, buggy, messy, ad-infested MSN 'official' client.
That's just a wild guess of course, but it makes sense. Hope MS shoots itself in the foot with this move. Let's see why.

The obvious response to MS blocking Pidgin would be to try some different IM apps, but do we really want to?
Actually, this is a good excuse to quit MSN once and for all.
Skype does the same job and it's becoming more popular by the day. I'll e-mail my Skype name to my MSN contacts, and tell them that they can find me there.

---

### Post by Sunspore on 2009-01-12
I have the same problem as well, does this means that we cannot use pidgin temporary? Funny thing is that it still work on ebuddy.

---

### Post by Sunspore on 2009-01-12
just open terminal and type:

sudo apt-get install msn-pecan

Then change the account type in Pidgin to 'WLM' from 'MSN


I just tried, work for me.

---

### Post by leorolla on 2009-12-10
It just stopped working for me also... 2.4.1

I can't upgrade or install anything, I'm no super-user here.

---

### Post by Soul-Sing on 2009-12-10
I installed the newest pidgin from the website adding the source and [COLOR="Red"]KEY![/COLOR] to my software sources and pidgin does work again....
(issue on ubuntu 8.04)

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
```

```
echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
```

```
sudo apt-get update
```

---

### Post by scouser73 on 2009-12-10
It works under Pidgin version 2.6.3

---

### Post by Soul-Sing on 2009-12-13
> **scouser73 said:**
> It works under Pidgin version 2.6.3

yes it does!

---

