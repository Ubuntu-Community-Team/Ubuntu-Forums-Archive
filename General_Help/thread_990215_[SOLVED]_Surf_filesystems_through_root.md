---
title: "[SOLVED] Surf filesystems through root"
date: 2008-11-22
forum: General Help
---

### Post by L1GTN1NG on 2008-11-22
I triple boot windows ubuntu and SUSE. In SUSE I can surf my files through root, I just have to enter in my root password and I can change anything I want. I am sure you can do that in ubuntu, but how? Thanks in advance

---

### Post by Idefix82 on 2008-11-22
You need to read this:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by L1GTN1NG on 2008-11-22
I know the advantages and disadvantages of using su. I used SUSE linux for over a year and am just trying ubuntu. I dont want to change folders around and all that stuff through terminal. I read through I'd like it to be in a window like you see normally, except your root. I hate seeing 'error: permission denied.':)

---

### Post by Idefix82 on 2008-11-22
Then start your GUI applications with gksudo, like 
```
gksudo gedit
```
or
```
gksudo nautilus
```

---

### Post by L1GTN1NG on 2008-11-22
With root:
```

root@laptop:/home/lxuser# gksudo gedit
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(gksudo:9984): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(gedit:9985): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported

root@laptop:/home/lxuser# 

```

```
root@laptop:/home/lxuser# gksudo nautilus
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(gksudo:10236): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:10237): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: No such file or directory
Could not create per-user gnome configuration directory `/root/.gnome2/': No such file or directory
root@laptop:/home/lxuser# 


```


Not in root:```
lxuser@laptop:~$ gksudo nautilus
(nautilus:10372): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: No such file or directory
Could not create per-user gnome configuration directory `/root/.gnome2/': No such file or directory

``````

lxuser@laptop:~$ gksudo gedit
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-qrVrVGdHTx: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-M7vefScBmH: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-4h6qXTF07Z: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-pnAASkvcAM: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-YK5p6YafJj: Connection refused)

```

---

### Post by prshah on 2008-11-22
> **L1GTN1NG said:**
> I dont want to change folders around and all that stuff through terminal. 
I hate seeing 'error: permission denied.'

Not recommended, but:

Press Alt+F2, then give the command ```
gksudo nautilus
``` or the file manager of your choice.

root logins are discouraged in Ubuntu, to the extent that it is against forum policy on how to enable root logins.

If you are logged in as root, do not use gksudo. If you are a regular user, use gksudo to get root-like abilities.

---

### Post by L1GTN1NG on 2008-11-22
> **prshah said:**
> Not recommended, but:

Press Alt+F2, then give the command ```
gksudo nautilus
``` or the file manager of your choice.

root logins are discouraged in Ubuntu, to the extent that it is against forum policy on how to enable root logins.

If you are logged in as root, do not use gksudo. If you are a regular user, use gksudo to get root-like abilities.

Alt-F2 did the trick. Thanks to both of you!!

---

### Post by prshah on 2008-11-22
> **L1GTN1NG said:**
> Alt-F2 did the trick. Thanks to both of you!!

Can you mark the thread solved? Click "Thread Tools" near the upper right hand side of the page, and select "Mark Thread as Solved".

---

