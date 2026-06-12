---
title: "Ubuntu maintenance and security questions"
date: 2008-09-25
forum: General Help
---

### Post by abeautifulbeat on 2008-09-25
With Windows I had tune-up utilites for keeping things neat and tidy.  Is there an equivalent program for Ubuntu?  Is it even needed?  
Also, does it need a firewall, anti-virus, anti-spyware, etc.?

---

### Post by lisati on 2008-09-25
Tune-up: Linux uses a different file system to, something like defrag is less likely to be needed.
Security: Have a look [here]("http://ubuntuforums.org/showthread.php?t=510812") Some people think you don't really need antivirus for Ubuntu: it's up to you; having it can be useful if you exchange files with Windows users.

---

### Post by aysiu on 2008-09-25
Yes, there are tune-up utilities to keep things neat and tidy.

1. Don't change any security defaults unless you know what you're doing (i.e., don't install OpenSSH server or FTP server software, etc. if you don't know how to secure them properly).

2. Use a strong password.

3. If you're installing stuff you think you may want to uninstall later, keep track of what you've installed. There are programs like GTKorphan, however, that will try to find no-longer-needed applications for you to remove.

4. Go to System > Administration > Services and uncheck any boxes you know you don't need (for example, I never use Bluetooth, so why do I need that service running?)

---

