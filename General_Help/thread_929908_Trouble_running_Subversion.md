---
title: "Trouble running Subversion"
date: 2008-09-25
forum: General Help
---

### Post by NuNn DaDdY on 2008-09-25
I recently installed subversion on my system, however I am unsure as to how to the client or where the executable file is located.

---

### Post by nikgare on 2008-09-25
man svn

---

### Post by ingo on 2008-10-23
> **nikgare said:**
> man svn

@ nikgare - was that supposed to be helping or crapping on somebody from a very large height?

@ NuNn DaDdY - I'm hitting a similar brick wall as you. As far as I can see you are able to set up a project by typing ```
svnadmin create /path/name_of_project
```But I am afraid I am not much further than that :( The man pages (as nikgare kindly pointed out) are less than helpful and their website is stuffed full of links and I haven't found one yet which makes sense.

Let's exchange info if you/me/anybody finds how to get out of this mess.

---

### Post by ingo on 2008-10-23
Update - a quick 
```
apt-cache search svn|grep kde
```came up with kdesvn - I'm not sure whether there is anything for gnome. Kdesvn comes with a handbook which I am about to pour over...

---

### Post by ingo on 2008-10-23
and today's last post:

There is a forum! Let's hope there is some kind soul there who treats people new to the subject kindly... Anyway, here goes:

[http://svnforum.org/](http://svnforum.org/)

---

### Post by shaggy999 on 2008-10-23
There is a free book available called "Version Control with Subversion" that talks about everything you need to know about subversion. I think it was an O'Reilly book once and then they put it on the internet for free. The book is available here:

[http://svnbook.red-bean.com/](http://svnbook.red-bean.com/)

---

