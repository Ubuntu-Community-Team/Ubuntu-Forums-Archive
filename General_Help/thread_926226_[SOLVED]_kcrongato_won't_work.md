---
title: "[SOLVED] kcron/gato won't work"
date: 2008-09-21
forum: General Help
---

### Post by computer_freak_8 on 2008-09-21
I am having issues with two different programs, "kcron" and "gato".

When I attempt to run gato from the Applications menu, nothing appears to happen. However, by using "tail -f /var/log/syslog", I get the following output:
```
Sep 21 17:08:10 multiboot kernel: [14812.432843] gato[9759]: segfault at 1 rip 7f84e5e2537e rsp 7fffee376bc0 error 4
```From the command line, it looks like:

user@computer:~$ gato

GLib-CRITICAL **: file ghash.c: line 138 (g_hash_table_lookup): assertion `hash_table != NULL' failed.

Gtk-CRITICAL **: file gtkobject.c: line 1162 (gtk_object_ref): assertion `GTK_IS_OBJECT (object)' failed.

GLib-CRITICAL **: file ghash.c: line 138 (g_hash_table_lookup): assertion `hash_table != NULL' failed.

Gtk-CRITICAL **: file gtkobject.c: line 1069 (gtk_object_get_data_by_id): assertion `object != NULL' failed.
Segmentation fault
user@computer:~$ 


As for kcron, it runs fine - it just won't execute any tasks. However, looking at the log when a scheduled task ("vlc /home/jaredtbrees/Media/alarm002.wav") is supposed to go off, I get the following from "tail -f /var/log/syslog":
```
Sep 21 17:15:01 multiboot /USR/SBIN/CRON[9825]: (jaredtbrees) CMD (vlc /home/jaredtbrees/Media/alarm002.wav)

```I have checked to make sure both cron and at are installed:
```
user@computer:~$ sudo apt-get install cron at
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cron is already the newest version.
at is already the newest version.
The following packages were automatically installed and are no longer required:
  dpatch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
user@computer:~$ 
```Any ideas on what the problem could be?


Thanks, 

computer_freak_8

---

### Post by computer_freak_8 on 2008-09-24
Bump, please?

---

### Post by computer_freak_8 on 2008-09-30
Bump

---

### Post by computer_freak_8 on 2008-10-03
Bump???

---

### Post by computer_freak_8 on 2008-10-13
[SIZE="7"]B[/SIZE][SIZE="6"]umpity, [/SIZE][SIZE="5"]bumpity, [/SIZE][SIZE="4"]bump [/SIZE][SIZE="3"]bump [/SIZE][SIZE="2"]bump[/SIZE][SIZE="1"]![/SIZE]

---

### Post by computer_freak_8 on 2008-10-23
BbbBBBbbbbbBBBBBBBBbbbbbbbbbbbbbump bump.

---

### Post by computer_freak_8 on 2008-11-14
Okay, I understand if no one knows of a solution. But will somebody please post some sort of a reply so I know that my thread is visible? I just remembered that my computer was glitchy the day I started this thread. I don't know how this could have affected the visibility of this thread, but ya' never know, ya' know?

---

### Post by computer_freak_8 on 2008-11-16
I did some more looking around. Finally, I ran across someone that appeared to have the same problem. Thanks to user bigtomrodney over at the Linux Forums, I now know the reason it was failing, and I also have a solution.

For those it may help:

Cron doesn't have a connection to the X Server. I wondered if this was the case, but doubted it since I could run it from the command line. The [explanation]("http://www.linuxforums.org/forum/ubuntu-help/125920-solved-cron-issues-i-think.html#post607102") I read, however, made sense as to why my reasoning was wrong.

Here's the solution: Write a "wrapper script".

In my case, I ended up with pointing (via Kcron) my crontab file to a script I wrote and made executable. The script looks like this:```
#!/bin/bash
export DISPLAY=:0.0
vlc /home/jaredtbrees/Media/alarm002.wav
exit 0
#EOF
```Note: I first tried using "/bin/sh" as the program to run the script, but it didn't work, so I had to change it to "/bin/bash".

---

