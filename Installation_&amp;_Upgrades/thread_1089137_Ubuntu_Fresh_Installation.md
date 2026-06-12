---
title: "Ubuntu Fresh Installation"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by Colinho on 2009-03-06
Well I stuffed up an upgrade and now I need to do a fresh installation.

When I first installed ubuntu a few months ago I put separate partitions for / and /home, in case I got my self into a situation like the one I am i now. But before I reinstall 8.04 (the only disc I have) I have some questions.

First of all, should I format my / partition when reinstalling it?

How much will I actually lose/retain? I know that my docs, videos etc will still be there, but what about my applications, settings, presets be removed or will I still have them?

I'm sorry I don't know exactly what is and what isn't in the root folder.

I can give some more details later if you need them.

Thanks!

---

### Post by taurus on 2009-03-06
All your files and personal settings will be in your $HOME which is on /home so make sure when you reinstall, mount the other partition to / filesystem and format it.  But mount the one with /home to /home and _do not_ format it or all your stuff will be gone.  Then, create the same username as before so you would use the same $HOME when you first log back in again.

---

### Post by Colinho on 2009-03-06
Hi, thanks for the quick reply.

So if I reinstall onto the / partition (formatting it), create the same usernames, and then when my internet rolls over I upgrade to 8.10, it should be pretty much exactly how it was a few days ago before the failed upgrade? It will have the same applications, drivers and settings etc?

Thanks again!

---

### Post by taurus on 2009-03-06
You probably have to reinstall the drivers for your graphic card or maybe even wireless if you use one.  Regarding to settings, what settings are you refered to?

---

### Post by Colinho on 2009-03-06
Firefox addons, about:config edits, CCSM changes and stuff like that. Not the most important stuff but I'd still like to keep as much as I possibly can.

---

### Post by taurus on 2009-03-06
Unless those plugins are in ~/.mozilla/plugins, you have to reinstall them.

This would do it.

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Colinho on 2009-03-07
Ok thanks, and finally, do I need to do anything in preparation? Do you recommend me making anymore partitions? (I heard somewhere that a /usr partition was good to make)

Thanks for your help! Even though there aren't as many users, help for Ubuntu is so much easier than trying to get help for something on Windows. These forums are really great, thanks again!

---

### Post by Colinho on 2009-03-08
Well I reinstalled it earlier today, and so far it has been pretty good. The installation stayed on "82% - Configuring apt: Scanning Mirror" for a very very long time but eventually it all got installed. I created my user exactly the same and was nicely surprised when I saw my wallpaper, theme etc were all the same. The programs I had installed are no longer there, so I guess I will have to download them again when my internet rolls over (I've been capped to dialup speed). I think the application data still remains though, firefox is exactly how it was (if not better ^^) and after reinstalling Virtual box I got both my windows xp boxes back.

The only problem that I really have (reinstalling programs isn't really much trouble) is creating the other user that I had before. In the installation wizard it let me create my user, but in System -> Administration -> Users and Groups, when I try to create a user with the same info the other user I had it says "Home directory already exists"

Is there a workaround to this?

Btw this question is open to everyone, the more the merrier ^^

Cheers

EDIT: For anyone that finds this thread looking for help about an Ubuntu Fresh Installation, check out this article:
[http://www.ubuntugeek.com/howto-reinstall-all-of-currently-installed-packages-in-fresh-ubuntu-install.html](http://www.ubuntugeek.com/howto-reinstall-all-of-currently-installed-packages-in-fresh-ubuntu-install.html)
It tells you how to reinstall all of the packages you had before you reinstalled ubuntu.

---

