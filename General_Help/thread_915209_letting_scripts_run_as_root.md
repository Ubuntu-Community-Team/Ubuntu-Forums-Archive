---
title: "letting scripts run as root"
date: 2008-09-09
forum: General Help
---

### Post by shortridge11 on 2008-09-09
I am writing a program, and when certain conditions are met it runs script.  Some of the things i want it to do are update or reboot.  I can't do either of those things unless i use sudo or run as root.  How do i make my scripts run things as root?  I can't give everything in the program access as root because that is unsecured for what i'm using this for.  One of my friends told me about fakeroot, but that's not really working.  At the least, could i do something like make the script run 
sudo reboot; [insert password here];

or maybe do something that would make time pass between the 2 commands and then have the password put in?  I'd like to bypass the password part if possible though.  But if not, i can read it in from a file or something more secure.

---

### Post by hyper_ch on 2008-09-09
add a cronjob that run the script like every 5 min. In the script make a check on whether a file exists. If it exists, then let the script delete that file continue with what you want actually the script to do. If it does not exist, then quit the script.

Then, when the conditions are met that you desire, have that empty file being created.

---

### Post by bodhi.zazen on 2008-09-09
Make a new user ...

Lock down the new user (passwd new_user-l, chsh to /bin/false, use rbash, etc.).

Give the new user the ability to run the commands in question with sudo without a password :

ie use visudo

Then make the script owned by root.new_user

permissions 550

Then :

sudo -u new_user script

========

or use expect :

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

[http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

---

### Post by shortridge11 on 2008-09-10
editing visudo for the new user idea seems like the best bet.  I want to give it no-password access to certain things.  How would i edit it to have access to only specific programs?  I called my new user oscar, and here is what i typed in under root- this is temporary until i figure out how to do specific programs...until i figure that out i'll just give it full access

oscar  ALL(ALL) NOPASSWD:ALL

---

### Post by shortridge11 on 2008-09-11
bump

---

### Post by bodhi.zazen on 2008-09-11
[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

