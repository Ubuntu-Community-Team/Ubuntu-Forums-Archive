---
title: "Problem connecting to web server through ssh"
date: 2008-11-08
forum: General Help
---

### Post by My_web on 2008-11-08
Hi Everyone,

I've just updated to 8.10 & so far think it's great :)

I've got a problem I've been looking into for the past few days (it's not related to 8.10 I also had it with 8.04). When I try to connect to my web server through the command line with:

```
ssh root@XXX.XXX.XX.XX
```

It gives me a time out after a while, however if I reboot into Vista I can connect fine with WinSCP. I think the problem may be that the default port isn't right but I can't figure out how to set the port to login to...

Anyone know the correct command to do this? I've tried this after looking through the --help (tried with -p before root@ as well):
```
ssh root@XXX.XXX.XX.XX -p XXXX
```

But got the same result :( could there be something on the server blocking my Ubuntu install & not my Vista one? I don't see how as they're both using the same IP to connect to the web...

Please help & sorry if this is something really stupid!

PS. I can connect to another of my servers fine. So it seems this is just between the one server & my Ubuntu install :(

---

