---
title: "How to reach a nfs share from nautilus? [Brezy]"
date: 2005-11-06
forum: General Help
---

### Post by supermarchino on 2005-11-06
I mean, without mounting it from command line.

---

### Post by Tichondrius on 2006-01-21
[https://wiki.ubuntu.com/NFSClientHowTo](https://wiki.ubuntu.com/NFSClientHowTo)

---

### Post by slux on 2006-01-21
Since NFS doesn't have much in the way of authentication for individual users, it's usually just used by adding the entry to /etc/fstab and letting it get mounted at boot. The automount solution that Tichondrius linked has that a prerequisite and I don't see a huge benefit in letting automount handle it on demand as opposed to letting it be mounted all the time unless there's a serious need to limit traffic or something.

---

### Post by Tichondrius on 2006-01-21
[QUOTE=slux]Since NFS doesn't have much in the way of authentication for individual users, it's usually just used by adding the entry to /etc/fstab and letting it get mounted at boot. The automount solution that Tichondrius linked has that a prerequisite and I don't see a huge benefit in letting automount handle it on demand as opposed to letting it be mounted all the time unless there's a serious need to limit traffic or something.[/QUOTE]


umm.....no, you don't need to put anything in /etc/fstab which is just a file that tell linux which filesystems to mount when the OS is booting. You can mount anything afterwards without any relation to /etc/fstab.

Specifically for NFS, the automounter (autofs) lets skip even the mount stage, by simply using the path /net/hostname to browse the shared NFS directory on the specified NFS server.

Contrary to your opinion, I'm talking about facts here, as I am using this setup on my machines at home (2 desktops and a laptop). The NFS w/automount let's me browse each machine shared folders from any other machine just by using /net/hostname path.

---

### Post by slux on 2006-01-23
[QUOTE=Tichondrius]umm.....no, you don't need to put anything in /etc/fstab which is just a file that tell linux which filesystems to mount when the OS is booting. You can mount anything afterwards without any relation to /etc/fstab.


Specifically for NFS, the automounter (autofs) lets skip even the mount stage, by simply using the path /net/hostname to browse the shared NFS directory on the specified NFS server.

Contrary to your opinion, I'm talking about facts here, as I am using this setup on my machines at home (2 desktops and a laptop). The NFS w/automount let's me browse each machine shared folders from any other machine just by using /net/hostname path.[/QUOTE]

Sorry, I missed the part about it taking the hostname and dir and assumed that it needed to know what to mount to /net some other way (that being what fstab is most often used for)

In any case  if you'd like a permanent mount and don't have an arbitrary number of hosts you need to mount thru nfs, you could just add the mount to your fstab and be done with it. The automount solution is of course nice if you have a large number of different hosts that you like to access and even new ones all the time.

---

### Post by Robor on 2006-01-23
[QUOTE=Tichondrius]umm.....no, you don't need to put anything in /etc/fstab which is just a file that tell linux which filesystems to mount when the OS is booting. You can mount anything afterwards without any relation to /etc/fstab.

Specifically for NFS, the automounter (autofs) lets skip even the mount stage, by simply using the path /net/hostname to browse the shared NFS directory on the specified NFS server.

Contrary to your opinion, I'm talking about facts here, as I am using this setup on my machines at home (2 desktops and a laptop). The NFS w/automount let's me browse each machine shared folders from any other machine just by using /net/hostname path.[/QUOTE]
I've got a Fedora Core 4 server with my Ubuntu laptop as a client.  I've been using a command (sudo mount -t nfs 192.168.168.70:/storage /media/FC4Share) from the terminal to mount my FC4 NFS partition.  It's not a big problem but it would be nice if I could just browse to it rather than copy/paste the command from a text file.  How can I use this automounter you're speaking of?

**Edit:  Nevermind that question.  Just saw your HowTo link above.  I'll give that a try.  Thanks!**

---

### Post by Tichondrius on 2006-01-23
Not sure why people here are arguing but try to read again the original post:  

"How to reach a nfs share from nautilus? I mean, without mounting it from command line."

If you set up the automounter then you can do just that, e.g. "ls /net/gamma" and you will see the shared folder on gamma (NFS server) without having to mount it explicitly (the automounter will do that for you, and it will also unmount it after a while if it's not being accessed - smart, eh?)

---

### Post by triwave on 2006-11-22
> **Tichondrius said:**
> umm.....no, you don't need to put anything in /etc/fstab which is just a file that tell linux which filesystems to mount when the OS is booting. You can mount anything afterwards without any relation to /etc/fstab.

I tried to do:
```
sudo mount 192.168.0.100:/home/wbfsl
```

In hopes of reaching that machine and the shared wbfsl directory. I got an error back that "[COLOR="Red"]can't find 192.168.0.100:/home/wbfsl in etc/fstab or etc/mtab[/COLOR]"

I haven't had any luck sharing my folders and wanted to at least try and see if I can get to them just once via command line. I'm really confused by how complicated this is.

So far I have done the following on two machines connected through a home router:
1) Installed NFS and added directories to share on each
2) Installed Firestarter and configured to allow NFS to local network
3) Tried to browse or even just see the other machine and no luck ...

My goal is to be able to just do this once; afterwards I'll work on a more permanent solution. Surely to browse a shared network/folder somewhere just once you don't have to edit /etc/fstab and /etc/mtab but that's the error I get...

What am I doing wrong? :-k

---

