---
title: "HP LaserJet 1018 not working"
date: 2010-11-22
forum: Hardware
---

### Post by sm_ashiq on 2010-11-22
OS: Ubuntu 10.10 Maverick Meerkat 
Printer: HP LaserJet 1018

My printer is not working in Maverick Meerkat, i tried to install hplip-3.10.9.run but getting this error 

warning: There are 7 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: This installer cannot install 'gcc' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.

Please help me to solve the problem.

---

### Post by Fafler on 2010-11-22
Installing drivers that way is asking for trouble. The run file contains source code and needs to be compiled on your system. Instead use the hplip that comes with Ubuntu. Open a terminal and type
```
sudo apt-get install hplip
```
Or even better, just use Printing wizard from the administration menu. It should install drivers as needed.

---

### Post by sm_ashiq on 2010-11-22
but still printer HP LaseJet 1018 is not working in both system with Ubuntu 10.10, please help me solve.

---

### Post by Fafler on 2010-11-22
Open a terminal and type

```
tail -f /var/log/messages
```

Now, connect the printer and post any output from the terminal. Is the printer USB or parallel?

Did you use the wizard to install the printer?

---

### Post by sm_ashiq on 2010-11-22
> **Fafler said:**
> Open a terminal and type

```
tail -f /var/log/messages
```Now, connect the printer and post any output from the terminal. Is the printer USB or parallel?

Did you use the wizard to install the printer?

Not printing any thing, My printer is USB, i used wizard to install the printer.

---

