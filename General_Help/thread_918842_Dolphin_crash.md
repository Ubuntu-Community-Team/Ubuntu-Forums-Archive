---
title: "Dolphin crash"
date: 2008-09-13
forum: General Help
---

### Post by mark0495 on 2008-09-13
Hello everybody,

I just installed kde 4.1.1, and dolphin crashes every time now when I try to start it up. For I don't like to use Konqueror as a file manager, I would like to find a solution. When I saw this bug for the first time, I thought that it would be the best to check it out in terminal. This is the outcome:

> mark@ubuntu-desktop:~$ dolphin
ASSERT: "(*it).isValid()" in file /build/buildd/kde4libs-4.1.1+really4.1.1/kio/kio/previewjob.cpp, line 565
<unknown program name>(5874)/: Communication problem with  "dolphin" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "

mark@ubuntu-desktop:~$ KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = dolphin path = <unknown> pid = 5875
sock_file=/home/mark/.kde4/socket-ubuntu-desktop/kdeinit4__0


I'm using Kubuntu Hardy Heron KDE4 Remix

Thanks already,
Mark0495

---

