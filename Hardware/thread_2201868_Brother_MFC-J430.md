---
title: "Brother MFC-J430"
date: 2014-01-26
forum: Hardware
---

### Post by linux.girl on 2014-01-26
Hello,

I have a windows 7 VM (workstation 10) running on a ubuntu 13.10 host. I have a brother printer (MFC-J430), which always worked great on the win7 VM. Today I decided I wanted the printer to work on the linux host as well - and configured it to do so - it worked perfect. The problem is that when I re-attached the printer to windows vm, I can no longer print - when I try to print a word document there, it prints a blank page with half a line of black dots and that's it. I am sure that the fact that I made the printer work on linux is causing this problem, because the printer is working fine with other computers and it was also working fine on the win vm pre linux config.

Any suggestions or ideas of what could be wrong?

Thanks!!!

linux.girl

---

### Post by zteam2 on 2014-01-26
Have you tried to erase the printer query?

---

### Post by linux.girl on 2014-01-28
Hi zteam2,

The query was empty, so I didnt have to clean it, but I managed to solve it, this is how: I installed samba server on the Linux host and when I right clicked on the printer (on the Linux PC) it gave me two options: make this printer default for this computer only or make this printer default system wide. I chose to make it default system wide and as of magic, it started working on the windows VM too. So now it prints on both Linux host and Windows VM. 

Thanks a lot!

Linux.Girl

---

### Post by mörgæs on 2014-01-28
Good, please mark the thread 'solved'.

---

