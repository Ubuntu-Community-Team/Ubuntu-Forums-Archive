---
title: "how to update? or is it upgrade?"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by three_jeeps on 2009-09-29
I am currently running 8.04 LTS SERVER and am thinking that I should move it up to a newer version 8.10 or 9.04.  I use the machine to run a couple of (v) websites (apache 2.2) a mail server (at the moment, only outbound)[postfix/dovecot/courier], a fax server (hylafax), and home automation daemon (heyu).  The reason I am thinking about upgrading is that my USB modem operation is flakey, and there is some conflict when I run heyu that blocks the fax from answering.  Right now, heyu is low on the priority list so I don't run it. I pretty much did a standard install of 8.04 server and I went through a lot of pain to get the webserver & associated websites, mail and hylafax operational. What I don't want to have happen is for the upgrade to kill apache, faxserver, and mail server.  What is the likelyhood that the upgrade would be 100% successful without the patient dying???
I don't want to go through a clean install and reexperience the pain that I did before. Neither do I want the joy of trying to figure out what the upgrade did to kill one of my applications.
I was thinking about using the upgrade approach foundhere:
[http://www.howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server)
(better recommendations?)
So can someone point me to a source that explains exactly what happens when an update is done?  e.g. is a new kernel installed? are existing drivers preserved? etc.
Thanks in advance.
-J

---

### Post by Sef on 2009-09-29
I would wait for 10.04, Lucid Lynx because it will be an LTS.  The others you mentioned are only supported for 18 months instead of 5 years for the server version.

---

### Post by oboedad55 on 2009-09-29
I second waiting. It looks like you went through a lot to get things set up the way you want and it would be a shame to ruin that by upgrading to a version without lts.

---

