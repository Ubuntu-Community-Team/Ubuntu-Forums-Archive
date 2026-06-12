---
title: "[SOLVED] suddenly can't connect to MySQL server with third-party GUIs on local machin"
date: 2008-09-26
forum: General Help
---

### Post by Prince_Andrei on 2008-09-26
I use Aqua Data Studio to run queries on my local MySQL server, and it's been working like a champ for almost a year. Suddenly it can't connect. It looks like a java connection timeout error. The MySQL Query Analyzer and Administrator tools connect and work just fine. I tried downloading the trial version of Navicat, and it gets an error when it tries to connect as well.

I'm totally confused. Clearly the db server is working, and the connection info is correct, since the MySQL official apps work just fine. Could this be Java-related? I don't even know where to try to troubleshoot. I've never had a problem until now.

Thanks!

---

### Post by Prince_Andrei on 2008-09-26
I fixed the issue. I, for whatever reason, changed the alias used to refer to my machine in the System>Administration>Network. Adding "localhost" back as an alias fixed it.

---

