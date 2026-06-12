---
title: "How mount a samba share?"
date: 2005-11-09
forum: General Help
---

### Post by RCB on 2005-11-09
Hi Guys 

I'm fairly new to Linux, i have just installed Ubunto 5.10. So far its great, easier to install than Gentoo. 

Anyway I was trying to mount a file share from a Samba server. I can get to it from my gentoo build by typing 

#mount -t smbfs -o username=*  //server.*.* /mnt/share

and it says wrong fs type in my ubuntu terminal??

and if I try in the GUI it keeps asking for the domain & password. 

Please advise

---

### Post by Remmelas on 2005-11-09
```
sudo mount //server/sharename /mnt/share
``` gets it for me if there is no username and password needed, no -t option

---

### Post by jrbeaton on 2005-11-09
I had this same problem.  I fixed it by just installing the smbfs package.


Then, I just changed the mount command from this:
```

mount -t smbfs -o username=* //server.*.* /mnt/share

```

to this:
```

smbmount -o username=* //server.*.* /mnt/share

```

Hope this helps,
JRB

---

### Post by RCB on 2005-11-09
Thanks for replying even though I had a typo in the Title. :D 

JRB how did you install smbfs?


I have looked in the Synaptic Package Manager

and have already smbclient and samba-common 

and I installed samba just incase and did a reboot?

---

### Post by LinuxWiz83 on 2005-11-10
[QUOTE=jrbeaton]I had this same problem.  I fixed it by just installing the smbfs package.


Then, I just changed the mount command from this:
```

mount -t smbfs -o username=* //server.*.* /mnt/share

```

to this:
```

smbmount -o username=* //server.*.* /mnt/share

```

Hope this helps,
JRB[/QUOTE]

How can you add this to Startup without being prompt for the root password every reboot?

---

### Post by jrbeaton on 2005-11-14
In Synaptic, there is a package called "smbfs".  I just installed that.

You don't actually need "samba" if you're just going to act as a client (you're not going to share files on your machine).


JRB

[QUOTE=RCB]Thanks for replying even though I had a typo in the Title. :D 

JRB how did you install smbfs?


I have looked in the Synaptic Package Manager

and have already smbclient and samba-common 

and I installed samba just incase and did a reboot?[/QUOTE]

---

### Post by jrbeaton on 2005-11-14
To get the system to do it automatically, you need to add entries to /etc/fstab.  You'll need to add a line that looks something like...

```

//server/sharedir	/mnt/share	smbfs	username=*,password=* 0 0

```



[QUOTE=LinuxWiz83]How can you add this to Startup without being prompt for the root password every reboot?[/QUOTE]

---

### Post by Scanner on 2005-11-14
Make sur ethat the share is always available though, if not it slows the boot process to a crawl.

---

### Post by soulestream on 2005-11-14
you can also setup your share in fstab with

//server/share /media/share smbfs credentials=/etc/samba/cred,rw,noauto,fmask=0777,dmask=0777  0  0

thats all one line btw

noauto doesnt mount at startup, until you mount it with "mount /media/share" I use this on my laptop because its often not in my network. I just put an icon on the taskbar to mount/unmount it as needed.

the credentials file just hides your username and password in a non-user readable file

soule

---

### Post by LinuxWiz83 on 2005-11-15
Thank you for the info i'll try that.

---

### Post by Hypatia2 on 2005-11-17
Howdy,
I found this thread useful, but wanted to do something slightly different. I'm documenting it here because it might help someone else.
I wanted to be able to mount a hidden share as a normal user when needed by supplying a password at mount time. To do this, I had to add to my fstab:
> //*10.1.2.3*/*shareName$* /mnt/*winUser* smbfs rw,user,noauto,username=*winDomain*\*winUser*   0   0

I then had to make the smbmnt  command SUID:
> sudo chmod +s /usr/bin/smbmnt
And finally, make the mount point owned by the user:
> sudo chown * linUser * /mnt/*winUser*

Now, when I log in as *linUser*, I use the command:> mount /mnt/*winUser* and enter my windows password to access the windows share.

---

