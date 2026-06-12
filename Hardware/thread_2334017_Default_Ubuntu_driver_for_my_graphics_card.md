---
title: "Default Ubuntu driver for my graphics card?"
date: 2016-08-15
forum: Hardware
---

### Post by xenon3 on 2016-08-15
It is said that the default UBUNTU driver is better than the original driver of the producing company of the graphics card.

I have came across after a couple of hours searching: about 10 conflicting procedures for installing the original driver, from the producing company one the procedure consisted of about hundred steps involving 50 separate entry / run terminal commands, that ain't workable

Anyways GIMP (move selection) constantly freezes whole system

In other occasions sometimes system freezes too in FireFox

Graphic Card: NVIDIA GF116 EGeForce GTX 550 Ti (rev ai)

Original Driver: NVIDIA-Linux-x86-367.35.run ? Is that correct? I got x86 UBUNTU on x64 machine

I'm also plagued by viruses, I'm not sure whether someone is controlling my system from a distance, making my system freeze at his or her will, I can't rule that out

Because the default driver always worked fine, also in GIMP, problems are from lately

Should the default driver be good enough? For FireFox and GIMP?

---

### Post by ajgreeny on 2016-08-15
I can't help with your nvidia driver never having used an nvidia card but as it is not a very new card I think the driver suggested by the **Additional Drivers** utility would probably be the most successful for your system rather than the 367 version you have.

> I'm also plagued by viruses, I'm not sure whether someone is controlling my system from a distance, I can't rule that out
What makes you think that?

There are no known viruses for Linux in the wild though there are trojans and other malware items that can affect Linux and Ubuntu.
What symptoms are you seeing that make you suspect a virus problem?

---

### Post by xenon3 on 2016-08-15
> **ajgreeny said:**
> I can't help with your nvidia driver never having used an nvidia card but as it is not a very new card I think the driver suggested by the **Additional Drivers** utility would probably be the most successful for your system rather than the 367 version you have.


What makes you think that?

There are no known viruses for Linux in the wild though there are trojans and other malware items that can affect Linux and Ubuntu.
What symptoms are you seeing that make you suspect a virus problem?

When I only have Facebook, Gmail and Google open in FireFox tabs, leave computer on for a night, I get according to ClamTK viruses like:

PUA.HTML.Exploit.CVE_2015_1692-1
PUA.HTML.Trojan.Agent-37075
other HTML exploits too
and lots of PUA.Win.Trojan.Xored-1 (a diaspora in the mozilla subdirectories)

One night 16 similar, also LibreOffice macro viruses, OK I know PUA for windows, but I don't believe they are all harmless for LINUX.

Why would these websites bombard a client computer with PUA's during 12 hours? They are not there right after opening Facebook, Google and Gmail or after fresh connection.

OK if I recall correctly all were in the mozilla cache subdirectories besides the macro virus that was in the libreoffice subdirectory (small change that it was a CLAMTK false positive)

Either I have a stealth connection or these so called harmless PUA's come through the ports and not through websites (like computer worms)

---

### Post by mastablasta on 2016-08-16
> **xenon3 said:**
> When I only have Facebook, Gmail and Google open in FireFox tabs, leave computer on for a night,  this is not a good idea.

you probably have false positives. you can check the netework (and other) logs to see if anything is happening on your system. also clamtk scans mostly for widnows viruses and is known to give false positives. 
you can also try it with a live session and see if you get a similar result.

the recomended method to install the drivers in ubuntu is to use additional drivers application or to use a PPA (if you need a newer version). 

furthermore by default all ports are closed for incomming connections. if you feel paranoid or if you want to easilly manage ports then install gufw: [https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by CatKiller on 2016-08-16
You aren't plagued by viruses. Clear your Firefox cache and all those problematic files will disappear.

Don't install the driver from the NVidia website. Use the proprietary driver listed in the Additional Drivers tab, if it's listed, or stick with the open source nouveau driver, which is perfectly fine for most purposes, especially on a card of that vintage.

---

### Post by xenon3 on 2016-08-16
> **CatKiller said:**
> You aren't plagued by viruses. Clear your Firefox cache and all those problematic files will disappear.

Don't install the driver from the NVidia website. Use the proprietary driver listed in the Additional Drivers tab, if it's listed, or stick with the open source nouveau driver, which is perfectly fine for most purposes, especially on a card of that vintage.

Oh thanks, how convenient "Additional Drivers" utility, I did not know I had it 

I have in additional drivers: NVIDIA version 367.35 nvidia-367 (open source) listed among 20 or so for my geforce grapic card, this is the same version I got from the NVIDIA website search program

Is it dangerous to use this one?

 I mean I read on the Internet that someone installed the wrong graphic driver and after reboot login screen was blank, he tweaked all day from console to fix it, I would not know how to tweak if this happened to me

---

### Post by CatKiller on 2016-08-16
Installing the NVidia driver from the website is (deliberately, I think) a complete pain in the ****. Using the Additional Drivers will just install a package, the same as any other package. It's just not included by default because it's non-free.

If it all goes pear-shaped, just log in in text mode (or boot into single user mode if you prefer) and remove the package in the usual way and then reboot. But it's remarkably unlikely to go pear-shaped, since your card isn't really really new (which is where the problems usually lie).

If you get stuck, don't spend all day tweaking from the console, or use 50 random commands that you don't understand that you pulled from the Internet, just post back here while we still have some hope of helping you fix it ;-) 

So that you can practice, if you press Ctrl-Alt-F1, you'll switch to TTY 1, which will let you log in without troubling the graphics system. F7 will take you back to the graphical session. "The usual way" would be a command that starts * sudo apt-get remove * and then you'd type *nvidia* and let Tab-completion fill in the rest for you. You can reboot from the command line with *sudo shutdown -r now*.

Single user mode is accessed from the GRUB menu, and will automatically log you in as root. Be very careful if you're ever logged in as root.

Edit: wow, the forum censors ****. I wonder if it censors bum?

Edit 2: it doesn't. Good. "A complete pain in the bum."

---

### Post by xenon3 on 2016-08-16
> **CatKiller said:**
> Using the Additional Drivers will just install a package, the same as any other package.

Additional Drivers: NVIDIA version 367.35 nvidia-367 (open source) IS OK THEN?

My best option?

This would be the most easy to do!

---

### Post by CatKiller on 2016-08-16
I don't see any reason why that one wouldn't be perfectly fine.

---

### Post by xenon3 on 2016-08-16
> **CatKiller said:**
> Single user mode is accessed from the GRUB menu, and will automatically  log you in as root. Be very careful if you're ever logged in as root

Funny thing I don't know my root password UBUNTU installation wizard does not ask you to set one. (OK you say automatically logged in as root)

I got my main user account (which is an admin account) but that password does not work for ROOT, a while ago the terminal asked for the root password to issue some commands.

Is there a default root password like "Welcome" which one must change? :o from TTY 1? If root has a default I consider that as highly insecure, when someone has broken into your system.

---

### Post by CatKiller on 2016-08-16
By default root has no password, which makes it impossible to log in as root. You can only sudo or boot into single user mode to gain root permissions.

---

### Post by mastablasta on 2016-08-17
> **xenon3 said:**
> Additional Drivers: NVIDIA version 367.35 nvidia-367 (open source) IS OK THEN?


opensource is opensource driver. it should say recomended on some line. of course the listed drivers are all that work with your card. 

you can easilly remove the driver from console and get back to default. there is no need to spend a day in it. 

[SIZE=2]https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia
[/SIZE]

> **xenon3 said:**
> 
I got my main user account (which is an admin account) but that password does not work for ROOT,.

this account can be eleveted to root using sudo command. there is no root account password, as mentioned. you can use admin account to do things that root user would do. be sure to read this to understand what an admin account can do and when you need to use it: [SIZE=2]https://help.ubuntu.com/community/RootSudo
[/SIZE]
--------------------------------------------------------

> **CatKiller said:**
> 

Edit: wow, the forum censors ****. I wonder if it censors bum?

Edit 2: it doesn't. Good. "A complete pain in the bum."

please don't do it.

> **Profanity:** We have users of all age groups and of all tolerance levels where profanity is concerned. A language filter is in place to catch most major forms of profanity that may accidentally be used. Do not attempt to circumvent the language filter by using variations or slight misspellings of profanities.

---

### Post by xenon3 on 2016-08-24
> **CatKiller said:**
> By default root has no password, which makes it impossible to log in as root. You can only sudo or boot into single user mode to gain root permissions.

If I recall correctly, I think during my attempt to install the producer's (NVIDIA) driver packages, I was specifically asked for the root password in TTY 1 for one command string, don't know anymore which one, I tried so many, can be TTY said you got to be logged in as root and meant single user mode

---

### Post by xenon3 on 2016-08-24
> **CatKiller said:**
> I don't see any reason why that one wouldn't be perfectly fine.

Thanks Cat****** (don't kill those poor cats please)

Additional Drivers is a charm, works like a charm, thanks again, I can move selections and edit selections in GIMP, system does not freeze anymore

---

