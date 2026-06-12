---
title: "[SOLVED] problem running fetchyahoo"
date: 2008-07-18
forum: General Help
---

### Post by benayi32 on 2008-07-18
I've recently the latest version of fetchyahoo (2.12.0 alpha 13)

However on running the program I run into an error with the program being unable to "open output"

Running fetchyahoo from the command line gives me the following output

```

<my_username>:~$ fetchyahoo 
Please enter your Yahoo! password: Logging in securely via SSL as <my_username>@btinternet.com on Fri Jul 18 21:08:47 2008
Country code : uk       FetchYahoo! Version: 2.12.0alpha13
Successfully logged in as <my_username>@btinternet.com.
Marking messages read on the server

Marking messages read on the server

Fetching mail from folder: Inbox
Getting Message ID(s) for message(s) 1 - 25.
Getting Message ID(s) for message(s) 26 - 50.
Getting Message ID(s) for message(s) 51 - 75.
Getting Message ID(s) for message(s) 76 - 83.
Got 83 Message IDs
Failed: Couldn't open output: >>/var/spool/email/<my_username> at /usr/bin/fetchyahoo line 1727, <STDIN> line 1.
```

I've also tried using previous versions of the program but get the same error. 

Also I'm using the yahoo mail classic interface and the necessary perl libraries have been installed.

Any idea's what the problem could be?

Thanks in advance.

---

### Post by bapoumba on 2008-07-18
Thread moved to "General Help".

---

