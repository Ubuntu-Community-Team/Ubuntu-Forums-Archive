---
title: "Please help with Sopcast installation"
date: 2008-10-10
forum: General Help
---

### Post by kokkus on 2008-10-10
Hi.
I have a problem with the installation of Sopcast.
I followed this guide: [http://www.linux.ryukent.co.uk/show.php?id=36](http://www.linux.ryukent.co.uk/show.php?id=36)

Everything went fine untill I came to the RKMOD version of QSopCast archive.
I extracted it, cd opended it with terminal under the src directory as they tell me to do in the guide.
When I try to gmake, it says the gmake file doesn't exsist.

Do I forget something here? I think I may have made a mistake.
Please help, Thanks in advance:)

---

### Post by Ryadt on 2008-10-10
Sorry but was that not qmake instead of gmake?

---

### Post by kokkus on 2008-10-10
Yes I ment qmake, sorry.
But no, it won't work.

---

### Post by Ryadt on 2008-10-10
Have you got build-essential installed?
```
sudo apt-get install build-essential
```

---

### Post by kokkus on 2008-10-10
Yes I have

---

### Post by Ryadt on 2008-10-10
The error is caused by the file not being in the directory where you are running the command. Make sure that you are in the correct src directory before running the command.

---

### Post by kokkus on 2008-10-10
I know, but that's the strange thing here. I am sure I am in the right directory.
I extracted it to my desktop, so I ren the command cd /home/chris/desktop/qsopcast-0.3.5/src , it says it is in the right directory but when I then write sudo qmake, it says qmake doesn't exsist.

---

### Post by kokkus on 2008-10-10
Could someone create a .deb file for me so I can automaticly install it please?

---

### Post by kokkus on 2008-10-10
I found the problem.
Terminal won't recognize any commands such as sudo and cd.
Wow i need help now. Please:)

---

### Post by dabogsta on 2008-10-19
sudo apt-get install qt3-dev-tools
that will give you qmake.
.deb file [here]("http://ubuntuforums.org/showthread.php?t=258049")

---

