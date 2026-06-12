---
title: "How to Give Root Powers to others?"
date: 2008-09-11
forum: General Help
---

### Post by matey3 on 2008-09-11
Hi;
I know it is dangerous but hekk this is junker any way and I dont care...
Any way (advices aside) Can I or is it possible to give root's powers to another user?

The doggone thing wont let me make a root user at first and then to add insult to injury (lol) it wont let root logon to GUI (gdm)??
So when I want to copy stuff or do any thing it wont let me do it (in GUI side) and I have to do sudo for every thing else in the terminal (txt mode)?


I created a user called localadmin now how can this localadmin become a root? (or an assistant root)?

Thank You for sharing the info and your knowledge!

---

### Post by qstraza on 2008-09-11
you can edit the /etc/sudoers and add localadmin so he can use sudo command.

---

### Post by Nepherte on 2008-09-11
You could add the user to the %admin group. You must have the following entry in /etc/sudoers:
```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

Or you could give sudo powers to the user only:
```
# User privilege specification
username	ALL=(ALL) ALL
```

Remember to use visudo to edit /etc/fstab!

---

### Post by matey3 on 2008-09-11
> **qstraza said:**
> you can edit the /etc/sudoers and add localadmin so he can use sudo command.

Oh thank you...

As much as I dislike using GUI for the stuff (cuz I want to learn) I found out there is a place under System--Administration--Users And Groups where I can actually login as root/admin-user (by clicking Unlock) and then access the users information.
But I like the command line a lot better and that's because you can do much more that way!

Thanks for the Info.

Regards;

---

### Post by matey3 on 2008-09-11
> **Nepherte said:**
> You could add the user to the %admin group. You must have the following entry in /etc/sudoers:
```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

Or you could give sudo powers to the user only:
```
# User privilege specification
username	ALL=(ALL) ALL
```

Remember to use visudo to edit /etc/fstab!

oops....sorry... I didnt see your reply?!


Thanks very much...
 I copy these things and save them for future references. They come in handy... I appreciate it!
:)

---

