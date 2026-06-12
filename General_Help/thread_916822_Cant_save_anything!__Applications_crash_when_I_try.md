---
title: "Cant save anything!  Applications crash when I try to save."
date: 2008-09-11
forum: General Help
---

### Post by DaleNewton on 2008-09-11
Hi all,

Every time I try and save a document of any kind using any of the openoffice programs, Gimp, and evolution, the program immediately crashes with the error 

"Due to an unexpected error, (openoffice.org) crashed. ...................................
    .....the following files will be recovered"

This happens everytime- wIth the openoffice suite, Gimp image editor, and with evolution mail too!  

I cant save anything!  (except with Compozer web composer, which still allows me to save.

Any ideas about this?  I tried reinstalling open office. That didnt work. Are there any log files that log this kind of crash?
 
Thanks all,
Dale.

---

### Post by aysiu on 2008-09-11
A couple of questions and a suggestion:

1. Did this just start happening recently, or has it always been like this?

2. Does this happen for all users on your system? And if you have only one user, create a new test user and see if that test user has the same problem.

3. Try starting an application from [the terminal](http://www.psychocats.net/ubuntu/terminal) and seeing what error messages appear when the application crashes.

---

### Post by DaleNewton on 2008-09-12
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

[B]
when I run programs as Root everything works fine![/B]


I created a new user with the same privileges as my normal user, and everything works fine.

It has only just starting doing this.  I have dula boot with Windows and windows got a nasty virus the other day which changed system settings in Windows.It took hours to sort that out. About that time Ubuntu started doing this. DOnt know if thats anything to do with it.

D.

---

### Post by DaleNewton on 2008-09-22
**I found this after trying to save with Gimp in the var/log/syslog logfile:**

Sep 22 14:51:35 ubuntu kernel: [11119.466563] gimp-2.4[31061]: segfault at 3 rip 7f2d1d751940 rsp 7fff29172de8 error 4


Could this be a privileges problem?  Which folders/files should I be checking?  

I want to avoid running everything as root, or transferring my hard drive contents and setting up everything again. Plus would like to find out what the problem is.

Thanks for any help.

---

### Post by DaleNewton on 2008-09-22
'Eye of Gnome' document viewer and 'Evince' document viewer are now crashing when I try and open files aswell, with these errors:

Sep 23 00:22:22 ubuntu kernel: [ 3100.270260] evince[8440]: segfault at 3 rip 7f60cd6c9940 rsp 7fffdc041a28 error 4

Sep 23 00:24:13 ubuntu kernel: [ 3211.579352] eog[10122]: segfault at 3 rip 7fb2f2a3d940 rsp 7ffffefc6ef8 error 4

Any ideas/help appreciated.

---

