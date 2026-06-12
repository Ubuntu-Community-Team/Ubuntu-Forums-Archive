---
title: "Running a script from root as user? (From acpi open/close lid and hal events)"
date: 2009-02-20
forum: Hardware
---

### Post by lunatico on 2009-02-20
Hey All,

I have found a way to catch the "open/close lid" and "dock/undock laptop" events and now I want to run some scripts depending on the event. For example, if I close my lid I would like to set my Pidgin status to away with a message saying the my laptop's lid is closed, or if I dock my laptop I would like to configure my resolution on a certain way. I have all the scripts to do everything I want and if I run them as my user they run and work perfect.

My problem is, when I try to run those same scripts from the mentioned events some commands will not work.

Take the acpi lid event for example. There is a script on /etc/acpi/lid.sh which runs every time you open or close your laptop lid. So I just added a line at the begining of that script like /home/user/my_lid_script. As I said, if I run the script as my user it runs fine, but since the acpid process is owned by root, then root is the one that is running this script. Some things work, like aplay to make a wierd noise. But changing the status on Pidgin will not work.

To make things clear try this:
As user run:

```
purple-remote "setstatus?status=away&message=Test message"
```

The status of your Pidgin will change. Provided that you have it running, are logged in and have libpurple-bin installed.
Then become root and run the same command again. You will get error "No existing libpurple instance detected".

I have tried to run the command as the user with:
```

su - user -c 'purple-remote "setstatus?status=away&message=Test message"'
```

But it will still not work.
I am puzzled with this one. Any help would be much appreciated.

Thanks!

---

### Post by sdennie on 2009-02-20
I think /etc/acpi is a bit misleading.  It used to work just fine but, in versions later than 8.04 not all the scripts there execute on events and instead pm-utils handles a lot of things.  I'm not sure about the lid event and so it may still be handled by /etc/acpi/lid.sh.  I would try two things.  First, see if adding this to lid.sh creates a file in /tmp when you close the lid:

```

touch /tmp/lid_closed

```

Also, see if you changing your command to this helps:

```

DISPLAY=:0.0 su user -c "purple-remote 'setstatus?status=away&message=Test message'"

```

---

### Post by lunatico on 2009-02-20
> **sdennie said:**
> First, see if adding this to lid.sh creates a file in /tmp when you close the lid:

Yes I'm pretty sure the /etc/acpi/lid.sh scripts is working just fine. Running other things like aplay to make asound works ok.

> **sdennie said:**
> 
Also, see if you changing your command to this helps:

```

DISPLAY=:0.0 su user -c "purple-remote 'setstatus?status=away&message=Test message'"

```

Same error.

---

### Post by lunatico on 2009-02-28
I finally solved this. I posted a tutorial.

[[HOWTO] Run scripts for laptop lid open/close and dock/undock events]("http://ubuntuforums.org/showthread.php?t=1076486")

---

