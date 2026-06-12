---
title: "can you get security"
date: 2008-07-31
forum: General Help
---

### Post by dxlwebs on 2008-07-31
hey im a windows person mainly and im about to make a change to linux to creat a server and what not from the desktop very of ubuntu and i was wondering if there is any forms of security like anti virus and anti hacking soft and if its also free or not!

sorry about for another stupid question

thanks alot for helping me

---

### Post by Rocket2DMn on 2008-07-31
Hello,
No virus scanning software is necessary since viruses are not a problem in linux.  Only a few have ever been made, but there are none "in the wild" right now.  If a new virus were to be released, a patch would come out so fast that the virus would not have time to spread.  Quick fixes are an advantage of free and open source software (FOSS).  On the topic of FOSS, it's free as in beer!
No anti-hacking tools are necessary, though there are ways to beef up security.  Here is a great thread about Ubuntu security - [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by dxlwebs on 2008-07-31
thank you very much i'll start reading up now

---

### Post by hyper_ch on 2008-07-31
You generally don't need anti-virus and
you generally don't need to alter your firewall also.

There might be reasons when you want to have anti-viruse (for examples if you serve files to windows computers - although I think it should be their task to secure their windows computers).

Altering the firewall settings (by default it's set to let everything pass) is only necessary if you want to install servers/services and want to limit them. If you are behind a router and have UPnP deactivated I don't even see a reason then the alter firewall settings on ubuntu.

---

### Post by spiderbatdad on 2008-07-31
Webservers present a different type of security risk than what the average users faces, obviously because you have opened a port in your firewall and configured your computer to receive requests from the internet.

There is a great deal of information out there regarding various types of webservers. It can be overwhelming. Once you decide what type of server application you want to run, look into what security is needed. Apache for example is often secured by running it from a chroot or by debootstrapping. Apache security is often done at the time of compilation...especially necessary for a chroot.  Anyway, it's great fun to host a server, and a great learning experience.

---

