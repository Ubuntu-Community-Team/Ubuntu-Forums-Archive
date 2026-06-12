---
title: "firefox-3.5 segmentation fault (core dumped)"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by fuhrysteve on 2009-04-22
I have been unable to start firefox-3.5 (under jaunty, obviously) since 3.1 when I ambitiously tried to install colorzilla (some obscure extension).

I have tried quite a number of things on multiple occasions, including purging the package w/ apt, and deleting every file on the filesystem that looked even slightly related to it manually (using find).

Here is a bug report I filed with no response from devs [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/353881](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/353881)
this report contains a number of debugging things I preformed without success.

Hopefully I'm not the only one with this problem -- I cannot run firefox-3.5 under any circumstance at this point. Anyone have any suggestions?

```
steve@dickens:~$ uname -a
Linux dickens 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
```

---

### Post by FredB on 2009-04-23
It is not officialy released as a beta version. 3.5 beta 4 will be released before end of this month. I think Firefox 3.5 will be released in june, or even in september. Not before.

---

### Post by manuelb on 2009-04-23
I have the same problem on my desktop: if i purge the profile in ~/.mozilla/firefox-3.5 it will recreate it and then a segfault will follow anyway: instead it's running fine on my notebook.

---

### Post by tardifj on 2009-04-24
Yes same problem here with firefox 3.5 beta and the nightly builds. I also tried thunderbird 3.0 beta experience the same issue. For thunderbird 3, I used the ppa at:

[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)

with not luck.

---

### Post by manuelb on 2009-04-27
really no one else with this problem?

---

### Post by lvleph on 2009-04-27
I am having similar problem on Intrepid. However, mine goes even further. I have seg faults for the following.
firefox-3.5
firefox-3.6
songbird (current version in repository)

---

### Post by manuelb on 2009-04-29
Sorry to bump the thread again but i'm still scratching my head with it: the problem has been confirmed ([https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/353881]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/353881")) by others, hope to find away around it.

---

### Post by manuelb on 2009-04-29
I got it running, the Launchpad is offline at the moment so i'll post here how to do it, hope it can help you as well.
It seems xulrunner-1.9.1b5pre is not being used (at least in my case) thus causing some problems (look at your kernel.log) in the ld-2.9.so loader.
I'm simply forcing xulrunner-1.9.1b5pre to load firefox by specifying full paths, so i just created a new Launcher on the desktop with this command:

```

/usr/lib/xulrunner-1.9.1b5pre/run-mozilla.sh /usr/lib/firefox-3.5b5pre/firefox-3.5

```

It work nicely, but i'm going to figure out how to handle updates since i think the command will need to be updated whenever xulrunner version increments, in the meantime i can test it out its new features :)

---

### Post by lvleph on 2009-04-29
This did not allow me to run firefox-3.6 or firefox-3.5

```
uname -a
Linux erichs 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64 GNU/Linux

```

---

### Post by Laibcoms on 2009-05-01
> **manuelb said:**
> ```

/usr/lib/xulrunner-1.9.1b5pre/run-mozilla.sh /usr/lib/firefox-3.5b5pre/firefox-3.5

```It work nicely, but i'm going to figure out how to handle updates since i think the command will need to be updated whenever xulrunner version increments, in the meantime i can test it out its new features :)

It works.  Thanks.

---

### Post by manuelb on 2009-05-05
Just to add some more information, i found out that the version of **xulrunner** being installed during Jaunty alpha days was **1.8.1** and that obviously lead to segaulting apps if linked against more recent version of it, such as 1.9.
So, uninstalling 1.8.1 and installing 1.9 should let Firefox 3.5b4+ as well as other apps such as Miro 2.0.4+ work the way they are supposed to without manually calling the xulrunner1.9.1beta binary.
Please help spread this information since i read other threads where xulrunner-based apps keeps crashing, that could resolve these issues as well.

---

### Post by fuhrysteve on 2009-05-05
> **manuelb said:**
> Just to add some more information, i found out that the version of **xulrunner** being installed during Jaunty alpha days was **1.8.1** and that obviously lead to segaulting apps if linked against more recent version of it, such as 1.9.
So, uninstalling 1.8.1 and installing 1.9 should let Firefox 3.5b4+ as well as other apps such as Miro 2.0.4+ work the way they are supposed to without manually calling the xulrunner1.9.1beta binary.
Please help spread this information since i read other threads where xulrunner-based apps keeps crashing, that could resolve these issues as well.

this did it for me. Thanks!

```
sudo apt-get purge xulrunner libxul-dev
```

---

### Post by Jeffrey04 on 2009-05-14
I am having the same problem, and somehow only root user is able to launch firefox-3.5. If I attempt to launch firefox not as a root user, then I get segfault....?!

---

### Post by configt on 2010-07-27
(sorry this is not a precise document, but I hope it is useful to someone using global-menu applet)

I skipped FF 3.5 and went straight to 3.6.7 from 3.0 on amd64 Jaunty.  Right after the upgrade I could no longer launch firefox or thunderbird without an immediate segfault.  I had tried completely removing firefox, deleting the ~/.mozilla directory, adding new profiles, reinstalling, rebooting, such and so fourth as previously recommended here, but to no avail.

One important thing to note was that other user accounts on the same PC were able to use firefox and thunderbird just fine.  My primary account is using a global-menu applet.  Once I added the global-menu applet to another user account where firefox was working, it would then segfault in the exact same manner as on my primary user account.  Disabling the window menu option in the preferences of the gnome-global-menu applet resolved the issue with the mozilla apps, but of course, global-menu was no longer useful as it didn't show the menu options for the app window in focus.  

Long story short, I completely removed the global-menu applet, and installed the latest version of it.  Now it all works just fine.  That was somewhat painful.  SO, if you are using an older version of the gnome-global-menu applet (commonly installed in addition to mac4lin themes), and can't launch firefox after the recent branding upgrade that enables binary upgrades to the latest firefox for ubuntu without an immediate segfault, upgrade your gnome-global-menu applet.

---

