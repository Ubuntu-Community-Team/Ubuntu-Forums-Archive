---
title: "Delete system log for today?"
date: 2008-07-18
forum: General Help
---

### Post by sugarplumfairy on 2008-07-18
how do you delete the system log? is that possible?

---

### Post by Vivaldi Gloria on 2008-07-18
> **sugarplumfairy said:**
> how do you delete the system log? is that possible?

There are a number of logs created. You can find them in

```
/var/log
```

---

### Post by Claus7 on 2008-07-18
Hello,

I think that you are refering to /var/log/syslog.
If you do sudo rm -rf syslog (inside the aforementioned folder) you will erase it.

Regards!

---

### Post by sugarplumfairy on 2008-07-18
That's exactly what i was looking for 
but where is the folder located?
And how exactly do i write the code in to delete it? 
I'm a new user

---

### Post by Vivaldi Gloria on 2008-07-18
> **sugarplumfairy said:**
> That's exactly what i was looking for 
but where is the folder located?

In /var/log. Press Alt+F2 and type

```
nautilus /var/log
```

to see that folder.

> And how exactly do i write the code in to delete it? I'm a new user

When you open that folder you'll see that there are a lot of logs created. Double click on syslog to see if it is indeed the one you want to wipe.

Start a terminal from applications > accessories menu. The following command in a terminal will clear syslog:

```
sudo cat /dev/null > /var/log/syslog
```

More generally, to clear a text file use this command:

```
sudo cat /dev/null > /path_of_the_file/name_of_the_file
```

If you want to delete it rather than clear it, use the command:

```
sudo rm -i /path_of_the_file/name_of_the_file
```

---

### Post by Yannick Le Saint kyncani on 2008-07-18
> **sugarplumfairy said:**
> how do you delete the system log? is that possible?

Why would you want to remove the system log ? Logrotate will make sure they don't eat too much space on the hdd anyway.

And if it's a privacy issue, your data are scattered all over $HOME.

---

### Post by Bruno12 on 2008-07-18
perhaps it depends on how hard they look?

---

