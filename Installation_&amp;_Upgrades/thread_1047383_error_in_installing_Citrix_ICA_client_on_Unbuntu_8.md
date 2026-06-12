---
title: "error in installing Citrix ICA client on Unbuntu 8.10 Server"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by rpedwards on 2009-01-22
I have trid multiple times to install the file en.linuxx86.tar.gz from the Citrix web site using the instructions on the Ubuntu site ([https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)). I have OpenMotif installed. I get the following:

michael@LinuxServer:~$ cd /home/michael/Desktop/icainstall2
michael@LinuxServer:~/Desktop/icainstall2$ ls
eula.txt  install.txt  linuxx86  PkgId  readme.txt  setupwfc
michael@LinuxServer:~/Desktop/icainstall2$ sudo ./setupwfc
[sudo] password for michael:
/home/michael/Desktop/icainstall2/./linuxx86/hinst: 236: /home/michael/Desktop/icainstall2/./linuxx86/echo_cmd: not found
/home/michael/Desktop/icainstall2/./linuxx86/hinst: 237: /home/michael/Desktop/icainstall2/./linuxx86/echo_cmd: not found
/home/michael/Desktop/icainstall2/./linuxx86/hinst: 238: /home/michael/Desktop/icainstall2/./linuxx86/echo_cmd: not found
/home/michael/Desktop/icainstall2/./linuxx86/hinst: 239: /home/michael/Desktop/icainstall2/./linuxx86/echo_cmd: not found
/home/michael/Desktop/icainstall2/./linuxx86/hinst: 4011: /home/michael/Desktop/icainstall2/./linuxx86/echo_cmd: not found
/home/michael/Desktop/icainstall2/./linuxx86/hinst: 4043: /home/michael/Desktop/icainstall2/./linuxx86/echo_cmd: not found
/home/michael/Desktop/icainstall2/./linuxx86/hinst: 4043: /home/michael/Desktop/icainstall2/./linuxx86/echo_cmd: not found
/home/michael/Desktop/icainstall2/./linuxx86/hinst: 4043: /home/michael/Desktop/icainstall2/./linuxx86/echo_cmd: not found
/home/michael/Desktop/icainstall2/./linuxx86/hinst: 4043: /home/michael/Desktop/icainstall2/./linuxx86/echo_cmd: not found
At this point, the terminal program stops.

---

### Post by TenDollarMan on 2009-03-14
If its the new one (ver 11), you need OpenMotif 2.3.1

---

