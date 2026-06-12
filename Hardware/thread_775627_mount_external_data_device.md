---
title: "mount external data device"
date: 2008-04-30
forum: Hardware
---

### Post by Dailydog on 2008-04-30
I have a problem with external storage devices (camera, stick, external HD).

The first one I mount is always rejected: I see it listed but when I try to access it I get the message: 'device is not mounted'. When I add a second device there are no problems at all.

I work on a Dell XPS. 

I had the problem with Gutsy and thought it might be gone after installing Hardy, but no such luck.

Any suggestions on how to solve this?

---

### Post by EKa on 2008-04-30
Hi,

I managed to mount and link an external directory on my Netcenter using:

		
> sudo mkdir /mnt/mydir
sudo mount -t smbfs -o username=myname //WD-NETCENTER/Mydir /mnt/mydir 
sudo ln -T /mnt/mydir -s Mydirlnk

---

