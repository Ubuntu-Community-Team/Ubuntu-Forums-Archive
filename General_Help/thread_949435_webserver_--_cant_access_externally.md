---
title: "webserver -- cant access externally"
date: 2008-10-16
forum: General Help
---

### Post by kroenecker on 2008-10-16
I set up nginx to server up web content on port 8080.

Setup:

Poked a hole in ufw at 8080.

My router appears to be forwarding to 8080 ... When I use [http://www.canyouseeme.org/](http://www.canyouseeme.org/) pointed at 8080 the nginx access log shows that it has been accessed.

However, when I enter http://<myip>:8080 into a web browser I get a "can't establish a connection error".  On the other hand [http://localhost:8080](http://localhost:8080) serves up content at I would expect.

So what am I doing wrong?

---

### Post by kroenecker on 2008-10-16
Alright I don't quite understand...

When I stop nginx, doing a port scan indicates that nothing is responding.  When I start nginx, a port scan indicates that the proper port is responding.

Nonetheless actually pointing my browser at that ip gives me a "can't establish a connection to the server" error.

Any help would be greatly appreciated!

---

