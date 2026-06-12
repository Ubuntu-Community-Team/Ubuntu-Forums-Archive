---
title: "website update alerter"
date: 2008-10-19
forum: General Help
---

### Post by StoutMaster on 2008-10-19
i was wondering if there was a program that could alert you somehow when a website updates.   

i'm in a high school marching and i want to know right away when the website is updated.  an email would be ok, or a noise from my computer speakers


thank you in advance

---

### Post by Hangwire on 2008-10-19
Hmm... 
As far as I know, this is possible with an RSS feed. Does that site support RSS?

---

### Post by StoutMaster on 2008-10-19
no, the site doesn't have an rss feed

the site is carrollbands.org

---

### Post by Hangwire on 2008-10-19
I found just the right thing for you - 

[http://specto.sourceforge.net/](http://specto.sourceforge.net/)

---

### Post by Sam on 2008-10-19
If you want to track the Last-Modified header (if it's used correctly) of the website homepage, use this:
```
wget --output-file=/dev/null --output-document=- --save-headers http://carrollbands.org/ |grep '^Last-Modified:'
```

You can make some script that run in background and checks any changes with this command.

---

