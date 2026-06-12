---
title: "Installing fresh samba not working"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by bulletmike on 2008-12-18
Hi All,

The SWAT gui interface screwed up my whole smb.conf file so I wanted to re-install samba with the default smb.conf file. So I removed samba by running the command below:

sudo apt-get --purge remove samba

It said it successfully removed. However, it didn't remove the /etc/samba directory and its contents so I removed that as well.

I then tried re-install of Samba by running the command below:

sudo apt-get install samba

Although it installs, it fails to start the samba and from the log files it shows that it is because it cant locate the smb.conf in /etc/samba. My questions is:

1) Shouldn't the install create the /etc/samba director and its default config files ?
2) How do I go about to re-install a fresh copy of samba ?

I would appreciate any kind of feedback. 

Thanks !!!

---

### Post by ethernet on 2008-12-18
Have you tried purging samba and reinstalling from fresh as well? Might be worth a shot.

---

### Post by bulletmike on 2008-12-19
Thanks for the tip ethernet. I actually dug through different threads in this ubuntu forum and was able to resolve my problem. I should have done that in the first place than wasting another topic ](*,) 
Well the solution to my problem was inshort resolved by completely removing samba-common and installing it again.

---

