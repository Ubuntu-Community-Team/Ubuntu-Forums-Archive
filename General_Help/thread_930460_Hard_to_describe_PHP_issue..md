---
title: "Hard to describe PHP issue."
date: 2008-09-26
forum: General Help
---

### Post by fatgeek on 2008-09-26
I'm trying to setup and run [RUTV]("http://linux.softpedia.com/get/Office/News-Diary/RUTV-40155.shtml") and I'm having some issues. It requires PHP be installed. It also requires CURL, PDO, XMLRPC, DOM. I was able to add PHP and I think I installed the modules correctly.

When I try and run the script, or any other PHP for that matter, I get the following error:
```
PHP Fatal error:  PDO: driver sqlite2 requires PDO API version 20060511; this is PDO version 20060409 in Unknown on line 0
PHP Fatal error:  Unable to start SQLite module in Unknown on line 0
```

The version I have installed seems to be up to date and the requested version is from 2006. Something here is simply not making sense to me. Any help would be appreciated.

---

### Post by cariboo on 2008-09-26
Have you got php5-cli installed? You are going to need it if you intend to run php scripts fron the command line.

Jim

---

### Post by fatgeek on 2008-09-26
I do have php5-cli installed

---

