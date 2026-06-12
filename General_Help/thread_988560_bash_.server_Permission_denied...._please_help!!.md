---
title: "bash: ./server: Permission denied.... please help!!"
date: 2008-11-20
forum: General Help
---

### Post by mcweaver on 2008-11-20
Hi

I'm trying to do some coursework which involves having two terminals open, one acting as a server and one as a client and messages get passed between them.  However (having just installed build-essential and got my programs to compile) when I type ./server into one terminal so that it can act as a server, I get the message bash: ./server: Permission denied. I really need to get this working so I can finish this work! 

Please help, thank you

---

### Post by Linteg on 2008-11-20
Try making the file executable (if it isn't already)
```
chmod +x server
```

---

### Post by dexter on 2008-11-20
You have to change the file permissions and make it executable:
```
chmod u+x server
```

If you run "ls -al", all files are listed, including permission. A file is executable only when the executable flag (x) is set.

---

