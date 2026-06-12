---
title: "[SOLVED] Problems Mounting NAS Drive"
date: 2008-09-02
forum: General Help
---

### Post by Bang Crash on 2008-09-02
I'm trying to permanently mount a share on my NAS so that it automatically connects at boot up, I have put the following line in fstab:

```
//192.168.1.4/music	/mnt/music	cifs	credentials=/root/.smbcredentials,rw   0   0
```

The share is mounting at boot but I think there is a permissions problem because I cant see anything in it when logged in as my user account.  If I run a mount -a command I get the following message:

```
mount: wrong fs type, bad option, bad superblock on //192.168.1.4/music,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

If I run dmesg | tail I get the following:
```

[128239.471348]  CIFS VFS: No username specified
[128239.471359]  CIFS VFS: cifs_mount failed w/return code = -22
```

But there is definitely a username and password listed in my credentials file as follows:

```
username=*******
password=*******
```


Can anyone tell me where I'm going wrong?

---

### Post by b20963a2 on 2008-09-02
It might be useful to specify which brand & model of NAS you're actually using. The Western Digital Netcenter doesn't play nice with linux for instance.

---

### Post by fballem on 2008-09-02
I'm going back in memory, but could you please check to see if you have smbfs installed (System > Application > Synaptic Package Manager, then do a search for 'smbfs'). If you don't have it installed, then please install it and reboot.

The reason for the suggestion is that I remember reading the CIFS depends on smbfs, but it is not installed by default.

Hope this helps

---

### Post by Bang Crash on 2008-09-02
Installing smbfs seems to have done the trick, thanks.

Just for the record it's a Linksys NSLU2 NAS, which to date has not presented any problems mounting to my server which is running hardy.

---

