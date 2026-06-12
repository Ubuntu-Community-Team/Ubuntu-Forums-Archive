---
title: "Cron scheduling of iptables-save"
date: 2008-11-02
forum: General Help
---

### Post by Disselboom on 2008-11-02
Hallo all,

I am currently trying to use cron to schedule the automatic saving of my iptables rules using 
[INDENT]"iptables-save > ipsavefile"[/INDENT]

The problem is that the output file "ipsavefile" is blank. This would seem to suggest that "iptables-save" is not being run as root. I did though create the crontab as a root user, and running
[INDENT]crontab -u root -l[/INDENT]
gives the following output
[INDENT]00 00 * * * iptables-save > ipsavefile[/INDENT]
I have confirmed that the cron scheduler is indeed working with an
[INDENT]"echo test > testfile" command. In this case, "testfile" [/INDENT]contains the word "test"

Any help would be greatly appreciated
Thanks

---

### Post by geirha on 2008-11-02
```

$ which iptables-save
/sbin/iptables-save

```

cron uses a minimal environment, and if you try to set the following job "echo $PATH >/tmp/foo" then you'll see that the PATH variable is rather short compared to $PATH in your terminal. In my case its /usr/bin:/bin

So, give the absolute path to the command and it should work. /sbin/iptables-save.

---

### Post by Disselboom on 2008-11-02
Thanks alot, geirha.

That seems to have solved the problem. I'll remember that in future.

---

### Post by bodhi.zazen on 2008-11-02
And to add to that, it is always good to specify the full path for commands in scripts or when automating anything to be run as root.

---

