---
title: "Connecting to Samba, using fstab - won't connect on boot"
date: 2008-07-13
forum: General Help
---

### Post by eagle63 on 2008-07-13
So following the instructions found in what seems like a million threads here (and other sites) I've added a line to my fstab to mount a Samba share from another Ubuntu machine.  I've tried using both smbfs and cifs, and both work flawlessly if I run "sudo mount-a" from a command line.  However, if I reboot, both will fail during startup.  (error just shows, "waiting for /var/mediaShare" which is my mount point - and eventually times out)

My only theory at this point is that maybe the networking "stuff" isn't loaded yet when the fstab executes during startup?  But if that's the case, then why is everyone recommending using fstab for connecting to samba??  

I can post my fstab if needed, but I thought I'd keep things general to start with.  Thanks!

---

