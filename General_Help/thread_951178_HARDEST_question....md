---
title: "HARDEST question..."
date: 2008-10-17
forum: General Help
---

### Post by Shiv4m on 2008-10-17
Yes this is rocket science for me :(

How do I make myself the owner?
Example: creating folder in the opt file.

Thank You

---

### Post by MaxIBoy on 2008-10-17
It's possible to do this, but DANGEROUS. You're talking about running with root access. When running with root, there are NO warnings, you can easily delete all your files or otherwise screw yourself over. People running with root access usually render their computer unbootable within days or loose valuable data, and then come running back to the forums for help. Because of this, anyone who teaches how to run in the graphical interface with root access is BANNED and the thread is DELETED. 


As an administrator (in Ubuntu, there's always at least one administrator,) you have a safer version of the same thing. Run a program from the console, add "sudo" to the beginning of the command (or "gksudo" if the program you're running is graphical,) and that one single program will be given root access. Only use commands which you fully understand with root access. If you don't know what a command does, don't risk it. There are some seriously cruel pranksters out there who give evil "advice."

---

### Post by jerome1232 on 2008-10-17
Are you installing some software there?

Generally you would make a dir like this, then to make it owned by you

```
sudo mkdir /opt/dirname
sudo chown $USER:$USER /opt/dirname
```

preferably I'd leave it owned by root normally programs will have correct permissions setup out of the archive. Sometimes I'll give my user read/write permissions through the group permissions. I can elaborate on that if you want.

---

