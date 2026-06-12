---
title: "Firewall to start at start up"
date: 2008-08-19
forum: General Help
---

### Post by Tony_photoplus on 2008-08-19
I have been reading on this web site:
[http://www.fs-security.com/docs/faq.php#trayicon]("http://www.fs-security.com/docs/faq.php#trayicon")
How to get your firewall starting at start up.  This should be standard, I am aghast that this is not done as the norm.  However, I read and don't understand where I have to write a line to.  Just stating the fact makes no sense, so would like to know where if poss this area is?  Also do you know how to just have an icon in the tray as when I close it and expect it to stay it shuts down and not close to the icon in the tray.  Weird way of doing things.

Many thanks

tony

---

### Post by mike555 on 2008-08-19
You could go to  [www.getdeb.net](www.getdeb.net) and get "gufw" it will let you turn on the firewall and do some adjustments........

---

### Post by colobix on 2008-08-19
Ok. go to the system menu > preformances > sessions and then click on Add.

Good luck.

---

### Post by coffeecat on 2008-08-19
> **Tony_photoplus said:**
> How to get your firewall starting at start up.

No - that tells you how to get firestarter to start when booting-up. Firestarter is **not** the firewall; it is merely a GUI frontend to change and adjust firewall rules. The Linux firewall is IPtables which is working every time you boot up Ubuntu - unless you use firestarter to switch it off.

---

### Post by Tony_photoplus on 2008-08-20
> **coffeecat said:**
> No - that tells you how to get firestarter to start when booting-up. Firestarter is **not** the firewall; it is merely a GUI frontend to change and adjust firewall rules. The Linux firewall is IPtables which is working every time you boot up Ubuntu - unless you use firestarter to switch it off.

So in other words it already there and this is just a piece of software that turns it on and off.  Sorry just getting it in my head and repeating what yo stated.  I will get rid of it then as I want it on all the time and if it ever needs turning off I know where to go.

Thanks 
Tony

---

### Post by mb_webguy on 2008-08-20
Yes, iptables is always running, but by default has rules of ACCEPT for all connections (which you can see with the command "sudo iptables -L" in the terminal).  That means that it's not actually blocking anything unless you change some settings.  You can do that manually in the terminal, or you can install a GUI front-end for iptables, such as Firestarter.

Also, before you start worrying too much about installing Firestarter and messing around with your firewall settings, you might want to have a look at [this website]("http://www.psychocats.net/ubuntu/security") dealing with security on Ubuntu.  You may very well decide you don't need to do anything.  While that page wasn't written by a security specialist (as the disclaimer at the top states), it's good information (and this is coming from someone who *does* know a bit about network security).

---

### Post by Tony_photoplus on 2008-08-20
Thanks for that.  Its a lot to take in

Tony

---

