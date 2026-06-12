---
title: "Ubuntu 9.10 wubi.exe installer fails on final part."
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by Cyra on 2009-11-12
[http://i36.tinypic.com/2f0ahvr.jpg](http://i36.tinypic.com/2f0ahvr.jpg)
Im trying to install Ubuntu 9.10 via the Wubi in windows installer.
It gets to the last little bit and gives me this error.
What is up why doesnt this work?

---

### Post by Mark Phelps on 2009-11-12
Which version of Windows are you trying to install in?  XP,Vista, or Seven?

---

### Post by Cyra on 2009-11-12
Windows 7 Enterprise

---

### Post by Cyra on 2009-11-12
No further feedback ?
Anybody else in windows 7 enviroment get this ?

> 11-12 15:28 DEBUG  Distro:   checking whether C:\Users\XXXX\AppData\Local\Temp\pyl673A.tmp is a valid Mythbuntu CD
11-12 15:28 DEBUG  Distro:     does not contain C:\Users\XXXX\AppData\Local\Temp\pyl673A.tmp\casper\filesystem.squashfs
11-12 15:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 15:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 15:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
11-12 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 15:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 15:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 15:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-12 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 15:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 15:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 15:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 15:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 15:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 15:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 15:28 INFO   Distro: Found a valid CD for Ubuntu: E:\
11-12 15:28 INFO   root: Running the installer...
11-12 15:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\XXXX\AppData\Local\Temp\pyl673A.tmp\translations, languages=['en_ZA', 'en']
11-12 15:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\XXXX\AppData\Local\Temp\pyl673A.tmp\translations, languages=['en_ZA', 'en']
11-12 15:28 INFO   WindowsFrontend: Operation cancelled
11-12 15:28 DEBUG  WindowsFrontend: frontend.quit
11-12 15:28 DEBUG  WindowsFrontend: frontend.on_quit
11-12 15:28 DEBUG  root: application.on_quit
11-12 15:28 INFO   root: sys.exit

The last part of the log.
The log is quite big , if you need more info than that please let me know.

---

### Post by Mark Phelps on 2009-11-12
Sorry to be discouraging, but nearly all the problematic posts I've seen here with Wubi and Windows involve the following:
1) Windows 7
2) Ubuntu 9.10
3) Wubi install

And, I have not seen one single case where anyone has posted a solution to this.

The Wubi guide itself does not indicate support for Windows 7, and while, in general, 7 is based on Vista (which Wubi does support), it uses an entirely new partitioning scheme.  That, coupled with the new GRUB2 in Ubuntu 9.10 appears to be presenting a show-stopper situation.

Sorry.

---

### Post by Cyra on 2009-11-13
Hmmm thats a bit dissapointing.
Any ideas as to what might be causing the fail at the end of the installation ?

---

### Post by Sciophobia on 2009-11-15
> **Cyra said:**
> Hmmm thats a bit dissapointing.
Any ideas as to what might be causing the fail at the end of the installation ?

When you installed Windows 7 did you do a clean install where it gave you a message about creating a reserved partition?  If you have the 100MB system reserved partition I believe that is what is making wubi fail.  I just reinstalled after having the same problem and partitioned before installing to avoid the 100MB partition.  It appears to be working fine now.

In summary, partition before installing 7 so it doesn't create extra partitions that mess up wubi.

---

