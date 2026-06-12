---
title: "Zyxel NAS326 and Ubuntu 20.04"
date: 2022-04-09
forum: Hardware
---

### Post by kanaske-maybe on 2022-04-09
As of 3 days ago none of my 6 machines all running Ubuntu 20.04 Desktop can any longer access the NAS. It seems like it may have been a change on the SMB support on Ubuntu. I know the NAS is fine as the AFP protocol which it also supports works fine. The NAS does support SMB 2 and above. When SMB access was available a few days ago I had noticed it was seen as CIFS shares.

---

### Post by TheFu on 2022-04-09
Unix-like OSes should use NFS for network file access whenever possible.  NFS provides native Unix permissions that are the same on the client as on the server.

MS-Windows clients should use CIFS.

I saw that Samba defaults changed in an announcement in the last 2 weeks, but doubt those changes have been incorporated into any Linux distro at this point.  They disabled SMB1 support.

What troubleshooting has been done already between the client and the NAS?  Is the network fine? Is avahi or DNS working?  Have you tried to use smbclient in verbose mode?  Any errors in that command or in the system logs?  Can any other devices access the NAS using CIFS?

---

### Post by kanaske-maybe on 2022-04-10
Did you even read the question? I want nothing to do with NFS and never asked about it. Nor did I ask anything about Windows nor do I want to hear about Windows I do not use it. I said the NAS supports other then SMB 1. I said the NAS is fine the AFP is working. You have said nothing but crap that has nothing to do with the question. I also said all 6 of my machines have the same issue. Thanks for wasting my time.

---

### Post by TheFu on 2022-04-10
If you feel that my post was malicious, please report it.
Nobody here is trying to 'waste your time'. We provide ideas that you may not have considered and steps to try. 
If the post isn't what you seek, please ignore it.
Good day.

---

### Post by him610 on 2022-04-10
#1
> As of 3 days ago none of my 6 machines all running Ubuntu 20.04 Desktop can any longer access the NAS. It seems like it may have been a change on the SMB support on Ubuntu. I know the NAS is fine as the AFP protocol which it also supports works fine. The NAS does support SMB 2 and above. When SMB access was available a few days ago I had noticed it was seen as CIFS shares.
#3
> Did you even read the question?
There does not appear to be any questions in original post, only statements;)

---

### Post by kanaske-maybe on 2022-04-11
Problem has been solved. All the mount commands had to redone as the syntax of the mount command has changed since some recent update to the SMB.

---

### Post by TheFu on 2022-04-11
Thanks for being extra helpful and posting the solution so others can learn and quickly solve their issue too.  

Also, thanks for marking this thread as SOLVED, so other people seeking answers can find it quickly - use the thread tools button.  This also will keep people seeking to help from wasting their time on already solved threads.

---

### Post by #&amp;thj^% on 2022-04-11
> **TheFu said:**
> This also will keep people seeking to help from wasting their time on already solved threads.

I can't say that wasn't deserved. :) Tense thread user beware.:lolflag:

---

