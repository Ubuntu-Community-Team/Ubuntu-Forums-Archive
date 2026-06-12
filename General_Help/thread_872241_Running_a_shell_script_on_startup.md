---
title: "Running a shell script on startup"
date: 2008-07-27
forum: General Help
---

### Post by turiya on 2008-07-27
I have a shell script that I want run every time I log in. How do I go about setting that.

---

### Post by scragar on 2008-07-27
System>Preferences>Sessions

---

### Post by kaibob on 2008-07-27
As noted by scragar, the easiest way is to use the sessions tool:

*System > Preferences > Sessions > Startup Programs > Add*

You can also do this by way of the crontab file with the @reboot option:

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

[http://www.debianhelp.co.uk/crontab.htm](http://www.debianhelp.co.uk/crontab.htm)

---

### Post by cheetaux on 2008-07-27
Assuming that you are running the bash shell, you can just add the name of your script to the .bash_login file in your home directory.

---

