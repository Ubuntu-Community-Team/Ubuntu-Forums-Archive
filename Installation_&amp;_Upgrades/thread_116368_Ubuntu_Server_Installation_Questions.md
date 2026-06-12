---
title: "Ubuntu Server Installation Questions"
date: 2006-01-12
forum: Installation &amp; Upgrades
---

### Post by jacobrich on 2006-01-12
I am getting ready to install Ubuntu server on a spare PC. I am very new to Linux, but really want to learn about it. I am a Windows Network Administrator and am familiar with most networking/server issues as they exist in the Windows world.

I would like to know how the following items compare to the Windows world:

[LIST]
[*]Does Ubuntu have any sort of built-in software firewall (like the basic Windows firewall).
[*]Is the ability to Telnet into a server included automatically with a basic server install?
[*]Is the ability to make TAR or ZIP files included with a basic server install?
[*]Is it possible to make a TAR file and then transmit it via Telnet (for back-up purposes?)
[/LIST]

Right now I am running eyeOS ([www.eyeos.org](www.eyeos.org)) on my Windows XP Pro box with IIS and PHP 5.x installed. I would like to set up an Ubuntu server on my LAN. I would like for this Ubuntu server to only include the most basic parts of Linux, though. I don't need SSH, FTP, X, etc... Just command line stuff. Can it be done? I am asking if I can do the TAR items via Telnet because I would prefer to just Telnet into the box and copy the files over to another machine for backup purposes. I figured I'd just install Apache, SSL, PHP and some sort of firewall.

---

### Post by Koybe on 2006-01-13
> **jacobrich][*]Does Ubuntu have any sort of built-in software firewall (like the basic Windows firewall).[/QUOTE]iptables (Netfilter) is the comand line for any linux distribution's firewall. Nothing more is needed, it's in the kernel.

[QUOTE=jacobrich][*]Is the ability to Telnet into a server included automatically with a basic server install?[/QUOTE]SSH send telnet back to his old age. Forget about telnet, use SSH  said:**
> [*]Is the ability to make TAR or ZIP files included with a basic server install? Of course.

[QUOTE=jacobrich][*]Is it possible to make a TAR file and then transmit it via Telnet (for back-up purposes?)[/QUOTE]Use scp which comes with ssh. :)

---

### Post by jacobrich on 2006-01-13
Is there a way to remove Telnet? Or is it in the kernel? I would like to run one, or the other (Telnet or SSH). Can I install SSH and remove Telnet?

Also, does the basic server install include any sort of CD writing capabilities?

---

### Post by Koybe on 2006-01-13
I don't know why you worry about that. I never tought about this.

I don't know about cd wrinting, i guess not. Why would it be on a standard server install? Anyway, if you need one just apt-get it ;)

---

### Post by jacobrich on 2006-01-13
Koybe, thanks for all your help. I am new to Linux and I know I might ask questions that seem very basic. I really want to learn everything I can about it.

---

### Post by jacobrich on 2006-01-13
[QUOTE=Koybe]I don't know why you worry about that. I never tought about this.

I don't know about cd wrinting, i guess not. Why would it be on a standard server install? Anyway, if you need one just apt-get it ;)[/QUOTE]

Is Telnet disabled by default? I have a fresh install of Ubuntu server on my system, but I can't find it using telnet from my other machines on the network. Is there a config file that tells the system what daemons to run at start-up?

---

### Post by Koybe on 2006-01-14
There is no telnet server on your ubuntu server, anyway if you install a servie such as smtp you'll be able to telnet the 25 port. (someone will correct me if i'm wrong on this).

All the startup script can be found in */etc/init.d/*
Then you have all the directories named */etc/rcX.d/* containing links to the scripts above.

When you start your server level 1 and 2 will be executed as it's telle on */etc/inittab* (initdefault). You can manage all this using the *update-rc.d* command.

You can also check what process are running with *ps* and/or *top* command.

---

### Post by jacobrich on 2006-01-14
Thank Koybe, you talked me into it, no telnet, only SSH.

---

