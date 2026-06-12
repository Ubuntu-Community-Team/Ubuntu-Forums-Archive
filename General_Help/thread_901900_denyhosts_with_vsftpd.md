---
title: "denyhosts with vsftpd"
date: 2008-08-26
forum: General Help
---

### Post by tmetzcc325 on 2008-08-26
Hey all,

I am currently running sshd and vsftpd on my home PC so I can access it from work.  There is only one user that is allowed to login via ssh (my own user account as defined by the AllowUsers parameter), and I am only allowing two users to login via ftp (one for my account, and one for my father, so I can quickly share files with him [he's in Ohio, I'm in Virginia...I set up a local user account for him, but deny him access to log in remotely except to the ftp server]).

Anyways, I am using denyhosts to automatically block IPs that attempt to brute-force their way in via ssh, and it is working wonderfully.  The problem is that it is checking auth.log just fine, but does not check vsftpd.log for anyone that attempts to brute force thru ftp.

I have been searching online to try to figure out how to get denyhosts to also watch vsftpd.log, but I don't know a ton about python or building programs or daemons in linux, so I am in a bit of a quandry.  Does anyone know of an easy way to get denyhosts to watch the vsftpd.log file, or maybe give me a few pointers as to how I may be able to implement this myself?

Thanks in advance,
Tom

---

### Post by nickmax99 on 2010-01-20
Did you ever get a response for this? I'm looking for exactly the same thing. I run denyhosts on ssh enabled public facing servers and am staggered by the amount of brute force attacks it sees and stops. 

I'd also like something to do the same to stop brute force attacks on ftp.

---

### Post by tmetzcc325 on 2010-01-20
Sorry, I never heard anything.  I eventually shut down the FTP server just because I never used it, but my only advice would be to use VSFTP and use an authorized users list.  Create unique usernames and passwords, and pray.  I know it isn't the best advice, but not being a linux guru, I don't know any other way.

Good luck,
Tom

---

