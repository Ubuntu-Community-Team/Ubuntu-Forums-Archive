---
title: "Configuration's gone forever."
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by ramandhingra on 2009-04-02
Hi

I installed Asterisk on my Ubuntu Server using 'apt-get install' and then removed it using 'apt-get remove', the config files under /etc/asterisk wasnt removed, so I removed them manually. Now, when I try to reinstall Asterisk using apt-get again, it doesn't bring back the config files, :(, what to do..

I think this is not something Asterisk specific, but just a general install/remove issue. Help, thanks.

---

### Post by ajgreeny on 2009-04-02
> Now, when I try to reinstall Asterisk using apt-get again, it doesn't bring back the config files, :sad:, what to do..
Do you mean that the application will not install or that it simply does not automatically make the /etc/asterisk configuration folder/files?  Don't forget they may not be there until you start asterisk for the first time, and then close it down, rather like firefox or thunderbird which only make the .mozilla and .mozilla-thunderbird folders after starting up the programs.

---

### Post by ramandhingra on 2009-04-05
Ajgreeny, it gets installed and creates the folder /etc/asterisk too but the folder is empty with no configuration files in there.

---

### Post by ramandhingra on 2009-04-09
Hi.. anyone, whats the solution to this? :(
Thanks.

---

