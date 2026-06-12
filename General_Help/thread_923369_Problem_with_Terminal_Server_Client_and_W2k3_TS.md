---
title: "Problem with Terminal Server Client and W2k3 TS"
date: 2008-09-18
forum: General Help
---

### Post by sbantz on 2008-09-18
I have a Windows 2003 server set in application server mode serving 20 WYSE thin client machines connecting over RDP.  One of the WYSE terminals quit working, so I took an old Hp PC and loaded Ubuntu on it.  I tried using Terminal Server Client to connect to the terminal server, but the terminal server stated that the user has to have Administrator rights to log in to the Windows 2003 server.  If I make the user an admin, they can log in, but I do not want them to be an admin of the server.  If I go to any other WYSE thin client or even Terminal Server Client on a Windows XP machine, they can log in as a regular user just fine.

What is different about Ubuntu Terminal Server client that makes it behave differently?  Like I said, on a regular thin client and even a Windows XP remote desktop session, the user can log in to the terminal server just fine as a regular user.  If I try from Ubuntu, the server complains that they have to be an admin.

Thanks for any advice.

---

### Post by ju2wheels on 2008-09-18
Out of curiousity, did you assign your non admin user the proper group in the permissions for being able to log on remotely (Remote somthing group and not just User). Although I would think that if you hadnt you wouldnt be able to log in from XP, but still worth asking...

---

### Post by sbantz on 2008-09-18
Yep, the terminal server is set up correctly and is giving the proper session permissions.  This user can log in and operate fine from a Windows XP RDP to Windows 2k3 terminal server session.  An Ubuntu to Windows 2k3 terminal server session tells them they must be an administrator to log in.  I just don;t see how it would treat two RDP sessions differently for the same user.

---

