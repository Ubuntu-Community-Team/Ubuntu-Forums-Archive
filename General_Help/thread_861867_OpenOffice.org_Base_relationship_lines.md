---
title: "OpenOffice.org Base relationship lines?"
date: 2008-07-17
forum: General Help
---

### Post by Cyclops_ on 2008-07-17
Hey, all,

Have Hardy 8.04 32 bit at work and 64 bit at home.  In both cases, I've attempted to import a database from MySQL into OpenOffice.org Base (and been successful) using the JDBC Driver.  Once I have it imported, I attempt to set up table relationships.  I have tried this in two ways.

First by just dragging the field of one table to the field of another, and secondly by clicking on the New Relationship button.  In either case, I don't get any error messages, but I also don't get a relationship (line, that is).  Once I saved it, reinstalled everything, then reopened my save, and it had the relationship line, but upon closing and reopening the app, it was gone, and I have not since been able to get it back.

Any help with this would be GREAT!

Mostly I really just need to have a relationship diagram I can show to my boss / coworker by Saturday, so if there is another app that could do this for me, for the time being, I will be fine.

Is there any way to fix this or are there any Data Modelers for Ubuntu?


Thank you very much in advance!

Cy

---

### Post by Cyclops_ on 2008-07-17
*bump*

---

### Post by Cyclops_ on 2008-07-18
*bump again* !  anyone?  i really need this very very soon! 

(THANK YOU)

---

### Post by joris1977 on 2008-08-12
I have been looking into this as well. Not sure what is causing the problem here. Could be MySQL, but i don't know.

See this bug report: [http://bugs.mysql.com/bug.php?id=12975](http://bugs.mysql.com/bug.php?id=12975)

There is a  fix suggested:
Add overrideSupportsIntegrityEnhancementFacility=true to your JDBC connector. The line will look something like this:

jdbc:mysql://localhost:3306/MySQL?overrideSupportsIntegrityEnhancementFacility=true

After that i could fire up the relationship field, but couldn't make any relationships.

---

