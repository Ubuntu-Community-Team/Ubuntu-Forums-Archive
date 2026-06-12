---
title: "Confused about cron"
date: 2005-11-04
forum: General Help
---

### Post by BlueNoteMKVI on 2005-11-04
I'm a bit lost here...maybe someone can help me out.

On my servers and my Gentoo systems, I can run the command ```
crontab -e
``` as root and set up my cron schedule.  I know how to do this, it works well on the servers and the Gentoo boxen (which are being migrated to Ubuntu one at a time).

On my new Ubuntu box, I can run crontab -e, I see my crontab, I edit my crontab, but it's ignored.  The commands I put in there are never run.  At first I thought they were being run at the wrong time, because my backups were still happening and logwatch was firing, but nowhere near the times I put into crontab.  Then I found that installing those packages had put cron files into /etc/cron.d and /etc/cron.daily.  Those files were causing the scripts to run.

So...does "crontab -e" as root have any effect?  I'm not using sudo to do that, I put a password on the root account and I use "su" to become root.  If not, that's fine, I can put things into cron.d - Gentoo has all of those directories but I've never used them.  Where do I set the mailto variables for those?  Is there a system-wide mailto variable?  I'm running these crons on my backup server which I rarely log in to, I want an email in my inbox each day to tell me that my backups are complete and one with the logwatch.  How is this done?

---

### Post by Zwack on 2005-11-04
Do you actually have cron installed or just anacron?

Anacron is similar but different.  I can't remember if I had to install cron or if it was installed by default.  Looking at the packages it looks like it is installed by default.

You should also check if you have an /etc/cron.allow and or an /etc/cron.deny.

If you have either then put your username in /etc/cron.allow.

If all else fails perhaps your crontab is incorrect,  in which case a copy of it might help...

I hope that this helps.

Z.

---

### Post by henriquemaia on 2005-11-10
Same problem here. And I still can't get it solved.

I was trying to issue a simple X command, like running amarok at certain times, but still didn't manage to. 

If I run things from /etc/crontab things do happen, but only command line programs - applications under X don't.

Any ideas?

---

### Post by Vogateer on 2006-02-18
[QUOTE=henriquemaia]Same problem here. And I still can't get it solved.

I was trying to issue a simple X command, like running amarok at certain times, but still didn't manage to. 

If I run things from /etc/crontab things do happen, but only command line programs - applications under X don't.

Any ideas?[/QUOTE]

I know I'm awfully late on this one, but for future reference if people happen upon this thread, I'll put this in anyway.

In case anyone else happens upon this problem, the cron utility doesn't really know there is an X server up and running unless you specify the X screen you want to be used within your crontab.  For instance, here is a line that should work, though I'm using Gentoo, so I'd appreciate some feedback if this works for anyone running Ubuntu.

At the very top of your crontab, before anything else put in this line:

```
DISPLAY=:0.0
```

I think this is basically setting an environmental variable, in a way.  I'm still very much a noob on these things.:-k 

Then you should be able to use graphical style programs from your crontab the way you run other programs, given that your X server is up and running when cron tries to run the program.

---

### Post by nbsharma on 2007-02-21
Hi,

Thanks for this clue! It definitely works for Ubuntu, and without this info about X screen in crontab, cron doesn't execute some commands.

cheers.

---

