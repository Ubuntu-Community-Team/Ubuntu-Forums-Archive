---
title: "Proftpd and Logging"
date: 2008-09-26
forum: General Help
---

### Post by decoy415 on 2008-09-26
So I've setup proftpd on my linux box at home so that I can transfer files. I think I've setup the conf file correctly. But when I go to check my log files, no data comes up. Even after I do all kinds of things like transfers, login, or failed login. Since I'm the only user I'm not too worried about intrusion, but I would still like to be able to analyze these logs for comfort (and fun). I've attached my conf file. Any help is very much appreciated.

Greg

---

### Post by Sycron on 2008-09-26
To login use your greq password.

---

### Post by decoy415 on 2008-09-26
..... I know. I can do that.

I'm having trouble with the **LOGS** not login.

---

### Post by Sycron on 2008-09-26
Is this helpful ? [http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Logging.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Logging.html)

---

### Post by decoy415 on 2008-09-26
It was a bit. I read through it a couple times. But I still can't get the log files to write anything. I used this site and some others to edit my conf file. That is why you see lines that write the log files to a /home/ftp directory instead of the normal /var/log. I thought it might be a permissions issue.

---

### Post by Sycron on 2008-09-26
try ```
sudo chmod 777 /name/and/path/to/log
```

---

### Post by decoy415 on 2008-09-26
I did a:

```
sudo chmod 777 /home/ftp/test
```

Then went ahead and did my 3 tests. Nothin.

---

### Post by Sycron on 2008-09-26
Try to put the log file back to /var/log and see if it works.

---

### Post by decoy415 on 2008-09-26
Still nothing.

---

### Post by Sycron on 2008-09-27
We'll just follow this thread, when I'll have the time I'll test the logging. I'm using too proftpd.

---

### Post by reality1011 on 2008-09-27
I would suggest using the default settings to get logging back and then tweek things from there.

---

