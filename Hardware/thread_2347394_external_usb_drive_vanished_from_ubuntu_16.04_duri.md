---
title: "external usb drive vanished from ubuntu 16.04 during long file operations"
date: 2016-12-24
forum: Hardware
---

### Post by gkhar2 on 2016-12-24
[COLOR=#111111][FONT=Ubuntu]During big file copy operations a ntfs-formatted usb-drive just vanished from ubuntu. 

I checked on the syslog and found out that at 4:54am in the morning the device got lost. there are lots of other errors in the log, also.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]unfortunately i am new to ubuntu, so can anybody have a look at the syslog and can tell me what has happened and how i can get the device stay available in ubuntu?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I restarted the laptop and the usb-drive and again after a view hours of copying without problems it suddenly went offline again. same issue. 

Please  could anybody help me with that, i am without a clue.

other issue> i cannot upload the syslog (about 500k), as the uploader says, it exceeds the max filesize for txt files...???? What shall i do???

thanks so much 

gkhar2[/FONT][/COLOR]

---

### Post by gkhar2 on 2017-01-03
Hi, unfortunately no new comment. Maybe i should add some more information: It is a samsung story station 1,5TB. 

I tried and restartet ubuntu and the hdd again, but it happened again, after a couple of hours file copying.

Ansbody who had the same issues or knows what to do about it?

thanks 

gkhar2

---

### Post by gkhar2 on 2017-01-03
There was a similar issue discussed a long time ago, but the thread was closed.

[https://ubuntuforums.org/showthread.php?t=1330978](https://ubuntuforums.org/showthread.php?t=1330978)

---

### Post by gkhar2 on 2017-01-06
still nobody. Am i the only one, having these issues?

---

### Post by sudodus on 2017-01-06
I can try to help you troubleshoot your USB disk.

I suggest that you start by connecting it to a computer with Windows, and use Windows tools to check and if necessary fix the file system. You can do it with a GUI tool or via the command line in Windows `cmd`

```
chkdsk /f X:
```

where X is the drive letter. Replace with the actual drive letter, for example D:

If you suspect bad sectors (physical defects), you can use

```
chkdsk /r X:
```

---

### Post by gkhar2 on 2017-01-14
Hello sudodus,

thanks for your answer. The drive works well with windows 10 for 2 years, never did vanish nor did i get any errors from it. 

It just happened when i connected it to my ubuntu 16.4 laptop after maybe 2hours of intensive file-copy. I did this to copy files from it to a new ext4 formated drive, i want to use in my nas.

When i put the usb-drive back to windows 10, it is functioning without the slightest glitch (now again since 3 weeks).

if you could tell me, how to attach the syslog, i would put it here, but the uploader says it is too big (500k ?)

best regards

gkhar2

---

### Post by sudodus on 2017-01-15
I am no expert concerning log files. Let us hope someone who knows better will help you with the log files.

---

