---
title: "Newbie need help, blank screen after first reboot"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by 9192 on 2006-02-17
I rebooted after installation, but the screen was black with four tiny particle looks of Ubuntu log-in page.  It looks like Ubuntu autodetect put some uncompatible to my VGA card.  Samething on LiveCD boot.  

Is ther anyway I can install with monually set my VGA card to simple like VESA driver?

I can boot safemode that went to command line, but no idea how to use command line to fix this problem.

My system is laptop, Sharp MM20, efficeon 1 GHz, 512 RAM 20 GB hard drive and ATI redeon L6 with 16 Meg VRAM

Please help,

THank you,

9192

---

### Post by punkyetti on 2006-02-17
I've had a simular problem. After it installs and I boot up it goes thorugh everything and just before the login screen I get a message on my monitor that the resoultion doesn't work. But mine is with a desktop.

---

### Post by aysiu on 2006-02-17
Press control-alt-f1 when you're at the blank screen.
You should be able to log into a prompt something like ```
9192@ubuntu:~$
``` At that prompt, type ```
sudo dpkg-reconfigure xserver-xorg
``` use your user password as the password.

---

