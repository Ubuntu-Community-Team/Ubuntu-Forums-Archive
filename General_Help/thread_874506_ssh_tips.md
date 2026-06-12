---
title: "ssh tips"
date: 2008-07-30
forum: General Help
---

### Post by alazou on 2008-07-30
Hi everyone. her is my plea :)

I'm finaly trying out the ssh server, and I would like to know if it is possible through it, to mount an iso from my computer, on to another one. basicaly I want to know if it possible to copy something from my computer in to the other one.

Thanks for any reply and tips :)

---

### Post by p_quarles on 2008-07-30
Yes, mounting an ISO-9660 file remotely is possible via SSH. And, yes, copying things from one computer to another is possible. If you could explain a little more precisely what you want to do, I'm sure someone can help.

---

### Post by alazou on 2008-07-30
hi thanks for the quick reply.

to be more precise I'm trying to copy some doing the following : 
sudo cp /home/azalou/Do*/optimize.m /home/manaf

There is no error message but the file is not transfered. also firestarter reports no blocking whatsoever.

for the mounting I do the same with the mount command, but it says the file is not existant. I don't know what I'm doing wrong.

---

### Post by p_quarles on 2008-07-30
You can mount remote drives using sshfs and fuse, but that isn't necessary for this (nor is sudo). Try this:
```
scp [ip.address.of.remote.machine]://home/azalou/Do*/optimize.m /home/manaf
```
That should work unless there's more details you haven't yet provided.

---

### Post by iaculallad on 2008-07-30
Instead of using cp, try using scp:

```
sudo scp username@w.x.y.z:/home/whoever/wherever/file .
```

EDIT: Oooopppssss... they had already suggested it. Disregard

---

### Post by alazou on 2008-07-30
I'll try to be more precise :

what I have done so far :
installed ssh server
connect remotely to azalou's computer
issued the command.

and then it display the error mentionned before.

I tried installing sshfs and fuse and issued the command you have posted but it says cp: cannot stat 'ip-adress'L no such file etc..
here the commands that I tried
scp 192.168.etc ://home/blabla /home/blabla
scp [192.168.etc] ://home/blabla /home/blabla

I'm I missing something 6

---

### Post by p_quarles on 2008-07-30
"scp" is a copy command that connects to a remote computer (and is part of the ssh package). You don't connect to the remote computer prior to using it: you use scp to connect to the remote computer.

---

### Post by david_lynch on 2008-07-30
> **alazou said:**
> I'll try to be more precise :

what I have done so far :
installed ssh server
connect remotely to azalou's computer
issued the command.

and then it display the error mentionned before.
And what error would that be? I don't see any mention of an error above.

> 
I tried installing sshfs and fuse and issued the command you have posted but it says cp: cannot stat 'ip-adress'L no such file etc..
here the commands that I tried
scp 192.168.etc ://home/blabla /home/blabla
scp [192.168.etc] ://home/blabla /home/blabla

I'm I missing something 6
You don't need sshfs to scp a file. The commands you tried make no sense to me. Maybe if you explain exactly what it is you want to do, we can help. And please do a copy and paste of the exact commands you typed, and the error messages, so that we can make some sense of it.

:popcorn:

---

### Post by alazou on 2008-07-30
thank you very much it worked ! 
do you know if I can get some *simple* documentation on how to use ssh ? This way I won't bother you anymore :p

EDIT: No worry David, thanks. the only thing that I need doing now is mount remotely. but I,ll try finding that on my own, I've taken enough of your time.

---

### Post by jdoliner on 2008-07-30
hmm I think the man page for ssh is fairly simple just

```
man ssh
```

---

### Post by finite9 on 2008-07-30
if anyone knows how to mount an ISO over SSH I would be very grateful.  I am sick of SCP'ing my ISOs from server to laptop to watch them on laptop.  I am very familiar with all standard ssh stuff but not so hot on fuse.

I think I tried sshfs and fuse a year or two ago and could not get it to work.

oh wait...maybe my problem was that I could mount an SSH FS but Totem would not play an ISO on a remote mount.  anyone know of this issue?

---

### Post by bodhi.zazen on 2008-07-30
For ssh :

[uwiki]SSHHowto[/uwiki]

For sshfs :

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

You can use other network protocols to share files, samba or nfs or ftp or http :)

---

