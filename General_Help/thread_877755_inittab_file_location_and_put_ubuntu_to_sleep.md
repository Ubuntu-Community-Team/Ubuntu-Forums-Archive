---
title: "inittab file location and put ubuntu to sleep ?"
date: 2008-08-02
forum: General Help
---

### Post by tanveer on 2008-08-02
Hi,

I have some queries hope you great ones can easily answer which I am encountering.

1. The location of file /etc/inittab where the tty consoles are mentioned in ubuntu? As I was willing to block access to those for my users and just keep the GUI so that they can't use CTRL+ALT+F1-F6. But didn't find any file named inittab in ubuntu

2. How to make the starting of GUI login screen sleep for say 10/15 secs? The reason is that I joined my ubuntu machine with win AD 2003 using Likewise Open and afer starting the PC when the login GUI comes and if I immediately give the AD login credentials then It fails saying the Domain Controller is not accessible so using cached credentials. But if I give login credentials after 10/15 secs then it doesn't give that. May b the processes are taking some time to start. So want to give it some time by sleep. WHere to give that?

3. Now another problem is connection with Hardy and exchange 2007. Is anybody successful connecting these two? I had no problem when using exchange 2003 but recently we migrated to 2007 and which evolution exchange connector seems doesn't support yet. Is evolution brutus can do the trick as I also failed to compile that in Hardy.

Thanks in advance for any help.

---

### Post by Vivaldi Gloria on 2008-08-02
> **tanveer said:**
> 1. The location of file /etc/inittab where the tty consoles are mentioned in ubuntu? As I was willing to block access to those for my users and just keep the GUI so that they can't use CTRL+ALT+F1-F6. But didn't find any file named inittab in ubuntu


Ubuntu uses the new upstart init deamon. The main folder is /etc/event.d. All rc folders and ttys are called from there.

---

### Post by tanveer on 2008-08-03
Hey, 
Thanks for that.That solved my first prob. But isn't there any file like rc.local in ubuntu which is executed at last like in redhat so that I can put the sleep command there.

---

### Post by Vivaldi Gloria on 2008-08-03
> **tanveer said:**
> Hey, 
Thanks for that.That solved my first prob. But isn't there any file like rc.local in ubuntu which is executed at last like in redhat so that I can put the sleep command there.

There is

```
/etc/rc.local
```

---

### Post by tanveer on 2008-08-03
> **tanveer said:**
> Hey, 
Thanks for that.That solved my first prob. But isn't there any file like rc.local in ubuntu which is executed at last like in redhat so that I can put the sleep command there.

Found the the solution of 2nd problem here
[[https://help.ubuntu.com/community/RcLocalHowto]](https://help.ubuntu.com/community/RcLocalHowto])

---

### Post by tanveer on 2008-08-04
Yes, you are right. 
But putting sleep command doesn't seem to delay the display of GUI login window. :(

---

