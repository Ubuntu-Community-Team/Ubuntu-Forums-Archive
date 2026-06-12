---
title: "UID Limits and Migration Help"
date: 2008-08-21
forum: General Help
---

### Post by Redline21 on 2008-08-21
I have a bunch of users that I would like to move from Red Hat 9 to Ubuntu Server 8.04. The problem is that RH starts user ID's at 500, while Debian doesn't start until 1000. Anything below a 1000 is reserved for the system. My Ubuntu box is a new install, so I am not currently using and of the IDs between 500-1000. 

Can I go ahead and use those for the existing RH IDs in that range? From what I understand, in Debian everything between 100-1000 is dynamically assigned, so the system should be able to cope with me using some of those IDs for users, as long as it doesn't run out right? Will using those IDs for user accounts cause behavior/functionality problems for the users?

I am sure this is not recommended, but if it is possible it would certainly make things easier. If it is not possible, what can I do to move those users to new UIDs and update all of their file share permissions to reflect the new UIDs?

---

### Post by Vivaldi Gloria on 2008-08-21
I doubt you can use <1000 uids in ubuntu. Try first changing your users RH uids >1000 before you move.

---

### Post by Redline21 on 2008-08-21
I could probably do that...what is the best way?  If I have a user named Bob with a UID of 501, could I run something like

```
/usr/sbin/usermod -u 1001 Bob
```

to change his UID? Then how do I search for and change the files that are owned by his old UID to this new UID?

---

### Post by Vivaldi Gloria on 2008-08-21
> **Redline21 said:**
> I could probably do that...what is the best way?  If I have a user named Bob with a UID of 501, could I run something like

```
/usr/sbin/usermod -u 1001 Bob
```

to change his UID? Then how do I search for and change the files that are owned by his old UID to this new UID?

I've never done this myself before. But the code looks ok. I suggest you read these:

[http://it.toolbox.com/blogs/locutus/how-to-change-a-users-uid-and-gid-26368](http://it.toolbox.com/blogs/locutus/how-to-change-a-users-uid-and-gid-26368)
[http://www.ibm.com/developerworks/aix/library/au-satuidgid/index.html](http://www.ibm.com/developerworks/aix/library/au-satuidgid/index.html)

First create a test user and try on it. The ibm link has some owner scripts you can adapt.

---

