---
title: "How do i mount user directories individually in samba on WinXP"
date: 2008-08-12
forum: General Help
---

### Post by Avinash.Rao on 2008-08-12
Hi all,

I am using Samba on Ubuntu 8.0 as a PDC and the domain logon seems to be working fine. I am still trying to make the netlogon scripts working though! 


1) I have about 20 users and i have configured roaming profiles, so that users can use any computer in the lab and can access their profile. The profiles are working but i am not able to automate the process of mapping their home directories in samba. For example, if a user "ravi" logs into the domain, the login script should automatically map "ravi's" home directory. The share path is /export/username's. How can i do this in samba? I am able to do this manually from WinXP machine.

2) Access to local drives on winxp is restricted except "my documents" folder. How can i control this in samba? OR how can i map "my documents" folder to their respective home directories in /export/username ?

thanks a ton

---

### Post by Avinash.Rao on 2008-08-12
Hello all,

I have somewhat figured this out. The [homes] share is a special share which will mount the users home directory as a network drive on the windows box. This will work only if the home directory is in the default location which is /home !

But, if i share a different directory say for example /export, the entry for this in smb.conf file would be:

[share]
path = /export/U%
comment = Student Home Directory
read only = No
writable = yes

What this does is, if a user by name "ravi" logs in to the domain, it will make /export/ravi available in the network places in the winxp box but not as a separate network drive. How do i make this available to the as a separate network drive and how do i map the My documents directory in windows to this drive?

To map the my documents directory on windows to the samba share, i can change the location of the directory, but i cannot do this on every windows machine. Is there anyway i can do this through samba?

Thanks

---

