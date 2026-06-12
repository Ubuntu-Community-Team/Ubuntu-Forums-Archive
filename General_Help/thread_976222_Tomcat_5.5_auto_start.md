---
title: "Tomcat 5.5 auto start"
date: 2008-11-09
forum: General Help
---

### Post by ilitheblack on 2008-11-09
Hi m8s, does anybody how to interference auto-start of tomcat 5.5 at boot-time...I want to start it manually..i did not want to change config options to break down the program before asking to anybody if you know the right solution...
THX FOR YOUR INTERESTS..

---

### Post by ilitheblack on 2008-11-09
Nobody knows how to get rid of boot time start of tomcat 5.5 plz :(

---

### Post by Nepherte on 2008-11-09
To remove a service:
```
sudo update-rc.d script_name remove
```
where script is the script_name in /etc/init.d/ you want to remove from startup. In your case it's probably tomcat. To get the exact name, try this:
```
ls -l /etc/init.d/ | grep tomcat
```

---

### Post by ilitheblack on 2008-11-09
Excellent M8,THX for your advice... :) It works great :)... i will repeat this action for all of my auto-start services :)...

---

