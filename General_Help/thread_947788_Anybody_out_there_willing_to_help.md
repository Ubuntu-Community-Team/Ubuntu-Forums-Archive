---
title: "Anybody out there willing to help"
date: 2008-10-14
forum: General Help
---

### Post by zmaj_lee on 2008-10-14
PLEASE HELP****

This is my first post here, and I am new to ubuntu and Linux in general. I had to set up postfix at my company, actually I had to upgrade it because it was not running as it should. Original one was running from Red Hat so I just got Ubuntu-Hardy and at first I tried to install it and configure it from scratch but since it was unfamiliar to me I just used the old configuration file from Red Hat and it worked, it actually works fine. I am sorry for dragging this but here is my problem now: The conf file like I said is copied from old installation and it already has all of the rules set up and one of them is not to allow anybody to use my exchange as a relay, which is good but I am in the situation where somebody else is hosting my shopping cart and I need to make an exception in my postfix conf file so it allows this company (or their IP) to relay emails thru my exchange. I have available my configuration puled from webmin if needed for who ever wants to help me, or you can tell me other way of getting you my configuration, anyway this is being holding me from finishing this project for 2 weeks now and I really need to get this working so any help would be highly appreciated. Thank You very much everybody....

---

### Post by LowSky on 2008-10-14
I would like to say that maybe you should have stuck with a REd Hat Distro like Fedora, but Welcome to Ubuntu maybe it will all work fine.

Take a look at this website maybe it will help
[http://www.unixwiz.net/techtips/postfix-exchange-users.html](http://www.unixwiz.net/techtips/postfix-exchange-users.html)

---

### Post by zmaj_lee on 2008-10-14
Thank you LowSky for responding to my cry for help here. The link you provided is in regards to creating relay_recipients table which I already have set up on my postfix. It is the relay exception that I am looking for how to set up. I hope that there is answer to this cause my time is running out.........

---

