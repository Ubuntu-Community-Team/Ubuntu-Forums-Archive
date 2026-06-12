---
title: "lamp-server not being recognized"
date: 2008-11-10
forum: General Help
---

### Post by nbakewell on 2008-11-10
Hello all,

I am having some troubles getting lamp-server to work.  I installed it with the following command: *sudo tasksel install lamp-server* and it seemed to install fine - took a while, but I was prompted for a MySQL root password so I thought it was installing fine.  The installation completed and went back to my terminal screen with no error output, but now I can't find it.  I type *lamp-server* into the terminal and it says "bash: unknown command" and I do not see it anywhere under my Applications menu.  Did it not install then or am I just missing it?

Thanks for any help!

---

### Post by torgrot on 2008-11-10
LAMP stands for Linux Apache MySQL and Perl/Python  there isn't really a LAMP server.  You can try browsing to http:\\127.0.0.1\  and the Apache server should show you something.  

torgrot

---

### Post by Iowan on 2008-11-10
```
mysql
``` This command will start MySQL for you. You may need to install a browser. **w3m** is installed by default - I added **elinks**.

---

### Post by -Zeus- on 2008-11-10
> **torgrot said:**
> LAMP stands for Linux Apache MySQL and Perl/Python  there isn't really a LAMP server.  You can try browsing to http:\\127.0.0.1\  and the Apache server should show you something.  

torgrot

actually, the P stands for PHP ;)

---

