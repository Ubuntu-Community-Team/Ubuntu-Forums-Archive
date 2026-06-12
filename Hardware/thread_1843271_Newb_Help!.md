---
title: "Newb Help!"
date: 2011-09-13
forum: Hardware
---

### Post by xp_version1 on 2011-09-13
Hi there, 

Brand new Ubuntu user here in need of some help. I've installed Ubuntu 11.04 onto my netbook to use it as a very basic server between the three laptops in my house (2 Windows 7, 1 OSX Lion)

My intention is just to use to share a drive (a 3tb external Seagate drive) and as a print server. I've also read something about running torrents through the server, which would be quite useful too. Streaming to PS3 and Xbox would be a perk too.

Problem is that I can't seem to access the shared drive across my network. Ubuntu mounts it fine and I can use it normally and all three laptops can 'see' the drive, they just can't access it.

I've tried sharing a folder on the netbooks actual hard drive and this works fine across all three systems. It just won't let me do anything with the external HD.



In addition, is Ubuntu the best solution for what I want anyway or am I going about this all wrong? 
Also, once this is all setup, is there anything else cool I can do that I may not have considered?

Thanks muchly for any help.

---

### Post by mastablasta on 2011-09-13
> **xp_version1 said:**
>  
Problem is that I can't seem to access the shared drive across my network. Ubuntu mounts it fine and I can use it normally and all three laptops can 'see' the drive, they just can't access it.

The drive should be mounted in linux. if it is mounted then you need to give the users that log to it access. that is one of key linux security components - access to files and drivers is restricted to user/admin rather than available to anyone.
 
edit also make sure all necessary samba components are installed. i remember certain versions of this OS are done in a crappy way - i.e. someone forgot to include crucial files needed for sharing (example is Kubuntu 10.10).

---

### Post by xp_version1 on 2011-09-13
Thanks for the reply.

Touch wood, it seems to have been fixed by following this: [http://ubuntuforums.org/showthread.php?t=1797058](http://ubuntuforums.org/showthread.php?t=1797058)

But we shall see once I get home.

---

