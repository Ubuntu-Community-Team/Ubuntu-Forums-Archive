---
title: "cron job problem"
date: 2008-08-02
forum: General Help
---

### Post by dapim on 2008-08-02
i want to print some words each 30 minutes , for that i had make a script and put it to run in cron, isn't working 

00-59/2 *** *   root    /etc/test.sh

---

### Post by dapim on 2008-08-02
every 2 minutes, sorry

---

### Post by kpkeerthi on 2008-08-02
/etc is not the right place to keep your scripts. But that's just my personal opinion. I would rather keep my scripts in /usr/local/bin/ or atleast /usr/bin/

Make sure you have executable permission on test.sh.

What happens when you run the script from command line? Does it run?

There should be spaces after each asterick in the cron entry.

Also note that when cron is run, there is no terminal (the standard output) so you won't be able to see the output from cronned commands if they are printing to standard out. So consider redirecting the command output from the cron to a file or have it open a terminal and run the commands in it, like so:
```
gnome-terminal -e <the command to run in this terminal>
```

---

### Post by kpkeerthi on 2008-08-02
You may find this helpful to some extent:

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by dapim on 2008-08-02
is now running , just put space between each * 

but i would like to do is to pop up a windows with the words each 30 minutes.
and with cron jobs just go to mail, doesn't pop up any window, you know how to do that?

have to do some java program or something?


u are right about files in etc, it was just for test proporsal.

---

### Post by sefs on 2008-08-02
Why not install and use zenity for the pop-ups.

---

