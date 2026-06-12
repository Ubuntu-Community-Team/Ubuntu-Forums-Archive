---
title: "I accidently deleted the wifi strength reader."
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by litechocolate on 2009-07-18
Can someone tell me how to get it back :P Thanks!

---

### Post by philcamlin on 2009-07-18
sudo apt-get install *name of wifi stregnth reader*

:)

edit when i was first here i had alot of questions like this 

your not an idiot :)

---

### Post by master_kernel on 2009-07-18
Haha you're not an idiot (even though that's what I voted :)).

But if you use Jaunty, chances are you removed the notification bar. So right click on the panel and readd the notification panel.

The name of the applet is network-manager BTW.

---

### Post by philcamlin on 2009-07-18
> **master_kernel said:**
> Haha you're not an idiot (even though that's what I voted :)).

But if you use Jaunty, chances are you removed the notification bar. So right click on the panel and readd the notification panel.

The name of the applet is network-manager BTW.

oh jeez i thought he was talking about an app

sorry if i was wrong litechocolate

---

### Post by cabrey on 2009-07-18
Press Alt-F2 and type nm-applet. Then click run. Of course, that'll only last you for one session... :?

edit: Make an entry in System -> Preferences -> Startup Applications and put this in 'Command' field:

nm-applet --sm-disable

You can name is whatever, but it's default name is 'Network Manager'.

---

### Post by AgentXSmith on 2010-06-21
I deleted the network manager applet from my top panel by accident and can't put it back.  It's not on the drop down menu anymore though it is still in Preferences.  How do I get this back on my panel?

---

