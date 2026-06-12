---
title: "[SOLVED] Apps crashing when saving / opening"
date: 2008-09-24
forum: General Help
---

### Post by DaleNewton on 2008-09-24
Hi all,

Every time I try and SAVE a document of any kind using any of the openoffice programs, or Gimp, evolution mail and some other apps, the program immediately crashes and closes. 

ALso 'Eye of Gnome' document viewer and 'Evince' document viewer are now crashing  when I try and OPEN files.  This started a few days ago.  Everything was fine up to then.

Below are the messages I get in the terminal window and log files....

**When I run evolution mail from terminal I get:**

dale@ubuntu:~$ evolution
evolution-shell-Message: Killing old version of evolution-data-server...

(evolution:7055): camel-CRITICAL **: camel_object_is: assertion `o != NULL' failed

(evolution:7055): camel-CRITICAL **: camel_store_get_folder: assertion `CAMEL_IS_STORE (store)' failed

(evolution:7055): camel-CRITICAL **: camel_object_is: assertion `o != NULL' failed

(evolution:7055): evolution-mail-CRITICAL **: mail_tools_folder_to_url: assertion `CAMEL_IS_FOLDER (folder)' failed

**When I try to save something I get:**

Segmentation fault

**When I run GImp and try to save I get**

dale@ubuntu:~$ gimp

(script-fu:7593): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
Segmentation fault

[B]Gimp Error log: I found this after trying to save with Gimp in the var/log/syslog logfile:
[/B]
Sep 22 14:51:35 ubuntu kernel: [11119.466563] gimp-2.4[31061]: segfault at 3 rip 7f2d1d751940 rsp 7fff29172de8 error 4
[B]
When 'Eye of Gnome' document viewer and 'Evince' document viewer crash when opening files, I get these errors in the logfile:
[/B]
Sep 23 00:22:22 ubuntu kernel: [ 3100.270260] evince[8440]: segfault at 3 rip 7f60cd6c9940 rsp 7fffdc041a28 error 4

Sep 23 00:24:13 ubuntu kernel: [ 3211.579352] eog[10122]: segfault at 3 rip 7fb2f2a3d940 rsp 7ffffefc6ef8 error 4

When I open apps as root they work, and creating a new user works.  However, I dont want to set everything up again on new user, and would like to know whats wrong and fix it if possible.  

Im Using Ubuntu Hardy 8.04.
 
Thanks. ANy help greatly appreciated.

---

### Post by DaleNewton on 2008-10-05
Anyone having this same problem:

One solution I have found is working so far.  You have to remove the programs with synaptic package managerm including configuration files, then reinstall.  THis has worked for me so far with two programs.

---

### Post by Retrolives on 2008-10-23
I'm having the same problem. I'm a n00b though so am useless. If I get it to work I'll it pass on

---

