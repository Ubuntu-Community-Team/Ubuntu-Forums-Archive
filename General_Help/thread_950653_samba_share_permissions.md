---
title: "samba share permissions"
date: 2008-10-17
forum: General Help
---

### Post by eppo on 2008-10-17
i have my ubuntu server setup to join my windows active directory domain. all of the computers on my network join this domain. i have a raid array mounted to my /home/raid folder. that folder is shared using samba. as my main user, i want full access to anything within that /home/raid folder while using my windows networked computers.  how would i go about setting the directory permissions? within that raid folder i'm going to set up 2 folders, 1 for each user to use as their my documents folder. so i want this folder to only be available to the user it belongs to.
how would i set this up? what user and group should own these directories? does samba use the unix permissions, or use its own?
thanks
Joe

---

### Post by cmnorton on 2008-10-17
Windows domain logins still throw me. 

As I understand it, each windows user needs to map to a Linux user. Many windows users can map to one Linux user. I have it set up as a one-to-one mapping.

I have the problem where my Windows users have Windows login names of first_initial-last-name, but their Linux login may be something else. That is where smbusers comes in.

The linux user is mapped to the windows user in /etc/samba/smbusers, and that linux user gets its password set using smbpasswd. When mapping in Windows, the linux name is used, not the windows name, and yet the smbusers mapping provides the samba server with the Windows domain credentials needed. 

So your samba permissions should be what you need for the local user, and then let that user map to their area. You certainly can allow multiple users to map to a common area as well.

---

