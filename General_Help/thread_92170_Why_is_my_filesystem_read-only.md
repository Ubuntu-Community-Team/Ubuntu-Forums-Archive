---
title: "Why is my filesystem read-only?"
date: 2005-11-18
forum: General Help
---

### Post by HugiAsgeirsson on 2005-11-18
Hi

I just installed Ubuntu on a dual boot system. My computer had just crashed and I was facing having to reinstall Win XP, so I seized the opportunity and left 10 GB of space unpartitioned. I formated the rest of the drive into NTFS and installed Win XP. I then proceeded with installing Ubuntu, partitioning the remaining 10 GB into 500 mb of swap and 9.5 GB ext3 partition. I got Ubuntu set up just fine, and I could log in, however the ext3 filesystem was in read-only mode.

The strange thing was that I could create folders on the desktop, and when I was following instructions to get my MA111 WIFI card set up, I managed to unpack linux-wlan by typing sudo "sudo apt-get install linux-wlan-ng".
Alas, when I tried to edit /etc/network/interfaces, it wouldn't let me.

I don't have a lot of experience with linux, I'm just starting of.

Any ideas to how I can solve this?

---

### Post by Czar on 2005-11-18
[QUOTE=HugiAsgeirsson]The strange thing was that I could create folders on the desktop, and when I was following instructions to get my MA111 WIFI card set up, I managed to unpack linux-wlan by typing sudo "sudo apt-get install linux-wlan-ng".
Alas, when I tried to edit /etc/network/interfaces, it wouldn't let me.

I don't have a lot of experience with linux, I'm just starting of.

Any ideas to how I can solve this?[/QUOTE]

Dear HugiAsgeirsson,

Everything other then the items included in your ~ (Home) folder are owned by root (give and take a few).  The easiest way I believe to modify your root files is by the use of [SUDO](http://packages.ubuntu.com/breezy/admin/sudo) (Super User DO).  

Example;  

```
sudo vi /etc/network/interfaces
```

*Note; SUDO will always ask for YOUR password, not root's password*

---

### Post by iguanaphobic on 2005-11-18
Linux is a multi user system. All of the core OS files are only accessible by the root user. All of the files in your home folder (Desktop is a sub-folder of your home) are accessible by you.

sudo provides temporary root access to a regular user. Ubuntu makes the root password the same as the users password. When asked to edit system files using a text editor, open a terminal window and preface the command with sudo. 

eg. sudo gedit /etc/apt/source.list

would open the software sources list in gedit, a graphical text editor. 

Many other commands will also only work if prefaced with sudo. Your best bet is to check these forums for instructions.

---

### Post by HugiAsgeirsson on 2005-11-18
Ah, thank you for a simple answer to a pretty humiliating newbie question. It "solved" this problem, allthough I'm still having troubles with editing the /etc/network/interfaces file... I'll try a few things before asking again. Should new questions to seemingly unrelated problems be posted in a new thread?

---

