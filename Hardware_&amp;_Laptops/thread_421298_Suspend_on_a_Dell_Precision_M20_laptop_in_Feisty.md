---
title: "Suspend on a Dell Precision M20 laptop in Feisty"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by LegoAddict on 2007-04-24
So I love running Ubuntu on my Dell Precision M20 laptop.  I installed Feisty when it was in the beta, and it's great now it's out.  The only beef I have with it is the suspend.  I like to just be able to close the lid on my laptop when I go away, and when I open it, see my work again.


Well I can't, and it's a pain in the behind.  One of the things (other than some games) that keeps me logging in to Windows XP, which I have dual booted.


I've heard from different sources that this has been fixed, but I just installed the recent update package (4/24/07) and I saw there was a kernel update.  So I shut my computer's lid to see if it worked... no.


So is there a fix that I can get officially or unofficially to get this thing to work?  I'm on Ubuntu 7.04 up to date system Dell Precision M20 laptop.


I found this:

[http://boulderjams.wordpress.com/2007/02/20/ubuntu-dell-suspend-fix/](http://boulderjams.wordpress.com/2007/02/20/ubuntu-dell-suspend-fix/)

but I don't really want to mess around with my system.

I'm very proficient in Windows, and relatively competent in Ubuntu.

---

### Post by strabes on 2007-04-24
[http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200](http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200)

> Finally, the perhaps most important change goes into /etc/default/acpi-support. Change the line POST_VIDEO=true to read POST_VIDEO=. This was the point when it started working on my system.

```
gksudo gedit /etc/default/acpi-support
```

---

### Post by LegoAddict on 2007-04-25
I'm quite new at Linux, and so I'm having a few problems with getting the stuff to work.

First, how do I log on as administrator?  My account has all the privledges I can give it and it still can't edit in any way that folder.

Also, what does the terminal code do?  I'm familiar with some of the basics of the terminal, but I'd like to know what I'm doing.

But thanks, it will be great if I can get this to standby.

---

### Post by strabes on 2007-04-25
You don't need to log in as administrator. You can run commands as the root user using *sudo*. For more info check these pages:

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

The terminal command I pasted will (after you enter your password) open up the important file in a GUI text editor. Simply change the line I mentioned, save the file (Ctrl + S) and close the file. I'm not sure if you have to reboot or not for the setting to take effect. Just try to suspend without rebooting. If it doesn't work, reboot and then try again.

---

### Post by LegoAddict on 2007-04-26
YES!

Thanks a tonne.  It works fine.


Finally I don't have to turn off my computer all the time!

---

### Post by flyboy284 on 2007-04-27
I am having the same problem with suspend, but editing the POST_VIDEO= line didn't helpin my case. It still locks up on suspend, is there any thing else I can try?

---

