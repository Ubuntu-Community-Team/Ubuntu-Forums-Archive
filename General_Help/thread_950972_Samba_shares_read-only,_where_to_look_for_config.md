---
title: "Samba shares read-only, where to look for config"
date: 2008-10-17
forum: General Help
---

### Post by amorangi on 2008-10-17
I upgraded my home server from 7.04 to 8.04, but the way to admin samba shares seems to have changed for the worse. Previously I had about 10 shares with different levels of read/write access for each member of the household for each folder. When I set up the shares again on 8.04 under no circumstances would it allow write access from the clients, either from a windows client, mounted using cifs, or using the network browser. After reading a lot of threads none solved my problem, and what seemed to fix it was copying my old smb.conf file from 7.04 backup to the 8.04 install. This worked for most but not all of the shares - about 7 now have the correct write access, but 3 remain stubborn. In my attempts at using the new system for assigning the shares I've obviously defined some bad values somewhere in the system that I can't find.

For the malfunctioning shares: 
If I remove the share, rename the folder, then reassign the share it will have the correct write access.
If I remove the share, move the folder to a different location, then reassign the share it will NOT have the correct write access.

As well as this I've had a few hard lockups on the 8.04 clients which I can only attribute to the cifs mounts, probably due to me changing the shares on the server while trying to fix this problem. It's happened on 2 machines that have previously been rock solid, and I've run extensive tests to rule out any hardware faults, plus the fact it's only happened once I've been playing around changing the smb settings on the server.

So 2 questions
1) Where else can I look to find miscreant samba settings? I'm using /etc/samba/smb.conf for the shares, and /var/lib/samba/usershares is empty. Where else can samba shares be defined?
2)Is there a bug with cifs mounts that could cause a hard lockup?

---

### Post by quibbler on 2008-10-18
To your first question, I also found /usr/share/samba/smb.conf.
Your second question, I'm afraid I have no idea.

Regards quibbler

---

### Post by Nepherte on 2008-10-18
The configuration of samba happens in /etc/samba/smb.conf.

---

### Post by amorangi on 2008-10-19
Well there is definitely a bug in cifs. If I make changes to the share on the host the clients randomly freeze. This has happened with my main PC, my laptop and a VM, all running 8.04. I'm mounting them in fstab with the following example:
```

//orac/Audio  /home/nitrous/Music cifs credentials=/home/nitrous/.smbcredentials,uid=1000  0  0

```

As I explained before, if I change the share name I get write access, but if I remove the share and recreate it I still don't, even moving it to another drive. The only place where shares are being defined is in /etc/samba/smb.conf as far as I can see, so I don't know where it's getting this 'memory' effect from.

So I've had to change the names of the shares that weren't working, and now I have write access, but now I've got another problem. When I copy a folder to a share the folder is created, but the files within aren't and I get the error "Permission denied". The permissions on the folder are fine though, and the second time I do the copy it works fine - merging to the previously denied folder without any complaints. This is rather a problem as I have a large number of folders to copy, and cancelling each one and redoing them is a pain.

I'm getting quite sick of Samba on 8.04. Unfortunately I have Windows machines on my network.

---

