---
title: "can connect to NAS in command line but not is fstab"
date: 2010-01-16
forum: Hardware
---

### Post by x200t on 2010-01-16
I have the following line that works in command line:
sudo mount -t cifs //192.168.0.103/sharename /media/mdrive -o user=xxx,pass=xxx

I am able to access the drive completely and do all operations.

However, when I put it in fstab it doesn't work. If I put in the line:
//192.168.0.103/sharename    /media/mdrive    cifs    user=xxx,pass=xxx,noauto  0    0

I am unable to mount.

I have tried all variants of:
//192.168.0.103/sharename    /media/mdrive    cifs    user=xxx,pass=xxx,user,uid=7006,gid=100,noauto,nounix,noexec,iocharset=utf8,file_mode=0777,dir_mode=0777    0    0

I get the message "unable to mount".

If I take out the "user" I get the message "only root can mount".

If I take out "noauto" then it mounts on startup, but when I try to unmount by right clicking on icon I get "only root can unmount".

My uid,gid are 7006,100 respectively because at work I connect to a network drive and my root uid was changed to match what it was on the network. For that reason I have noauto on the mdrive which I will only connect to at home. Putting in uid=1000 or leaving it out makes no difference anyhow.

Using a credentials file instead of directly putting in user/pass makes no difference. It also stops the drive from being listed in the Places menu.

I have Karmic (Ubuntu 9.10) and my network drive is a dlink dns323.

Any help would be appreciated.

---

### Post by IcarusR on 2010-01-17
You could try autofs. This mounts filesystems on the fly as one accesses them & unmounts after a defined period of inactivity.
Is in the repos.

---

### Post by DaithiF on 2010-01-19
Hi, instead of 
```
//192.168.0.103/sharename    /media/mdrive    cifs    user=xxx,pass=xxx,noauto  0    0
```

can you try:
```
//192.168.0.103/sharename    /media/mdrive    cifs    username=xxx,password=xxx,user,noauto  0    0

```

'user' is the option that controls whether the currently logged in user can mount/umount (in addition to root).  Its different to the 'username' option which provides authentication details to the target filesystem.

---

