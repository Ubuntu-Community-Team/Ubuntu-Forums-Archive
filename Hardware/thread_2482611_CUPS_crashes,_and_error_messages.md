---
title: "CUPS crashes, and error messages"
date: 2023-01-05
forum: Hardware
---

### Post by goodstuff9 on 2023-01-05
Ubuntu 22.04 (wayland), CUPS 2.4.1, hplip is not installed (does that matter???).  


I keep getting error messages relating to CUPS and hpfax that I don't understand.  


In /var/log/cups/error_log, here is an example of the messages I'm getting:  




```
E [04/Jan/2023:07:40:23 -0600] [cups-deviced] PID 1741 (hpfax) stopped with status 1!
E [04/Jan/2023:07:40:34 -0600] [Client 6] Unable to encrypt connection: Error in the push function.
E [04/Jan/2023:07:40:44 -0600] [Client 9] Unable to encrypt connection: Error in the push function.
E [04/Jan/2023:07:40:54 -0600] [Client 12] Unable to encrypt connection: Error in the push function.
E [04/Jan/2023:07:41:05 -0600] [Client 13] Unable to encrypt connection: Error in the push function.

```



And here is what keeps showing up in /var/crash/_usr_lib_cups_backend_hpfax.0.crash:  




> PythonArgs: ['/usr/lib/cups/backend/hpfax']
Traceback:
 Traceback (most recent call last):
   File "/usr/lib/cups/backend/hpfax", line 83, in <module>
     from base.g import *
 ModuleNotFoundError: No module named 'base.g'
 
 During handling of the above exception, another exception occurred:
 
 Traceback (most recent call last):
   File "/usr/lib/cups/backend/hpfax", line 89, in <module>
     bug("Error importing HPLIP modules: %s\n" % (pid, e))
 TypeError: not all arguments converted during string formatting
UserGroups: N/A


I have two HP printers attached to this computer, as far as I can tell I am able to use them as I wish.  But I keep getting these error messages, and:  


1)  They're an annoyance; and far more importantly, 
2)  Something is clearly wrong, I'd like to have a properly working system.  


Looking for help:  


A)  What are these messages telling me?
B)  What is the problem?  
C)  How do I fix the problem?  


Thanks in advance.

---

