---
title: "Dual Media Problem"
date: 2009-09-15
forum: Hardware
---

### Post by BlueerSkies on 2009-09-15
Bismillaah.   Peace.  To begin, my floppy drive never functioned, after installation. I've mounted it, but it just makes clicking sounds, never displaying the contents of the disk. Its data (text) was initially saved on win xp.

The DVD player works, but recently I tried to backup some text files to a CD, which was successful, as far as imaging the backup, however there are no new files on the open CD, the files were in iso format in a document folder!  

Must I format a CD, using ubuntu?  If so how is that done?  I didn't try to format a floppy using kfloppy, would that be required to make the floppy drive funtional?  Then would it only run on ubuntu?  I have a load of files on XP that I can work with on ubuntu, but I want to transfer them by CD's and floppies. What is the quickest way to make this operational?  Thanks in advance for any help.    


BlueerSkies

---

### Post by BlueerSkies on 2009-09-18
Bismillaah.   Peace.   I tried to format a new floppy disk with kfloppy, and as it turns out it needed fdutils to complete the task.  However, once fdutils was installed it crashed twice after 100% formatting; once with dos format, and again with minix format:

Application: KFloppy (kfloppy), signal SIGSEGV

re:DOS

Thread 1 (Thread 0xb5b06700 (LWP 4323)):
[KCrash Handler]
#6  0xb66c4919 in QObject::objectName () from /usr/lib/libQtCore.so.4
#7  0x08052523 in _start ()


Application: KFloppy (kfloppy), signal SIGSEGV

re: Minix

Thread 1 (Thread 0xb5b69700 (LWP 4676)):
[KCrash Handler]
#6  0xb672791c in QObject::objectName () from /usr/lib/libQtCore.so.4
#7  0x08052523 in _start ()

Can anyone tell what exactly happened here?

I was unable to login to the bug report site, my password('s) was invalid for whatever reason.  

Ububtu 9.04 on a compact presario 2500 notebook, 1gb ram, 80gb hdd.  dual boot w/win xp.

---

