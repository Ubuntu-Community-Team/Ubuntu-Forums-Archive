---
title: "Remote Subclipse Repository"
date: 2008-10-19
forum: General Help
---

### Post by gvanto on 2008-10-19
I am using Subclipse within Eclipse (Ganymede) and find it to be a great tool.

I would like to set up a remote repository for my little java project so that a friend and I can both work on the same project. 

I have an online server for which I know the ftp details for (however do not have SSH access, but can get it) and would like to set the repository up so that it is located on this online server. (Its hosted with lypha, originally for hosting php site).

I would like check-in and check-out capability.

If anyone has advice on how to go about getting this set up, it would be greatly appreciated!

Many thanks,
Gerry
Subclipse newbie

---

### Post by Sam on 2008-10-19
You can install Apache + dav_svn module.

[https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)

---

### Post by gvanto on 2008-10-19
Hi Sam,

Thanks for your reply.

I'm about 95% sure the host is already running an apache server on their end. Presumably I'd need to install svn on the server then?

Many thanks again,
Gerry

---

### Post by Sam on 2008-10-19
You must install the package libapache2-svn, then enable the "dav_svn" module in Apache. There are plenty of tutorials about apache+svn. Ask if you need more help.

---

