---
title: "How do I install Python Cherrypy 2.1?"
date: 2005-12-27
forum: Installation &amp; Upgrades
---

### Post by eyce on 2005-12-27
The only version I can find is Cherrypy 0.1.01 or something (April 04) - but no late versions. I'm a total newbie to linux (just made the switch).

Thanks for all your help.

---

### Post by eyce on 2005-12-27
Got it working.
Install python-dev.
Download Cherrypy source, and extract it to a folder.
Then go in and do the command-line thing as super-user (su): 
> python setup.py install.

Cheers all.

---

### Post by Railsbuntu on 2008-01-24
Old thread but still useful.

Where should I create the cherrypy folder? I don't feel like messing up my home folder.

By the way cherrypy is now up to version 3.0.3 :popcorn:

If you want the tutorials to work, edit tutorial.conf and change localhost to your server's IP if you want to access it from another computer.

---

