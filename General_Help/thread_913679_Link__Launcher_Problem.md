---
title: "Link / Launcher Problem"
date: 2008-09-08
forum: General Help
---

### Post by LostPavek on 2008-09-08
I'm trying to create a link or launcher for a shell script but I can't figure out why it doesn't work.

The script is /usr/local/tomcat/bin/startup.sh

I can enter that on the command-line and Tomcat starts.  I create a link by typing:

```
ln -s /usr/local/tomcat/bin/startup.sh ~/Desktop
```

And either double clicking on the link or right-clicking and executing the link causes nothing to happen.

I renamed the link "start tomcat" and moved the link to /usr/bin and now I can type "start tomcat" anywhere in a terminal and Tomcat will start, but if I create a launcher with "start tomcat" as the command, tomcat doesn't start, seemingly nothing happens.

I can run the startup.sh and shutdown.sh scripts from a terminal, I can run them using the links from a terminal, but they don't run using a launcher or by executing a graphical link.

I've checked the permissions on the scripts and they're set to 755 so that doesn't seem to be a problem.

Thanks for any help understanding this problem!

---

